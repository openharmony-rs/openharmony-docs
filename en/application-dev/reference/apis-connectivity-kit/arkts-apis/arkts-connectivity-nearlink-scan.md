# @ohos.nearlink.scan(NearLink Scanning Capability)

This module provides the definition of the NearLink scanning mode.

**Since:** 26.0.0

<!--Device-unnamed-declare namespace scan--><!--Device-unnamed-declare namespace scan-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [offDeviceFound](arkts-connectivity-scan-offdevicefound-f.md#offdevicefound) | Unsubscribes from NearLink scanning results. This API uses an asynchronous callback to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md#ondevicefound) | Subscribes to NearLink scanning results. This API uses an asynchronous callback to return the result. |
| [startScan](arkts-connectivity-scan-startscan-f.md#startscan) | Starts NearLink scanning. This API uses a promise to return the result. You need to call [scan.onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md) to subscribe to the scanning results. After this API initiates scanning, the scanned device information is reported through the [scan.onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md) callback. After the scanning is complete, you can call [scan.stopScan](arkts-connectivity-scan-stopscan-f.md) to stop scanning. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [stopScan](arkts-connectivity-scan-stopscan-f.md#stopscan) | Stops NearLink scanning. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |

### Interfaces

| Name | Description |
| --- | --- |
| [ScanFilters](arkts-connectivity-scan-scanfilters-i.md) | Defines the scan filters |
| [ScanOptions](arkts-connectivity-scan-scanoptions-i.md) | Represents the scan options. |
| [ScanResults](arkts-connectivity-scan-scanresults-i.md) | Represents the scanning results. |

### Enums

| Name | Description |
| --- | --- |
| [ScanMode](arkts-connectivity-scan-scanmode-e.md) | Enumerates the scan modes. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ScanMode](arkts-connectivity-scan-scanmode-e-sys.md) | Enumerates the scan modes. |
<!--DelEnd-->
