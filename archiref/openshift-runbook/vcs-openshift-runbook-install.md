---

copyright:

  years:  2019, 2020

lastupdated: "2020-04-03"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Red Hat OpenShift 4.2 user provider infrastructure installation
{: #openshift-runbook-runbook-install-intro}

Red Hat OpenShift 4 introduced the following concepts:

* Installer Provisioned Infrastructure (IPI) - For use on supported platforms, only AWS currently. The installer provisions the underlying infrastructure for the cluster and it configures the cluster.
* User Provisioned Infrastructure (UPI)  -  For use on bare metal, vSphere, and other clouds that do not support IPI. The user is required to provision the infrastructure; compute, network, storage that the OpenShift cluster is hosted on. The installer configures only the cluster.

These instructions use the OpenShift installer in the UPI mode. Terraform is used to provision the seven VMs for the bootstrap, control-plane, and compute nodes. The following process is completed:

1. A `yaml` file is created that is ingested by the OpenShift installer.
2. The installer is run and creates a number of files, including the Ignition files. The Ignition files are used to configure the bootstrap, control-plane, and compute nodes at first boot.
3. The Ignition file for the bootstrap node is copied to the NGINX default directory on the bastion node, so that the bootstrap node can fetch it on first boot.
4. The Ignition Terraform file is updated with the DNS server.
5. The `terraform.tfvars` file is created to hold the variables for the Terrafrom installation.
6. Terraform is run, which provisions the VMs. The VMs are started, configured, and the OpenShift cluster is created.

For more information about installing the OpenShift user provider infrastructure, see [Internet and Telemetry access for OpenShift Container Platform](https://docs.openshift.com/container-platform/4.2/installing/installing_vsphere/installing-vsphere.html#cluster-entitlements_installing-vsphere){:external}.

## Creating the OpenShift Installer yaml file
{: #openshift-runbook-runbook-install-yaml}

Use the following table to document the parameters you will need for your deployment, examples are shown that match the deployment described in this document.

* The SSH key can be copied after being displayed by using the command: `cat /root/.ssh/id_rsa.pub`.
* The pull secret collected from Red Hat. For more information, see [OpenShift Infrastructure Providers](https://cloud.redhat.com/openshift/install/vsphere/user-provisioned){:external}.

| Parameters | Example | Your Deployment |
| --- | --- | --- |
| Base Domain | dallas.ibm.local | |
| metadata name | ocp | |
| vCenter Server IP address | 10.208.17.2 | |
| UserName | administrator@vsphere.local | |
| Password | s3cretPassw0rd | |
| vCenter Server instance datacenter | datacenter1 | |
| vCenter Server instance datastore | vsanDatastore | |
| Pull Secret | | |
| Public SSH Key| | |
{: caption="Table 1. install-config.yaml file parameters" caption-side="top"}

Using the following install-config.yaml file shown in the figure, update it using your deployment details from the previous table:

1. Update the base domain name.
2. Update the metadata name with the OpenShift cluster name.
3. Provide the following vCenter information:
   * vCenter IP address.
   * vCenter username and password.
   * Datacenter name.
   * DataStore name.
4. Paste the Pull Secret.
5. Paste the SSH key.
6. The following figure shows the install-config.yaml file. Copy the file to the clipboard.

```bash
apiVersion: v1
baseDomain: acmeskb.net
compute:
- hyperthreading: Enabled
  name: worker
  replicas: 0
controlPlane:
  hyperthreading: Enabled
  name: master
  replicas: 3
metadata:
  name: ocp
platform:
  vsphere:
    vcenter: 10.208.17.2
    username: administrator@vsphere.local
    password: 's3cretPassw0rd'
    datacenter: datacenter1
    defaultDatastore: vsanDatastore
pullSecret: 'COPY PULL SECRET HERE'
sshKey: 'COPY PUBLIC SSH KEY HERE'
```
{: caption="Figure 1. install-config.yaml file contents" caption-side="bottom"}

In the SSH session to the bastion node with root privileges, use the following commands to create the install-config.yaml file:

```bash
cd /opt/ocp42install
vi install-config.yaml
```

Type `i` to enter insert mode, paste the file contents. Press Esc, then type `:wq` to save the file and exit the vi editor.

The OpenShift Installer will delete this file so to keep a copy use the following command:

```bash
cp install-config.yaml install-config.bak
```

## Running the OpenShift Ignition command
{: #openshift-runbook-runbook-install-ignition-cmd}

Now that the install-config.yaml is created and populated run the OpenShift Installer to create the ignition files

```bash
cd /opt/ocp42install/
openshift-install create ignition-configs --dir=/opt/ocp42install/
```
  The Ignition files are valid for 24 hours and your OpenShift deployment must be completed within this time. Otherwise, you must regenerate the Ignition files. For more information, see [Troubleshooting OpenShift problems](/docs/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-trbl-intro).
   {:note}

The following files are produced by the OpenShift Installer:

```bash
.
├── auth
│   ├── kubeadmin-password
│   └── kubeconfig
├── bootstrap.ign
├── master.ign
├── metadata.json
└── worker.ign
```

## Copying the bootstrap Ignition file to the web server
{: #openshift-runbook-runbook-install-ignition-nginx}

The bootstrap.ign file needs to be copied to the document root of NGINX. The bootstrap ignition file must be hosted on the web server so the bootstrap node can reach it on first boot. The Ignition file is too large to fit in a vApp property.

Copy the *bootstrap.ign* file to the document root of NGINX.

```bash
cp bootstrap.ign /usr/share/nginx/html
```

## Terraform files
{: #openshift-runbook-runbook-install-terraform}

There are three Terraform files that need updating:

* ignition.tf - This file needs to be updated so that the DNS entry matches the deployment.
* terraform.tfvars - This file needs to be created and holds the variables that are used by the main.tf file
* main.tf - This file needs to be updated to remove the DNS section.

### ignition.tf - Updating the DNS entry in the template
{: #openshift-runbook-runbook-install-terraform-ignition}

The DNS IP details are hardcoded within the Terraform template. You must change this IP to be the vCenter Server instance AD DNS server.

| Parameters | Example | Your Deployment |
| --- | --- | --- |
| DNS1 | 10.187.214.66 | |
{: caption="Table 2. ignition.tf file parameters" caption-side="top"}

1. In the SSH session to the bastion node, with root privileges, use the following command to open the file:
   `vi /opt/ocp42install/installer/upi/vsphere/machine/ignition.tf`
2. Type `i` to enter insert mode, and then scroll down to the DNS1 entry.
3. Update the IP address from 8.8.8.8 to match the deployment.
4. Press Esc, then type `:wq` to save the file and exit the vi editor.

The file should be similar to the following example:

```JSON
locals {
  mask = "${element(split("/", var.machine_cidr), 1)}"
  gw   = "${cidrhost(var.machine_cidr,1)}"

  ignition_encoded = "data:text/plain;charset=utf-8;base64,${base64encode(var.ignition)}"
}

data "ignition_file" "hostname" {
  count = "${var.instance_count}"

  filesystem = "root"
  path       = "/etc/hostname"
  mode       = "420"

  content {
    content = "${var.name}-${count.index}"
  }
}

data "ignition_file" "static_ip" {
  count = "${var.instance_count}"

  filesystem = "root"
  path       = "/etc/sysconfig/network-scripts/ifcfg-ens192"
  mode       = "420"

  content {
    content = <<EOF
TYPE=Ethernet
BOOTPROTO=none
NAME=ens192
DEVICE=ens192
ONBOOT=yes
IPADDR=${local.ip_addresses[count.index]}
PREFIX=${local.mask}
GATEWAY=${local.gw}
DOMAIN=${var.cluster_domain}
DNS1=10.187.214.66
EOF
  }
}

data "ignition_systemd_unit" "restart" {
  count = "${var.instance_count}"

  name = "restart.service"

  content = <<EOF
[Unit]
ConditionFirstBoot=yes
[Service]
Type=idle
ExecStart=/sbin/reboot
[Install]
WantedBy=multi-user.target
EOF
}

data "ignition_config" "ign" {
  count = "${var.instance_count}"

  append {
    source = "${var.ignition_url != "" ? var.ignition_url : local.ignition_encoded}"
  }

  systemd = [
    "${data.ignition_systemd_unit.restart.*.id[count.index]}",
  ]

  files = [
    "${data.ignition_file.hostname.*.id[count.index]}",
    "${data.ignition_file.static_ip.*.id[count.index]}",
  ]
}
```

### terraform.tfvars - Editing Terraform input variables
{: #openshift-runbook-runbook-install-terraform-tfars}

In Terraform, the `main.tf` file takes the input variables from `terraform.tfvars`. For variables that are not described in that file, it takes the default value from the `variable.tf` file.

Use the following table to document the parameters needed for your deployment, examples are shown that match the deployment described in this document.

The ignition files can be copied after using the following commands to display the files:

`cat /opt/ocp42install/master.ign`

`cat /opt/ocp42install/worker.ign`

| Parameter | Example | Your Deployment |
| --- | --- | --- |
| bootstrap_ip | 192.168.133.9| |
| control_plane_ips | 192.168.133.10<br>192.168.133.11<br>192.168.133.12| |
| compute_ips | 192.168.133.13<br>192.168.133.14<br>192.168.133.15| |
| machine_cidr | 192.168.133.0/24| |
| cluster_id | ocp| |
| cluster_domain | ocp.dallas.ibm.local| |
| base_domain | dallas.ibm.local| |
| vsphere_server| 10.208.17.2| |
| vsphere_user | administrator@vsphere.local|
| vsphere_password | s3cretPassw0rd | |
| vsphere_cluster | cluster1 | |  
| vsphere_datacenter | datacenter1 | |
| vsphere_datastore | vsanDatastore| |
| vm_template | rhcos-latest | |
| vm_network | vxw-dvs-22-virtualwire-24-sid-6011-OpenShift-LS | |
| bootstrap_ignition_url | `http://192.168.133.08/bootstrap.ign` | |
| control_plane_ignition | |
| compute_ignition | |

{: caption="Table 2. ignition.tf file parameters" caption-side="bottom"}

Using the following terraform-tvars example file shown in the figure, update the file using your deployment details from the previous table. Copy the file to the clipboard.

```bash
bootstrap_ip = "192.168.133.9"
control_plane_ips = ["192.168.133.10","192.168.133.11","192.168.133.12"]
compute_ips = ["192.168.133.13","192.168.133.14","192.168.133.15"]
machine_cidr = "192.168.133.0/24"
cluster_id = "ocp"
cluster_domain = "ocp.dallas.ibm.local"
base_domain = "dallas.ibm.local"
vsphere_server = "10.208.17.2"
vsphere_user = "administrator@vsphere.local"
vsphere_password = "s3cretPassw0rd"
vsphere_cluster = "cluster1"
vsphere_datacenter = "datacenter1"
vsphere_datastore = "vsanDatastore"
vm_template = "rhcos-latest"
vm_network = "vxw-dvs-22-virtualwire-24-sid-6011-OpenShift-LS"

bootstrap_ignition_url = "http://192.168.133.51/bootstrap.ign"

control_plane_ignition = <<END_OF_MASTER_IGNITION
COPY IN CONTENTS OF MASTER.IGN HERE
END_OF_MASTER_IGNITION

compute_ignition = <<END_OF_WORKER_IGNITION
COPY IN CONTENTS OF WORKER.IGN HERE
END_OF_WORKER_IGNITION
```
{: caption="Figure 2. terraform.tfvars example file" caption-side="bottom"}

The terraform.tfvars file is created as follows:
1. In the SSH session to the bastion node, with root privileges, use the following command to open the file; `vi /opt/ocp42install/installer/upi/vsphere/terraform.tfvars`.
2. Type `i` to enter insert mode, paste the file contents.
3. Press Esc, then type `:wq` to save the file and exit the vi editor.

### main.tf - Remove the DNS section
{: #openshift-runbook-runbook-install-terraform-main}

Remove the dns module section as the file expects to use AWS route 53 for DNS. The main.tf file is updated as follows:
1. In the SSH session to the bastion node, with root privileges, use the following command to open the file; `vi /opt/ocp42install/installer/upi/vsphere/main.tf`.
2. Type `i` to enter insert mode.
3. Scroll down the file until you reach the DNS module section.
4. Delete the entire section shown in "File 3: Section to be removed".
5. Press Esc, then type `:wq` to save the file and exit the vi editor.

```bash
module "dns" {
  source = "./route53"

  base_domain         = "${var.base_domain}"
  cluster_domain      = "${var.cluster_domain}"
  bootstrap_count     = "${var.bootstrap_complete ? 0 : 1}"
  bootstrap_ips       = ["${module.bootstrap.ip_addresses}"]
  control_plane_count = "${var.control_plane_count}"
  control_plane_ips   = ["${module.control_plane.ip_addresses}"]
  compute_count       = "${var.compute_count}"
  compute_ips         = ["${module.compute.ip_addresses}"]
}
```
{: caption="Figure 3. DNS module section to be removed" caption-side="bottom"}

## Run Terraform
{: #openshift-runbook-runbook-install-terraform-run}

Terraform is used to deploy the VMs for bootstrap, control-plane, and compute nodes. Terraform operates as follows:

* terraform init - initializes the terraform plug-ins and modules.
* terraform plan - performs a dry run on the templates, ensuring it can connect to the vCenter.
* terraform apply - runs the templates. The auto-approve switch can be added so that confirmation of each deployment is not required.

After Terraform provisions the VMs, the OpenShift cluster bootstraps itself:

1. The bootstrap node boots and starts hosting the remote resources that are required for the compute-nodes to boot.
2. The compute-nodes fetch the remote resources from the bootstrap node and finish booting.
3. The compute-nodes use the bootstrap node to form an etcd cluster.
4. The bootstrap node starts a temporary Kubernetes control plane by using the new etcd cluster.
5. The temporary control plane schedules the production control plane to the compute-nodes.
6. The temporary control plane shuts down and passes control to the production control plane.
7. The bootstrap node injects OpenShift Container Platform components into the production control plane.
8. The control plane sets up the compute nodes.
9. The control plane installs more services in the form of a set of Operators.
10. The result of this bootstrapping process is a fully running OpenShift cluster. The cluster then downloads and configures remaining components that are needed for the day-to-day operation.

In the SSH session to the bastion node, with root privileges, run the following commands, ensuring that each one completes with no errors before entering the next command.

```bash
cd /opt/ocp42install/installer/upi/vsphere/
terraform init
terraform plan
terraform apply -auto-approve
```

## Post deployment
{: #openshift-runbook-runbook-install-postdeployment}

1. After the virtual machines have bootstrapped, run the following command to monitor the installation:

    ```bash
    cd /opt/ocp42install
    openshift-install --dir=. wait-for bootstrap-complete --log-level debug
    ```

2. Wait until you see the following information:

    ```bash
    INFO It is now safe to remove the bootstrap resources
    ```

3. The Cluster Image Registry does not select a storage backend in UPI mode. Therefore, the cluster operator will continually wait for an administrator to configure a storage backend. A workaround is to point the image-registry to an empty directory to allow the installation to complete by running the following commands:

    ```bash
    mkdir /root/.kube/
    cp /opt/ocp42install/auth/kubeconfig ~/.kube/config
    oc patch configs.imageregistry.operator.openshift.io cluster --type merge --patch '{"spec":{"storage":{"emptyDir":{}}}}'
    ```

    After the installation is complete, change the image-registry to a suitable location.

4. Run the following command to monitor the installation:

    ```bash
    openshift-install --dir=. wait-for install-complete
    ```

5. Wait until you see the following message. The system provides the URL and credentials to log in to the OpenShift Console after the installation is complete. Your URL and password will be different:

    ```bash
    INFO Install complete!
    INFO To access the cluster as the system:admin user when using 'oc', run 'export KUBECONFIG=/root/go/src/github.com/openshift/installer/bin/auth/kubeconfig'
    INFO Access the OpenShift web-console here: https://console-openshift-console.opc.dallas.ibm.local
    INFO Login to the console with user: kubeadmin, password: my-kube-password
    ```

The password for the user that was created during installation can also be found in the auth subdirectory in the install-dir. It lets you log in through oc login and also gives you access to the web console. The URL for the console is `https://console-openshift-console.<cluster>.<base_domain>`.

1. Run the following command from the */opt/ocp42install* directory:

    ```bash
    watch -n5 oc get clusteroperators
    ```

2. Monitor for cluster completion. An output is provided in the following example:

    ```bash
    Every 5.0s: oc get clusteroperators

    NAME                                 VERSION   AVAILABLE   PROGRESSING   DEGRADED   SINCE
    authentication                       4.2.0    True        False         False      20m
    cloud-credential                     4.2.0    True        False         False      38m
    cluster-autoscaler                   4.2.0    True        False         False      38m
    console                              4.2.0    True        False         False      27m
    dns                                  4.2.0    True        False         False      35m
    image-registry                       4.2.0    True        False         False      14m
    ingress                              4.2.0    True        False         False      30m
    kube-apiserver                       4.2.0    True        False         False      33m
    kube-controller-manager              4.2.0    True        False         False      33m
    kube-scheduler                       4.2.0    True        False         False      32m
    machine-api                          4.2.0    True        False         False      38m
    machine-config                       4.2.0    True        False         False      33m
    marketplace                          4.2.0    True        False         False      30m
    monitoring                           4.2.0    True        False         False      28m
    network                              4.2.0    True        False         False      37m
    node-tuning                          4.2.0    True        False         False      32m
    openshift-apiserver                  4.2.0    True        False         False      31m
    openshift-controller-manager         4.2.0    True        False         False      33m
    openshift-samples                    4.2.0    True        False         False      24m
    operator-lifecycle-manager           4.2.0    True        False         False      35m
    operator-lifecycle-manager-catalog   4.2.0    True        False         False      35m
    service-ca                           4.2.0    True        False         False      38m
    service-catalog-apiserver            4.2.0    True        False         False      32m
    service-catalog-controller-manager   4.2.0    True        False         False      32m
    storage                              4.2.0    True        False         False      30m
    ```


**Next topic:** [Red Hat OpenShift 4.2 additional configuration](/docs/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-config-intro)

## Related links
{: #vcs-openshift-runbook-install-related}

* [VMware Solutions on {{site.data.keyword.cloud}} and Red Hat OpenShift overview](/docs/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-config-intro)
