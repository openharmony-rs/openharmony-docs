# AvailableDeviceStatusCallback (System API)

```TypeScript
type AvailableDeviceStatusCallback = (deviceStatusList: DeviceStatus[]) => void
```

Defines the callback triggered for receiving notifications of available device status changes. When the list of available devices changes (for example, a new device goes online or a device goes offline), the system notifies the application through this callback.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceStatusList | [DeviceStatus](arkts-userauthentication-companiondeviceauth-devicestatus-i-sys.md)[] | Yes | Device status list. It contains the status information about all devices that can be added as companion devices. The application can filter online devices based on the **isOnline** field and determine the service scope supported by the device based on the **supportedBusinessIds** field. |
