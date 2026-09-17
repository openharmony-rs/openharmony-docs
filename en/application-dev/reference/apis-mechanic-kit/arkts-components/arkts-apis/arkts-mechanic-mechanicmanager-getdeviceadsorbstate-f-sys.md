# getDeviceAdsorbState (System API)

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## getDeviceAdsorbState

```TypeScript
function getDeviceAdsorbState(mechId: number): AdsorbState
```

Obtains the adsorb state of a device. Before calling this method, ensure that the device is connected.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mechId | number | Yes | ID of the mechanical device. |

**Return value:**

| Type | Description |
| --- | --- |
| [AdsorbState](arkts-mechanic-mechanicmanager-adsorbstate-e-sys.md) | Returns the current device adsorb state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-device-not-connected) | Device not connected. |
