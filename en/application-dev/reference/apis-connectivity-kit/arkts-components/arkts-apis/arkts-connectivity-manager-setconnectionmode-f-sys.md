# setConnectionMode (System API)

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## setConnectionMode

```TypeScript
function setConnectionMode(mode: ConnectionMode, duration: number): Promise<void>
```

Sets the connection mode. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**Model restriction:** This API can be used only in the stage model.

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
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100040](../errorcode-nearlink-service.md#36100040-integer-out-of-range) | Integer out of range. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
