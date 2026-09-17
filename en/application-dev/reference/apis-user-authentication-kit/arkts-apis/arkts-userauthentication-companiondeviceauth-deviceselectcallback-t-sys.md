# DeviceSelectCallback (System API)

```TypeScript
type DeviceSelectCallback = (selectPurpose: number) => DeviceSelectResult
```

Defines the callback triggered for the companion device selection. When the system requires the user to select a companion device (for example, when adding a template or performing authentication), this callback is triggered. The application needs to return the information about the selected device.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectPurpose | number | Yes | Selection purpose. It identifies the purpose of the current device selection. For details about the value, see [SelectPurpose](arkts-userauthentication-companiondeviceauth-selectpurpose-e-sys.md). **SELECT_ADD_DEVICE(1)** means to select the device for adding a template, and **SELECT_AUTH_DEVICE(2)** means to select the device for authentication. Vendors can customize the extended value (greater than or equal to 10000). The application should return the corresponding device list based on the selection purpose. |

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceSelectResult](arkts-userauthentication-companiondeviceauth-deviceselectresult-i-sys.md) | Device selection result. It contains the device information list (**deviceKeys**) selected by the user and the optional extended context (**selectionContext**). |
