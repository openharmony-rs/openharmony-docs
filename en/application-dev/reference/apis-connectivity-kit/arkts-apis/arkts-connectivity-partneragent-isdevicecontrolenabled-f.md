# isDeviceControlEnabled

## Modules to Import

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## isDeviceControlEnabled

```TypeScript
function isDeviceControlEnabled(deviceAddress: PartnerDeviceAddress): boolean
```

Checks whether device control is enabled.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | Yes | The address of partner device. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether the device control is enabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal error. |
