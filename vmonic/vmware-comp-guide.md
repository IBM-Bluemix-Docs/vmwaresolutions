---

copyright:

  years:  2020, 2021

lastupdated: "2021-03-15"

keywords: vmware compatibility, vsan compatibility, product compatibility

subcollection: vmwaresolutions

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Product compatibility guide
{: #vmware-comp-guide}

Review the following tables for information about the products and versions that are supported in the current release of {{site.data.keyword.vmwaresolutions_full}}.

## Intel processors reference
{: #vmware-comp-guide-intel}

| CPU series | Cores and threads | CPUID information | CPUIDs | IBM-supported releases | Link |
|:---------- |:------------- |:---------- |:------ |:---------------------- |:---- |
| Intel® Xeon™ Gold 6200/5200 (Cascade Lake-SP) Series | 28 c, 56 t | 6.55.6</br>6.55.7 | 0x00050656</br>0x00050657 | VMware ESXi™ 6.7u2, 6.7u1, 6.7, 6.5u3 | [VMware® compatibility guide - CPU](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=cpu&productid=128&deviceCategory=cpu&details=1&cpu_series=128,129,130&page=1&display_interval=10&sortCol umn=Partner&sortOrder=Asc) |
| Intel Xeon Silver 4200, Bronze 3200 (Cascade Lake-SP) Series | 28 c, 56 t | 6.55.6</br>6.55.7 | 0x00050656</br>0x00050657 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3 | [VMware compatibility guide - CPU](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=cpu&productid=130&deviceCategory=cpu&details=1&cpu_series=128,129,130&page=1&display_interval=10&sortCol umn=Partner&sortOrder=Asc) |
| Intel Xeon Platinum 8200 (Cascade Lake-SP) Series | 28 c, 56 t | 6.55.6</br>6.55.7 | 0x00050656</br>0x00050657 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3 | [VMware compatibility guide - CPU](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=cpu&productid=129&deviceCategory=cpu&details=1&cpu_series=128,129,130&page=1&display_interval=10&sortCol umn=Partner&sortOrder=Asc) |
| Intel Xeon Gold 6100/5100, Silver 4100, Bronze 3100 (Skylake-SP) Series | 28 c, 56 t | 6.55.4 | 0x00050654 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2 | [VMware compatibility guide - CPU](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=cpu&productid=119&deviceCategory=cpu&details=1&cpu_series=119&page=1&display_interval= 10&sort Colum n=Partner&sortOrder=Aschttps://www.google.com/?gws_rd=ssl) |
| Intel Xeon E5-2600-v4 Series | 24c, 48 t | 6.4F | 0x000406F0 | ESXi 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | [VMware compatibility guide - CPU](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=cpu&productid=111&deviceCategory=cpu&details=1&cpu_series=111&page=1&display_interval= 10&sort Colum n=Partner&sortOrder=Aschttps://www.google.com/?gws_rd=ssl) |
| Intel Xeon E7-8800/4800-v4 Series | 24c, 48 t | 6.4F | 0x000406F0 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u2, 6.5u1, 6.5, 6.0 | [VMware compatibility guide - CPU](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=cpu&productid=116&deviceCategory=cpu&details=1&cpu_series=116&page=1&display_interval= 10&sort Colum n=Partner&sortOrder=Aschttps://www.google.com/?gws_rd=ssl) |
| Intel Xeon E-2174G | 4c, 8t | 6.9E.A | 0x000906EA, EB, EC | ESXi 6.7u3, 6.7u2, 6.5u3 | [VMware Compatibility guide - CPU](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=cpu&details=1&cpu_series=127&page=1&display_i nterval=10&sortColumn=Partner&sortOrder=Asc) |
{: caption="Table 1. Intel processors reference" caption-side="top"}

## SuperMicro server reference
{: #vmware-comp-guide-supermicro-server}

| Server configuration | MOBO | CPU | RAID | NIC | Trusted Platform Module |
|:-------------------- |:---- |:--- |:---- |:--- |:--- |
| PIO-628U-TR4T +-ST031 (1U/2U)</br>SYS-6028U-TR4T+ | X10DRU-i+_R1.02b | E5-2600-v4</br>Intel C612 chipset | (LSI) MegaRAID SAS 9361-8i | AOC-2UR6-i4XT</br>Intel X540-AT2 | AOM-TPM-9655V |
| PIO-648R-E1CR36L +-ST031 (4U)</br>SSG-6048R-E1CR36N | X10DRI-T4+</br>X10DRI-T4+_1.02 | E5-2600-v4</br>Intel C612 chipset | (LSI) MegaRAID SAS 9361-8i | 4x Onboard X540 Quad port 10GBase-T Intel X540 | AOM-TPM-9655V |
| PIO-8048B-TRF4T-ST031 (4U)</br>SYS-8048B-TR4FT | X10QBI_R1.01AX10QBi_R1.01B – MEM1 | E7-8800/4800/2800-v2</br>Intel C602J Chipset | (LSI) MegaRAID SAS 9361-8i | AOC-STG-i2T | Onboard |
| PIO-8048B-TRF4T-ST031 (4U)</br>SYS-8048B-TR4FT | X10QBi-MEM2 REV 1.21 | E7-8800/4800-v4</br>Intel C602J Chipset | (LSI) MegaRAID SAS 9361-8i | AOC-STG-i2T | Onboard |
| PIO-6029U-E1CR4T-ST031 (2U)</br>SYS-6029U-E1CR4T | X11DPU+</br>X11DPU+_R1.10 | Intel Xeon Platinum 8100, Gold 6100/5100, Silver 4100, Bronze 3100 (Skylake-SP) Series, Intel Xeon Platinum 8200, Gold 6200/5200 (Cascade-Lake-SP) Series</br>Intel C621 chipset | (LSI) MegaRAID SAS 9361-8i | AOC-2UR66-i4XTF (2U) </br>Intel XL710 | AOM-TPM-9671V |
| PIO-6019U-TN4R4T-ST031 (1U)</br>SYS-6019U-TN4R4T | X11DPU+</br>X11DPU+_R1.10 | Intel Xeon™ Platinum 8100, Gold 6100/5100, Silver 4100, Bronze 3100 (Skylake-SP) Series, Intel® Xeon™ Platinum 8200, Gold 6200/5200 (Cascade-Lake-SP) Series</br>Inten C621 chipset | (LSI) MegaRAID 9461-16i | AOC-UR-i4XTF (1U) Intel XL710 | AOM-TPM-9671V |
| SYS-2049U-TR4 | X11QPH+ R1.02 | Intel Xeon Platinum 8200/6200/5200 (Cascade Lake-SP) Series</br>Intel C621 chipset | (LSI) MegaRAID 9461-16i | Intel X710-T4. More NICs X710-T4 can be installed in top RAID (secondary) slot | AOM-TPM-9671V |
| SYS-5019C-WR | X11SCW-F R1.02 | Intel Xeon E-2174G Single Socket H4 (LGA 1151) Intel C246 Chipset | (LSI) MegaRAID SAS 9361-8i | 4-Port AOC-STG-i4T based on Intel X710 | AOM-TPM-9671V |
{: caption="Table 2. SuperMicro server reference" caption-side="top"}

## Lenovo server reference
{: #vmware-comp-guide-lenovo-server}

| Server configuration | MOBO | CPU | RAID | NIC | TPM |
|:-------------------- |:---- |:--- |:---- |:--- |:--- |
| ThinkSystem SR650 | SR650 | Intel Xeon Gold 6200/5200, Silver 4210 | LSI MegaRAID SAS 9461-16i | Intel / X710-T4 / Intel 10 Gigabit 4 Port/4 |
| ThinkSystem SR950 | SR950 | Intel Xeon Platinum 8280M | LSI MegaRAID SAS 9461-16i | Intel / X710-T4 / Intel 10 Gigabit 4 Port/4 |
{: caption="Table 3. Lenovo server reference" caption-side="top"}

## SuperMicro BIOS levels reference
{: #vmware-comp-guide-supermicro-bios}

| Server configuration | MOBO | CPU | {{site.data.keyword.cloud_notm}} infrastructure BIOS level | SMC BIOS | IBM-supported releases | Link |
|:-------------------- |:---- |:--- |:----------------------------------- |:-------- |:---------------------- |:---- |
| PIO-628U-TR4T+-ST031 (1U/2U)</br>SYS-6028U-TR4T+ | X10DRU-i+_R1.02b</br>X10DRU-i+_R1.10 | E5-2600-v4</br>Intel C612 chipset | 3.1, 8 June 2018 | American Megatrends Inc. 3.1 (Boot Mode - Legacy BIOS) | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&productid=42370&deviceCategory=server&details=1&partner=105&keyword=SYS-6028U-TR4T%20%20&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| PIO-648R-E1CR36L+-ST031 (4U)</br>SSG-6048R-E1CR36N | X10DRI-T4+</br>X10DRI-T4+_1.02 | E5-2600-v4</br>Intel C612 chipset | 3.1 06-08-2018 | American Megatrends Inc. 3.1 (Boot Mode - Legacy BIOS) | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&productid=46813&deviceCategory=server&details=1&keyword=SSG-6048R-E1CR36N&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| PIO-848B-TR4F4T-ST031 (4U)</br>SYS-8048B-TR4FT | X10QBi-MEM2 REV 1.21 | E7-8800/4800-v4</br>Intel C602J Chipset | 3.1 06-12-2018 | American Megatrends Inc. 3.1 (Boot Mode - Legacy BIOS) | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&productid=45398&deviceCategory=server&details=1&keyword=SYS-8048B-TR4FT&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| PIO-6029U-E1CR4T-ST031 (2U)</br>SYS-6029U-E1CR4T | X11DPU+</br>X11DPU+_R1.10 | Intel Xeon Platinum 8100, Gold 6100/5100, Silver 4100, Bronze 3100 (Skylake-SP) Series, Intel Xeon Platinum 8200, Gold 6200/5200 (Cascade-Lake-SP) Series</br>Intel C621 chipset | 3.1a, 25 September 2019 or 3.3, 21 February 2020 | 3.1a, 25 September 2019 | ESXi 6.7u3, 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&productid=49256&deviceCategory=server&details=1&keyword=SYS-6029U-E1CR4T&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| PIO-6019U-TN4R4T-ST031 (1U)</br>SYS-6019U-TN4R4T | X11DPU+</br>X11DPU+_R1.10 | Intel Xeon Platinum 8100, Gold 6100/5100, Silver 4100, Bronze 3100 (Skylake-SP) Series, Intel Xeon Platinum 8200, Gold 6200/5200 (Cascade-Lake-SP) Series</br>Intel C621 chipset | 3.1a, 25 September 2019 or 3.3, 21 February 2020 | 3.1a, 25 September 2019 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&productid=44741&deviceCategory=server&details=1&keyword=SYS-6019U-TN4R4T%20&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| SYS-2049U-TR4 (2u) | X11QPH+ R1.02 | Intel Xeon Platinum 8200, Gold 6200/5200 (Cascade-Lake-SP) Series</br>Intel C621 chipset | 3.0c, 20 March 2019 for MOBO Rls R1.01</br>3.1, 1 May 2019 for MOBO Rls R1.02 and R1.20 | American Megatrends Inc. 3.0c UEFIBIOS (Boot Mode - UEFI) and (Boot Mode - Legacy BIOS) | ESXi 6.7u2, 6.7u1 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=server&details=1&keyword=SYS-2049U-TR4&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| SYS-5019C-WR | X11SCW-F R1.02 | Intel Xeon E-2174G Single Socket H4 (LGA 1151) Intel C246 Chipset | 1.2 12-3-2019 | American Megatrends Inc. 1.2 (Boot Mode - Legacy BIOS) | ESXi 6.7u3, 6.7u2, 6.5u3 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&productid=49981&vcl=true) |
{: caption="Table 4. SuperMicro BIOS levels reference" caption-side="top"}

## Lenovo BIOS levels reference
{: #vmware-comp-guide-lenovo-bios}

| Server configuration | MOBO | CPU | {{site.data.keyword.cloud_notm}} infrastructure BIOS Level | Lenovo BIOS | IBM-supported releases | Link |
|:-------------------- |:---- |:--- |:----------------------------------- |:----------- |:---------------------- |:---- |
| ThinkSystem SR650 | SR650 | Dual Intel Xeon Cascade Lake Scalable CPU Support Intel C621 chipset | 2.51 1-14-2020 | Lenovo - [IVE152L-2.51] -  UEFI Mode (Boot Mode - UEFI) | ESXi 6.7u3, 6.7U2, 6.5u3 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&productid=48424&deviceCategory=server&details=1&partner=51&keyword=SR650&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| ThinkSystem SR950 | SR950 | Intel Xeon Platinum 8200 (Cascade-Lake-SP) Series Intel C624 chipset | 1.70 10-16-2019 | Lenovo - [PSE128K-1.70] - UEFI Mode (Boot Mode - UEFI) | ESXi 6.7u3, 6.7U2, 6.5u3 | [VMware compatibility guide - System](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&productid=47668&deviceCategory=server&details=1&partner=51&keyword=SR950&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
{: caption="Table 5. Lenovo BIOS levels reference" caption-side="top"}

## RAID controllers reference
{: #vmware-comp-guide-raid-control}

| Model | Drivers | Firmware | Supported releases | Link |
|:----- |:------- |:-------- |:------------------ |:---- |
| (LSI) MegaRAID SAS 9361-8i | lsi-mr3 version 7.703.18.00-1OEM.650 | 4.680.00-8301 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | [VMware compatibility guide - I/O device](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vsanio&productid=40379&deviceCategory=vsanio&details=1&vsan_type=vsanio&io_partner=50&keyword=MegaRAID%20SAS%209361-8i&page=1&display_interval=50&sortColumn=Partner&sortOrder=Asc) |
| (LSI) MegaRAID SAS 9461-16i (Cascade Lake servers) | lsi_mr3 version 7.709.10.00-1OEM.670 | 5.070.00-1894 | ESXi 6.7 U2 (vSAN™ 6.7 Update 2), ESXi 6.7 U1 (vSAN 6.7 Update 1), ESXi 6.7 (vSAN 6.7), 6.5u3 | [VMware compatibility guide - I/O device](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vsanio&productid=45822&deviceCategory=vsanio&details=1&vsan_type=vsanio&keyword=9461-16i&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| (LSI) MegaRAID SAS 9461-16i (Cascade Lake servers) </br>**Under test** | lsi_mr3 version 7.713.08.00-1OEM | 5.130.00-3059 | ESXi 6.7u3, 6.7u2, 6.5u3 | [VMware compatibility guide - I/O device](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=io&productid=48422&deviceCategory=io&details=1&keyword=48422) |
{: caption="Table 6. RAID Controllers reference" caption-side="top"}

## NICs with Intel Network adapter reference
{: #vmware-comp-guide-nics}

| Model | Drivers | Firmware | IBM-supported releases | Link |
|:----- |:------- |:-------- |:---------------------- |:---- |
| AOC-2UR6-i4XT | ixgbe version 4.4.1</br>ixgben version 1.5.3 | N/A</br>N/A | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | [VMware compatibility guide - I/O device](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=io&productid=42956&deviceCategory=io&details=1&partner=105&keyword=AOC-2UR6-i4XT&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| AOC-STG-i2T | ixgbe version 4.4.1</br>ixgben version 1.5.3 | N/A</br>N/A | ESXi 6.7u2, 6.7u1, 6.7, 6.5u2, 6.5u1, 6.5, 6.0 | [VMware compatibility guide - I/O device](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=io&productid=38693&deviceCategory=io&details=1&partner=105&keyword=AOC-STG-I2T&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| AOC-2UR66-i4XTF (2U) | i40en version 1.7.11 | 6.01 | ESXi 6.7u3, 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2 | [VMware compatibility guide - I/O device](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=io&productid=45006&deviceCategory=io&details=1&partner=105&keyword=AOC-2UR66-i4XTF&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| Secondary NIC - Intel / X710/X557-AT 10GBASE-T | i40en version 1.7.5 | 6.01 | ESXi 6.7u3, 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2 | [VMware compatibility guide - I/O device](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=io&productid=40583&deviceCategory=io&details=1&partner=46&keyword=Intel%20Corporation%20Ethernet%20Controller%20X710/X557-AT%2010GBASE-T&VID=8086&DID=1589&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| Intel Ethernet Network adapter E810-XXV-4 | `icen` Version 1.0.6 | 1.02 | ESXi 6.7u3, 6.7u2 | [VMware compatibility guide - I/O device](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=io&productid=49358&deviceCategory=io&details=1&keyword=E810-XXV-4&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
{: caption="Table 7. NICs with Intel Network Adapter reference" caption-side="top"}

## Micron SSDs reference
{: #vmware-comp-guide-micron-ssd}

| Model | Capacity | {{site.data.keyword.cloud_notm}} infrastructure firmware | vSAN HCL firmware | IBM-supported releases | Applicable to | Link |
|:----- |:-------- |:--------------------------------- |:----------------- |:---------------------- |:------------- |:---- |
| 5100</br>MTFDDAK960TCC-1AR16ABYY | 960 GB | D0MU051 | D0MU051 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=ssd&productid=41212&deviceCategory=ssd&details=1&vsan_type=vsanssd&ssd_partner=454&keyword=MTFDDAK960TCC-1AR16ABYY&vsanrncomp=true&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| 5100</br>MTFDDAK1T9TCC-1AR16ABYY | 1920 GB | D0MU051 | D0MU051 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=ssd&productid=41375&deviceCategory=ssd&details=1&vsan_type=vsanssd&ssd_partner=454&keyword=%20MTFDDAK1T9TCC-1AR16ABYY&vsanrncomp=true&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| 5100</br>MTFDDAK3T8TCB-1AR16ABYY | 3840 GB | D0MU417 | D0MU417 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=ssd&productid=41440&deviceCategory=ssd&details=1&vsan_type=vsanssd&ssd_partner=454&keyword=%20MTFDDAK3T8TCB-1AR16ABYY&vsanrncomp=true&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| 5200</br>MTFDDAK960TDN-1AT16ABYY | 960 GB | D1MU020 | D1MU020 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vfrc&productid=43546&deviceCategory=vfrc&details=1&keyword=MTFDDAK960TDN-1AT16ABYY&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| 5200</br>MTFDDAK1T9TDN-1AT16ABYY | 1920 GB | D1MU020 | D1MU020 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vfrc&productid=43547&deviceCategory=vfrc&details=1&keyword=MTFDDAK1T9TDN-1AT16ABYY&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| 5200</br>MTFDDAK3T8TDD-1AT16ABYY | 3840 GB | D1MU520 | D1MU520 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vfrc&productid=43996&deviceCategory=vfrc&details=1&keyword=MTFDDAK3T8TDD-1AT16ABYY&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| 5300</br>MTFDDAK960TDT-1AW16ABYY | 960 GB | D3MC000.1 | D3MC000.1 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=ssd&productid=46010&deviceCategory=ssd&details=1&vsan_type=vsanssd&keyword=MTFDDAK960TDT-1AW16ABYY&vsanrncomp=true&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| 5300</br>MTFDDAK1T9TDT-1AW16ABYY | 1920 GB | D3MC000.1 | D3MC000.1 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=ssd&productid=45992&deviceCategory=ssd&details=1&vsan_type=vsanssd&keyword=MTFDDAK1T9TDT-1AW16ABYY&vsanrncomp=true&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| 5300</br>MTFDDAK3T8TDT-1AW16ABYY | 3840 GB | D3MU401.1 | D3MU401.1 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=ssd&productid=46000&deviceCategory=ssd&details=1&vsan_type=vsanssd&keyword=MTFDDAK3T8TDT-1AW16ABYY&vsanrncomp=true&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
{: caption="Table 8. Micron SSDs reference" caption-side="top"}

Do not mix SSD vendors in vSAN servers or clusters.
{:note}

## Intel SSDs reference
{: #vmware-comp-guide-intel-ssd}

| Model | Capacity | {{site.data.keyword.cloud_notm}} infrastructure firmware | vSAN HCL firmware | IBM-supported releases | Applicable to | Link |
|:----- |:-------- |:--------------------------------- |:----------------- |:---------------------- |:------------- |:---- |
| Intel SSD D3-S4610 Series SSDSC2KG960G8 (960 GB, 2.5") | 960 GB | XCV10100 | XCV10100 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vfrc&productid=43954&deviceCategory=vfrc&details=1&keyword=SSDSC2KG960G8&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| Intel SSD D3-S4610 Series SSDSC2KG019T8 (1.92 TB, 2.5”) | 1920 GB | XCV10100 | XCV10100 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vfrc&productid=43950&deviceCategory=vfrc&details=1&keyword=SSDSC2KG019T8&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| Intel SSD D3-S4610 Series SSDSC2KG038T8 (3.84 TB, 2.5”) | 3840 GB | XCV10100 | XCV10100 | ESXi 6.7u2, 6.7u1, 6.7, 6.5u3, 6.5u2, 6.5u1, 6.5, 6.0 | vSAN All Flash Caching Tier</br>vSAN All Flash Capacity Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vfrc&productid=43951&deviceCategory=vfrc&details=1&keyword=SSDSC2KG038T8&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
{: caption="Table 9. Intel SSDs reference" caption-side="top"}

Do not mix SSD vendors in vSAN servers or clusters.
{:note}

## Intel Optane reference
{: #vmware-comp-guide-intel-optane}

| Model | Capacity | Dev driver | Firmware | IBM-supported releases | Applicable to | Link |
|:----- |:-------- |:---------- |:-------- |:---------------------- |:------------- |:---- |
| Intel Optane™ SSD DC P4800X Series SSDPED1K750GA (750 GB, HHHL) | 750 GB | intel-nvme-vmd 1.4.0.1016-1OEM.650 async (Note: 650 identifies ESXi 6.5) | E2010435 | ESXi 6.7u2, 6.7u1, 6.7 | vSAN All Flash Caching Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vfrc&productid=42966&deviceCategory=vfrc&details=1&keyword=SSDPED1K750GA%20&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
| Intel Optane SSD DC P4800X Series SSDPED1K750GA (750 GB, HHHL) | 750 GB | intel-nvme-vmd 1.4.0.1016-1OEM.670 async (670 identifies ESXi 6.7) | E2010435 | ESXi 6.7u2, 6.7u1, 6.7 | vSAN All Flash Caching Tier | [VMware compatibility guide - SSD](https://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vfrc&productid=42966&deviceCategory=vfrc&details=1&keyword=SSDPED1K750GA%20&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc) |
{: caption="Table 10. Intel Optane reference" caption-side="top"}

## Related links
{: #vmware-comp-guide-related}

* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [vCenter Server overview](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)
* [VMware vSphere® overview](/docs/vmwaresolutions?topic=vmwaresolutions-vs_vsphereclusteroverview)
* [vCenter Server BOM](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom)
* [VMware vSphere BOM](/docs/vmwaresolutions?topic=vmwaresolutions-vs_bom)
