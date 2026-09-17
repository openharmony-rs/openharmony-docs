# unbindDevice

## Modules to Import

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## unbindDevice

```TypeScript
function unbindDevice(deviceAddress: PartnerDeviceAddress): Promise<void>
```

Unbinds a partner device.

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
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900001](../errorcode-fusionConnectivity.md#34900001-device-not-registered) | The device is not bound. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal error. |
