# stopScan

## Modules to Import

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## stopScan

```TypeScript
function stopScan(): Promise<void>
```

Stops NearLink scanning. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-scan-function stopScan(): Promise<void>--><!--Device-scan-function stopScan(): Promise<void>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**See also:** [startScan](arkts-connectivity-scan-startscan-f.md#startscan-1) Starts NearLink scanning.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
