---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

# {{site.data.keyword.cloudaccesstrailshort}} events

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.Bluemix_notm}}.

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.Bluemix_notm}}. For more information, see the [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla).

## {{site.data.keyword.cloudaccesstrailshort}} events table

Check the following table for the description of the columns in the Activity Tracker events table.

Table 1. Description of the Activity Tracker events table

| Column                | Value type | Description |
|:----------------------|:-----------|:------------|
| Time                  | N/A        | The date and time when the event is created. |
| initiator.name        | String     | The IBMid of the user that initiates the action. |
| target_name           | String     | The resource on which the action is run. |
| target.typeURI        | String     | The Universally Unique Identifier (UUID) of the target on which the action is run. |
| action                | String     | The action that triggers the event. The valid values are `create`, `update`, and `delete`. |
| outcome               | String     | The result of the action. The value is `success`, `failure`, or `pending`. |
| reason_reasonCode     | Integer    | The reason code of the outcome. |
| initiator_host_address| String     | The IP address where the request comes from. |

For more information, see [Activity Tracker event fields](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event).

## Tracking instance management events

When you manage user accounts, instances, clusters, and services in {{site.data.keyword.vmwaresolutions_short}}, an event is generated and sent to the **account domain** in Activity Tracker.

Check the following table for the actions that generate and send management events to Activity Tracker.

Table 2. Description of actions that generate management events

| Action                                   | Description | Outcome |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.user_account.update`    | <ul><li>The request to update the user account is received.</li><li>The request to update the user account is responded.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>The request to update notifications is received.</li><li>The request to update notifications is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>The request to wipe secure data is received.</li><li>The request to wipe secure data is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>The request to migrate to bss account is received.</li><li>The request to migrate to bss account is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcf.order`                 | <ul><li>The request to order a Cloud Foundation instance is received.</li><li>The request to order a Cloud Foundation instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcf.delete`                | <ul><li>The request to delete a Cloud Foundation instance is received.</li><li>The request to delete a Cloud Foundation instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcf.add_hosts`             | <ul><li>The request to add ESXi servers to a Cloud Foundation instance is received.</li><li>The request to add ESXi servers to a Cloud Foundation instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcf.remove_hosts`          | <ul><li>The request to delete ESXi servers from a Cloud Foundation instance is received.</li><li>The request to delete ESXi servers from a Cloud Foundation instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcf.create_cluster`        | <ul><li>The request to create a cluster for a Cloud Foundation instance is received.</li> <li>The request to create a cluster for a Cloud Foundation instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcf.delete_cluster`        | <ul><li>The request to delete a cluster from a Cloud Foundation instance is received.</li><li>The request to delete a cluster from a Cloud Foundation instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcf.schedule_update`       | <ul><li>The request to schedule an update for a Cloud Foundation instance is received.</li><li>The request to schedule an update for a Cloud Foundation instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>The request to order a vCenter Server instance is received.</li><li>The request to order a vCenter Server instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>The request to delete a vCenter Server instance is received.</li><li>The request to delete a vCenter Server instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>The request to add ESXi servers to a vCenter Server instance is received.</li><li>The request to add ESXi servers to a vCenter Server instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>The request to delete ESXi servers from a vCenter Server instance is received.</li><li>The request to delete ESXi servers from a vCenter Server instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>The request to schedule an update for a vCenter Server instance is received.</li><li>The request to schedule an update for a vCenter Server instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>The request to create a cluster for a vCenter Server instance is received.</li><li>The request to create a cluster for a vCenter Server instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>The request to delete cluster from a vCenter Server instance is received.</li> <li>The request to delete cluster from a vCenter Server instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>The request to update the VMware NSX license is received.</li><li>The request to update the VMware NSX license is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>The request to upgrade a vCenter Server instance to a vCenter Server with Hybridity Bundle instance is received.</li><li>The request to upgrade a vCenter Server instance to a vCenter Server with Hybridity Bundle instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>The request to order a vSphere cluster is received.</li><li>The request to order a vSphere cluster is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>The request to update a vSphere cluster is received.</li><li>The request to update a vSphere cluster is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>The request to save the configuration of a vSphere cluster is received.</li><li>The request to save the configuration of a vSphere cluster is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>The request to order a NetApp ONTAP Select instance is received.</li><li>The request to order a NetApp ONTAP Select instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>The request to delete a NetApp ONTAP Select instance is received.</li><li>The request to delete a NetApp ONTAP Select instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>The request to update the configuration of a service is received.</li><li>The request to update the configuration of a service is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>The request to order a service for an instance is received.</li><li>The request to order a service for an instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>The request to delete a service from an instance is received.</li><li>The request to delete a service from an instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>The request to upgrade an existing vCenter Server instance to a vCenter Server with Hybridity Bundle instance is received.</li><li>The request to upgrade an existing vCenter Server instance to a vCenter Server with Hybridity Bundle instance is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.service.deploy` | The action to deploy a service on an instance is run. | `success` |
| `vmware-solutions.service.undeploy` | The action to remove a service from an instance is run. | `success` |

## Tracking events for the KMIP for VMware on IBM Cloud service

When you manage keys for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service, an event is generated and sent to the **account domain** in Activity Tracker.

Check the following table for the actions that generate and send events for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service.

Table 3. Description of actions that generate events for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service

| Action                                      | Description                               | Outcome |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>The request to create a key is received.</li><li>The request to create a key is answered.</li></ul> | <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>The request to get the content of a key is received.</li><li>The request to get the content of a key is answered.</li></ul> |  <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>The request to get the attributes of a key is received.</li><li>The request to get the attributes of a key is answered.</li></ul> |  <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>The request to activate a key is received.</li><li>The request to activate a key is answered.</li></ul> |  <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>The request to revoke a key is received.</li><li>The request to revoke a key is answered.</li></ul> |  <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>The request to destroy a key is received.</li><li>The request to destroy a key is answered.</li></ul> |  <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>The request to find the version of the KMIP for VMware on {{site.data.keyword.cloud_notm}} service is received.</li><li>The request to find the version of the KMIP for VMware on {{site.data.keyword.cloud_notm}} service is answered.</li></ul> |  <ul><li>`pending`</li><li>`success` or `failure`</li></ul> |

## Where to view the events

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} **account domain** that is available in the {{site.data.keyword.Bluemix_notm}} region where the events are generated.

### Related links

* [Provisioning Activity Tracker](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [Navigating to the Activity Tracker dashboard in the {{site.data.keyword.cloud_notm}} Console](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip-for-vmware-on-ibm-cloud-overview)
