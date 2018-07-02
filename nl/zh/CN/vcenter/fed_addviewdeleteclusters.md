---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-12"

---

# 添加、查看和删除 VMware Federal 实例的集群

缺省情况下，订购实例时配置的 ESXi 服务器会分组为 **cluster1**。

可以向 VMware Federal 实例添加集群以扩展计算和存储容量。在集群中，可以管理 ESXi 服务器以获得更佳的资源分配和高可用性。不再需要添加的集群时，可以从实例中将其删除。

**可用性**：添加和删除集群功能仅可用于部署在（或已升级到）V2.3 和更高发行版中的实例。

## 向 VMware Federal 实例添加集群

最多可以向一个实例添加 10 个集群。为 VMware Federal 实例添加集群时，必须指定以下设置。

### 系统设置

为 VMware Federal 实例添加集群时，必须指定以下设置。

#### 集群名称

集群名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 集群名称必须以字母数字字符开头和结尾。
* 集群名称的最大长度为 30 个字符。
* 集群名称在 VMware Federal 实例中必须唯一。

#### 数据中心位置

缺省情况下，集群的数据中心设置为 VMware Federal 实例的数据中心。

### 裸机服务器设置

#### 定制

指定用于裸机服务器的 CPU 型号和 RAM。可用选项可能有所不同，具体取决于初始部署实例的版本。

表 1. 定制 {{site.data.keyword.baremetal_short}} 的选项

|CPU 选项|RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon E5-2620 V4 / 共 16 个核心，2.1 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|

#### 裸机服务器的数量

一个集群至少需要 2 个 {{site.data.keyword.baremetal_short}}。

对于在 V2.3 或更高版本中部署的 VMware Federal 实例，可以为一个集群最多添加 59 个 {{site.data.keyword.baremetal_short}}，并且一次可以添加 1 到 59 个 ESXi 服务器。

部署后，最多可以创建四个集群。对于 vSAN 存储设置，初始集群和部署后集群都需要 4 个服务器。

<!--When there are more than 51 ESXi servers in the initial cluster of an instance, the HCX on {{site.data.keyword.cloud_notm}} service cannot be installed into the instance. Because the HCX service requires 8 IPs in the vMotion subnet from the initial cluster, if the number of ESXi servers exceeds 51, no IPs in the vMotion subnet can be available for HCX service.-->

### 存储设置

存储设置基于您选择的是 vSAN、NFS 还是定制 NFS 存储器。

#### vSAN 存储器

对于 vSAN，指定以下存储选项：

* **vSAN 容量磁盘的磁盘类型和大小**：选择满足共享存储器需求的容量。
* **vSAN 容量磁盘数**：选择要添加的 vSAN 共享存储器的磁盘数。磁盘数量必须为 2、4、6 或 8 个。
* 选择 VMware vSAN 6.6 许可证版本（Advanced 或 Enterprise）。

如果初始集群为 vSAN，那么其他任何 VSAN 集群都会使用与初始 vSAN 集群相同的 vSAN 许可证并具有与初始 vSAN 集群相同的配置。如果实例中的任何集群选择了要部署 vSAN（初始或其他集群），也是如此。第一次系统会提示您提供 vSAN 许可证和版本。下次您可为其他集群选择 vSAN，这将复用您最初选择的任何内容。

#### NFS 存储器

选择 **NFS 存储器**时，可以为实例添加文件级别的共享存储器，其中所有共享使用相同的设置，也可以对每个文件共享指定不同的配置设置。请指定以下 NFS 选项：

**注：**文件共享数必须在范围 1 到 32 之间。

* **分别配置文件共享**：选择此项以对每个文件共享指定不同的配置设置。
* **共享数**：对每个文件共享使用相同的配置设置时，指定要添加的 NFS 共享存储器的文件共享数。
* **大小**：选择满足共享存储器需求的容量。
* **性能**：选择基于工作负载需求的 IOPS（每秒输入/输出操作数）/GB。
* **添加 NFS**：选择此项以添加将使用不同配置设置的单个文件共享。

