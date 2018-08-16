---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Additional limitations and considerations

Review the following considerations and limitations when you work with {{site.data.keyword.vmwaresolutions_full}}.

## Windows automatic installation of updates

The Microsoft Active Directory (AD) / Domain Name Server (DNS) is automatically set up to download the updates only. It does not install these updates or restart automatically. You must install the updates manually and restart at a scheduled time that avoids any interruptions of the ongoing AD server configuration and other backup jobs. To apply Windows updates, install the updates manually.

## Considerations when choosing a root domain name for Cloud Foundation instances

When choosing a domain name during the deployment of a primary or secondary Cloud Foundation instance, you need to verify that the `sddcmanager.<subdomain>` host name does not resolve to an external domain by using the `ping` or `nslookup` commands.

The structure of the Cloud Foundation instance subdomain is `<VCF instance name>.<domain name>`. For example, if your `<domain name>` is `test.local`, and the Cloud Foundation instance name is `mytest`, then the `sddcmanager.mytest.test.local` host name should not resolve to an IP address before deploying the Cloud Foundation instance. Otherwise, the instance deployment might fail.
