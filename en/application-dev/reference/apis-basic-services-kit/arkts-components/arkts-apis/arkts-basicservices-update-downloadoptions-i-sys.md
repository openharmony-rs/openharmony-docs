# DownloadOptions (System API)

Defines the download options, including the **allowNetwork** and **order** fields, which are used to control the download behavior.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## allowNetwork

```TypeScript
allowNetwork: NetType
```

Network type allowed for download. The value **CELLULAR** indicates that only download over the cellular network is allowed; **WiFi** that only download using Wi-Fi is allowed; **CELLULAR_AND_WIFI** indicates that download over both the cellular network and Wi-Fi is allowed. You are advised to select a network type based on the upgrade package size and network environment. If the upgrade package is big, you are advised to set the network type to **WIFI** to reduce mobile data usage and improve the download speed. If you are in a mobile scenario or there is no Wi-Fi available, you can set the network type to **CELLULAR**. If the network environment is uncertain, you are advised to set the network type to **CELLULAR_AND_WIFI**.

**Type:** [NetType](arkts-basicservices-update-nettype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## order

```TypeScript
order: Order
```

The options are as follows: **DOWNLOAD**: download the upgrade package, which needs to be manually installed later; **INSTALL**: install the upgrade package that has been downloaded; **DOWNLOAD_AND_INSTALL**: download and install the upgrade package, which is the complete upgrade process; **APPLY**: apply the upgrade package that has been installed by restarting device; **INSTALL_AND_APPLY**: install the upgrade package and apply it immediately by restarting the device.

**Type:** [Order](arkts-basicservices-update-order-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
