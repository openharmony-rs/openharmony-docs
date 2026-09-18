# startScan

## Modules to Import

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## startScan

```TypeScript
function startScan(filters: ScanFilters[] | null, options?: ScanOptions): Promise<void>
```

Starts NearLink scanning. This API uses a promise to return the result. You need to call [scan.onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md) to subscribe to the scanning results. After this API initiates scanning, the scanned device information is reported through the [scan.onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md) callback. After the scanning is complete, you can call [scan.stopScan](arkts-connectivity-scan-stopscan-f.md) to stop scanning.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filters | [ScanFilters](arkts-connectivity-scan-scanfilters-i.md)[] &#124; null | Yes | Filter criteria for NearLink advertising. Devices that meet the filter criteria will be reported. If the filter is not enabled, **null** is passed.<br>If this parameter is set to **null**, all discoverable NearLink devices nearby will be scanned. However, this method is not recommended as it may pick up unexpected devices and increase power consumption. |
| options | [ScanOptions](arkts-connectivity-scan-scanoptions-i.md) | No | Scan options. The low power consumption mode is used by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100040](../errorcode-nearlink-service.md#36100040-integer-out-of-range) | Integer out of range. |
| [36100041](../errorcode-nearlink-service.md#36100041-invalid-url) | Invalid address. |
| [36100042](../errorcode-nearlink-service.md#36100042-empty-array) | Empty array. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
