# isSupportAction (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## isSupportAction

```TypeScript
function isSupportAction(mechId: number, actionType: ActionType): boolean
```

Check whether the specific action type is supported.

**Since:** 26.0.0

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mechId | number | Yes | ID of the mechanical device.<br>The value should be an integer. |
| actionType | [ActionType](arkts-mechanic-mechanicmanager-actiontype-e-sys.md) | Yes | Type of action sequence. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Indicates whether the action type is supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |
