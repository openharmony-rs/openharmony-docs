# ResumeDownloadOptions (System API)

Defines the resuming download options, which are used to specify the network type for resuming download. The object includes the **allowNetwork** field, which specifies the network type allowed for download.

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

Network type allowed for resuming download. This parameter is set only after the **pauseDownload** API is called to pause download. The value **CELLULAR** indicates that only download resumption over the cellular network is allowed; **WiFi** that only download resumption using Wi-Fi is allowed; **CELLULAR_AND_WIFI** indicates download resumption over both the cellular network and Wi-Fi is allowed. You are advised to select a network type based on the upgrade package size and network environment. If the upgrade package exceeds 100 MB, you are advised to set the network type to **WIFI** to reduce mobile data usage and improve the download speed. If you are in a mobile scenario or there is no Wi-Fi available, you can set the network type to **CELLULAR**. If the network environment is uncertain, you are advised to set the network type to **CELLULAR_AND_WIFI**.

**Type:** [NetType](arkts-basicservices-update-nettype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
