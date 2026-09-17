# getBoundDevices

## Modules to Import

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## getBoundDevices

```TypeScript
function getBoundDevices(): PartnerDeviceAddress[]
```

Gets the list of addresses of the bound partner device for this application.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Return value:**

| Type | Description |
| --- | --- |
| [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md)[] | Returns the list of addresses of partner device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal error. |