表 2. NFS 性能级别选项

|选项|详细信息|
  |:------------- |:------------- |
  |2 IOPS/GB|此选项旨在用于大多数通用工作负载。示例应用包括：托管小型数据库、备份 Web 应用程序或系统管理程序的虚拟机磁盘映像。|
  |4 IOPS/GB|此选项旨在用于同时活动数据百分比高的更高强度工作负载。示例应用包括：事务性数据库。|
  |10 IOPS/GB|此选项旨在用于要求最苛刻的工作负载类型（如分析）。示例应用包括：高事务数据库和其他性能敏感型数据库。此性能级别限制为每个文件共享的最大容量为 4 TB。|

### 许可证设置

用于以下各项的 IBM 提供的 VMware 许可证：
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.3
  * （对于 vSAN 集群）VMware vSAN Advanced 或 Enterprise 6.6

### 订单摘要

根据为集群选择的配置，估算成本会立即生成并显示在**订单摘要**右侧窗格中。

## 向 VMware Federal 实例添加集群的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击要添加集群的实例。

   **注**：确保实例处于**可供使用**状态。否则，无法向实例添加集群。

3. 单击左侧导航窗格上的**基础架构**，然后单击**集群**表右上角的**添加**。
4. 在**添加集群**页面上，输入集群名称。
5. 针对裸机配置，选择 **CPU 型号**、**RAM** 量和**裸机服务器数**。
6. 填写存储配置。
  * 如果选择的是 **vSAN 存储器**，请选择 **vSAN 容量磁盘的磁盘类型和大小**、**vSAN 容量磁盘数**和 VMware vSAN 许可证版本。
  * 如果选择的是 **NFS 存储器**，请选择**共享数**、**大小**和**性能**。
  * 要单独添加并配置文件共享，请选择**定制 NFS 存储器**选项卡，单击**添加 NFS** 标签旁边的 **+** 图标，然后为每个文件共享选择**大小**和**性能**。必须至少选择一个文件共享。
7. 为 VMware vSAN 选择许可证版本，以进行许可证配置。
8. 在**订单摘要**窗格上，验证集群配置，然后再添加集群。
   1. 复查集群的设置。
   2. 复查集群的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在添加集群之前确认您同意这些条款。
   4. 单击**供应**。

## 向 VMware Federal 实例添加集群后的结果

1. 集群部署会自动启动，并且集群的状态会更改为**正在初始化**。可以通过在实例摘要页面中查看部署历史记录，以检查部署的状态。
2. 集群准备就绪可供使用后，其状态会更改为**可供使用**。将对新添加的集群启用 vSphere 高可用性 (HA) 和 vSphere 分布式资源调度程序 (DRS)。

**重要信息**：不能更改集群名称。更改集群名称可能会导致集群中添加或除去 ESXi 服务器的操作失败。

## 查看 VMware Federal 实例中的集群

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击实例以查看其中的集群。
3. 在左侧导航窗格上，单击**基础架构**。在**集群**表中，查看有关集群的摘要：
   * **名称**：集群的名称。
   * **ESXi 服务器数**：集群中的 ESXi 服务器数。
   * **CPU**：集群中 ESXi 服务器的 CPU 规范。
   * **定制 vSAN 磁盘数**：集群中的 vSAN 磁盘数，包括磁盘类型和容量。
   * **内存**：集群中 ESXi 服务器的内存总大小。
   * **数据中心位置**：托管集群的数据中心。
   * **pod**：在其中部署集群的 pod。
   * **状态**：集群的状态。状态可以是下列其中一个值：
     <dl class="dl">
         <dt class="dt dlterm">正在初始化</dt>
         <dd class="dd">正在创建并配置集群。</dd>
         <dt class="dt dlterm">正在修改</dt>
         <dd class="dd">正在修改集群。</dd>
         <dt class="dt dlterm">可供使用</dt>
         <dd class="dd">集群准备就绪，可供使用。</dd>
         <dt class="dt dlterm">正在删除</dt>
         <dd class="dd">正在删除集群。</dd>
         <dt class="dt dlterm">已删除</dt>
         <dd class="dd">集群已删除。</dd>
     </dl>
   * **操作**：单击**删除**图标以删除集群。
