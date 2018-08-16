---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Managing system notifications

You can check notifications for the status of system or user operations. You can also use the information to investigate problems that might occur.

## Viewing notifications

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Notifications** from the left navigation pane.
2. In the **Notification History** table, view the summary about all notifications.

   Table 1. Notification history

    <table>
      <tr>
        <th>Column</th>
        <th>Description</th>
      </tr>
      <tr>
        <td>Severity</td>
        <td>The severity of the event that is reported by the notification.
          <dl class="dl">
          <dt class="dt dlterm">Critical</dt>
          <dd class="dd">A critical event might impact the entire system or service.</dd>
          <dt class="dt dlterm">Error</dt>
          <dd class="dd">An error event occurs during an operation that might need intervention from the administrator or the user.</dd>
          <dt class="dt dlterm">Warning</dt>
          <dd class="dd">A component fails or is not working properly. However, the failure does not disrupt the ongoing process of the component.</dd>
            <dt class="dt dlterm">Informational</dt>
            <dd class="dd">A system or user operation is completed. Typically, the following events report informational notifications:
              <ul class="ul">
                <li class="li">A service is installed.</li>
                <li class="li">A service is upgraded.</li>
                <li class="li">A service is removed.</li>
                <li class="li">All services are reconfigured for the added ESXi servers.</li>
                <li class="li">All services are reconfigured for the removed ESXi servers.</li>
              </ul>
            </dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>Type</td>
         <td>The type of component that the reported event is related to:<ul><li>vCenter Server instances</li><li>Cloud Foundation instances</li><li>Services</li><li>System</li></ul></td>
       </tr>
       <tr>
         <td>Resource</td>
         <td>The name of the instance or service that sends the notification.</td>
       </tr>
       <tr>
         <td>Description</td>
         <td>A short description of the notification.</td>
       </tr>
       <tr>
         <td>Date</td>
         <td>The date and time when the notification is sent.</td>
       </tr>
    </table>                                       

3. Click a notification row to view the details of the notification.

## Filtering notifications

By default, all unread notifications are displayed. You can filter the notifications by status, severity, and type. To filter the notifications, select the check boxes only for the items that you want to display in the **Status**, **Severity**, or **Type** lists.

### Related links

* [FAQ](faq.html)
* [User account and settings](useraccount.html)
