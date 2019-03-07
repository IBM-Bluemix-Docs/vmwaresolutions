---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

# 訂購 KMIP for VMware on IBM Cloud 實例

您可以訂購 KMIP for VMware on {{site.data.keyword.cloud}} 實例，而未將它關聯至任何 VMware 實例，以彈性管理服務及實例。

## 開始之前

請確定您已完成下列作業：
*  您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic/useraccount.html)。
*  您已檢閱[安裝 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例時的考量](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html)中的所有考量。

## 訂購 KMIP for VMware on IBM Cloud 實例

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**開始使用**。
2. 在**訂購其他服務**區域中，按一下 **KMIP for VMware on IBM Cloud**。
3. 在 **KMIP for VMware on IBM Cloud** 頁面上，視需要配置服務設定。
4. 按一下**佈建**。

## KMIP for VMware on IBM Cloud 服務配置

當您訂購此服務時，請提供下列設定：

### 實例名稱

指定 KMIP for VMware {{site.data.keyword.cloud_notm}} 實例的名稱。

### 服務地區

選取要在其中管理 KMIP for VMware {{site.data.keyword.cloud_notm}} 實例的 {{site.data.keyword.cloud_notm}} 地區。

{{site.data.keyword.cloud_notm}} 在服務可用的每一個地區中都會維護高度可用的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務端點。

表 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務端點地區

|地區           |端點|
|:---------------|:-----------------------|
|德國           |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
|東京| <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
|美國南部       |  <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### 服務 ID 的 API 金鑰

輸入用來存取 IBM Key Protect Service 實例之「{{site.data.keyword.cloud_notm}} 服務 ID」的 API 金鑰。

### Key Protect 實例

按一下**擷取**，以取得可用 IBM Key Protect Service 實例的清單，然後選取用於金鑰管理的實例。

### 客戶主要金鑰

按一下**擷取**，以取得所選取 IBM Key Protect 實例中儲存的客戶主要金鑰。

## 結果

自動啟動實例的訂購。您會收到正在處理訂單的確認，而且您可以檢視實例詳細資料來檢查訂單的狀態。

實例備妥可供使用時，實例的狀態會變更為**已安裝**，而且您會透過電子郵件收到通知。

## 下一步

新增所訂購 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例的用戶端憑證。如需相關資訊，請參閱[新增、檢視及刪除 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例的憑證](/docs/services/vmwaresolutions/services/kmip_standalone_addingdeletingcert.html)。

### 相關鏈結

* [檢視 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [刪除 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [Activity Tracker 事件](/docs/services/vmwaresolutions/vmonic/at-events.html)