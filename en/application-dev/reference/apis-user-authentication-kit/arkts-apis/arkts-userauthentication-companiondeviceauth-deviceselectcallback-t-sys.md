# DeviceSelectCallback (System API)

```TypeScript
type DeviceSelectCallback = (selectPurpose: number) => DeviceSelectResult
```

Defines the callback triggered for the companion device selection. When the system requires the user to select a companion device (for example, when adding a template or performing authentication), this callback is triggered. The application needs to return the information about the selected device.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-companionDeviceAuth-type DeviceSelectCallback = (selectPurpose: int) => DeviceSelectResult--><!--Device-companionDeviceAuth-type DeviceSelectCallback = (selectPurpose: int) => DeviceSelectResult-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectPurpose | number | Yes | Selection purpose. Used to identify the intent of the current device selection. For the values, see [SelectPurpose](arkts-userauthentication-companiondeviceauth-selectpurpose-e-sys.md). **SELECT_ADD_DEVICE(1)** indicates selecting a device for adding a template, and **SELECT_AUTH_DEVICE(2)** indicates selecting an authentication device. Vendors can define extended values (greater than or equal to 10000). The application should return a **DeviceSelectResult** containing the corresponding device information based on **selectPurpose**. |

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceSelectResult](arkts-userauthentication-companiondeviceauth-deviceselectresult-i-sys.md) | Used to return the device information selected by the user to the system, so that the system can perform subsequent template addition or authentication operations. Contains the list of device information selected by the user (**deviceKeys**) and the optional extended context (**selectionContext**). |