4. 单击集群名称以查看 ESXi 服务器、存储和许可证详细信息。

### ESXi 服务器

   * **名称**：ESXi 服务器名称的格式为 `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中：

      `host_prefix` 是主机名前缀，
      `n` 是 ESXi 服务器的序列，
      `subdomain_label` 是子域标签，
      `root_domain` 是根域名。

   * **版本**：ESXi 服务器的版本。
   * **凭证**：用于访问 ESXi 服务器的用户名和密码。
   * **专用 IP**：ESXi 服务器的专用 IP 地址。
   * **状态**：ESXi 服务器的状态，可以是下列其中一个值：
        <dl class="dl">
        <dt class="dt dlterm">已添加</dt>
        <dd class="dd">ESXi 服务器已添加并准备就绪可供使用。</dd>
        <dt class="dt dlterm">正在添加</dt>
        <dd class="dd">正在添加 ESXi 服务器。</dd>
        <dt class="dt dlterm">正在删除</dt>
        <dd class="dd">正在删除 ESXi 服务器。</dd>
        </dl>

### 存储

   * **名称**：数据存储名称。
   * **大小**：存储器的容量。
   * **IOPS/GB**：存储器的性能级别。
   * **NFS/门户网站**：存储器的 NFS 版本。
   * **状态**：存储器的状态，可以是下列某个值：
          <dl class="dl">
        <dt class="dt dlterm">已添加</dt>
        <dd class="dd">ESXi 服务器已添加并准备就绪可供使用。</dd>
        <dt class="dt dlterm">正在添加</dt>
        <dd class="dd">正在添加 ESXi 服务器。</dd>
        <dt class="dt dlterm">正在删除</dt>
        <dd class="dd">正在删除 ESXi 服务器。</dd>
        </dl>

### 许可证

   * **许可证**：许可证类型。
   * **订购类型**：许可证是 IBM 提供的还是用户提供的。
   * **许可证修订版**：许可证的版本和修订版。
   * **许可证密钥**：许可证密钥。
   * **总容量 (CPU)**：许可证的 CPU 总容量。
   * **可用容量 (CPU)**：许可证的可用 CPU 容量。

## 从 VMware Federal 实例中删除集群

当不再需要集群时，您可能希望将其从实例中删除。

**注**：使用此过程可从部署在（或已升级到）V2.3 和更高发行版中的实例中删除集群。

### 删除之前

* 使用此过程从部署在 V2.3 或更高发行版中的实例中删除集群。
* 对于在 V2.2 或更低版本实例中部署的集群，必须将实例升级到 V2.3，才能删除已添加到实例的集群。
* 一次可以删除一个集群。要删除多个集群，必须按顺序依次执行；请等待前一个集群删除后，再尝试删除下一个集群。
* 删除集群之前，请确保集群中的所有节点都已打开电源且正常运行。
* 删除集群时，集群中的所有 VM（虚拟机）也会一起删除且无法恢复。如果要保留这些 VM，请将其迁移到其他集群。
* 无法删除缺省集群。

## 从 VMware Federal 实例中删除集群的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击要从中删除集群的实例。

   **注**：确保实例处于**可供使用**状态。否则，无法从实例中删除集群。

3. 在左侧导航窗格上，单击**基础架构**。在**集群**表中，找到要删除的集群，然后单击**操作**列中的**删除**图标。

## 相关链接

* [查看 VMware Federal 实例](vc_fed_viewinginstance.html)
* [扩展和收缩 VMware Federal 实例的容量](vc_fed_addingremovingservers.html)