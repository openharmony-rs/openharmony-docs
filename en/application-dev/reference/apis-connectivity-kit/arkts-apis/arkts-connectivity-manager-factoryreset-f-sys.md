# factoryReset (System API)

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## factoryReset

```TypeScript
function factoryReset(): Promise<void>
```

Restores a device to its factory settings. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-manager-function factoryReset(): Promise<void>--><!--Device-manager-function factoryReset(): Promise<void>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
