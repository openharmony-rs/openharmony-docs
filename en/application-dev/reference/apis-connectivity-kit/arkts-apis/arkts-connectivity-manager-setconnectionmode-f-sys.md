# setConnectionMode (System API)

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## setConnectionMode

```TypeScript
function setConnectionMode(mode: ConnectionMode, duration: number): Promise<void>
```

Sets the connection mode. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-manager-function setConnectionMode(mode: ConnectionMode, duration: int): Promise<void>--><!--Device-manager-function setConnectionMode(mode: ConnectionMode, duration: int): Promise<void>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [ConnectionMode](arkts-connectivity-manager-connectionmode-e-sys.md) | Yes | Connection mode to be set. |
| duration | number | Yes | Duration of the mode to set, in seconds. The value **0** indicates no time limit.<br>The value should be an integer. |

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
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100040](../errorcode-nearlink-service.md#36100040-integer-out-of-range) | Integer out of range. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
