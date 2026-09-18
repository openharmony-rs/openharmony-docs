# setCarKeyDfxData (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## setCarKeyDfxData

```TypeScript
function setCarKeyDfxData(deviceId: string, action: CarKeyActionType): void
```

Set the dfx data of car key.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |
| action | [CarKeyActionType](arkts-connectivity-connection-carkeyactiontype-e-sys.md) | Yes | Indicates the action to set the data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |
