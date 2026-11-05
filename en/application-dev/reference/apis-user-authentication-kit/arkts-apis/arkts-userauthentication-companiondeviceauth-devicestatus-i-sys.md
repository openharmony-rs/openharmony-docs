# DeviceStatus (System API)

```TypeScript
interface DeviceStatus
```

Defines the device status information. It is used to describe the current status of a companion device, including the device service identifier, user name, model information, device name, online status, list of supported business IDs, and device sub-identity credential name.

**Since:** 23

<!--Device-companionDeviceAuth-interface DeviceStatus--><!--Device-companionDeviceAuth-interface DeviceStatus-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## deviceKey

```TypeScript
deviceKey: DeviceKey
```

Key information about the device. It contains the device ID type, device ID, device user ID, and device sub- identity credential ID, serving as the unique identifier of the device.

**Type:** [DeviceKey](arkts-userauthentication-companiondeviceauth-devicekey-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceStatus-deviceKey: DeviceKey--><!--Device-DeviceStatus-deviceKey: DeviceKey-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceModelInfo

```TypeScript
deviceModelInfo: string
```

Device model information. It identifies the device model, such as the product model and device type.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceStatus-deviceModelInfo: string--><!--Device-DeviceStatus-deviceModelInfo: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceName

```TypeScript
deviceName: string
```

Device name. It is the name or alias of a device, and is displayed to the user in the device list.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceStatus-deviceName: string--><!--Device-DeviceStatus-deviceName: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceSubProfileName

```TypeScript
deviceSubProfileName?: string
```

Name of the device sub-identity credentials. It corresponds to the nickname of the distributed account, serving as the display name of the foreground sub-identity credentials on the device and used for display on the device selection screen.

**Type:** string

**Default:** ""

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceStatus-deviceSubProfileName?: string--><!--Device-DeviceStatus-deviceSubProfileName?: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceUserName

```TypeScript
deviceUserName: string
```

Device user name. It is the display name of the current user on the device, and is displayed on the device selection screen.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceStatus-deviceUserName: string--><!--Device-DeviceStatus-deviceUserName: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## isOnline

```TypeScript
isOnline: boolean
```

Device online status. The value **true** indicates that the device is online and can communicate with the primary device. The value **false** indicates that the device is offline and cannot perform authentication interaction.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceStatus-isOnline: boolean--><!--Device-DeviceStatus-isOnline: boolean-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## supportedBusinessIds

```TypeScript
supportedBusinessIds: number[]
```

List of business IDs supported by the device. It indicates the business scenarios supported by the device, such as unlocking the screen lock and unlocking the application lock. The business scenarios supported by a device vary depending on the authentication security.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceStatus-supportedBusinessIds: int[]--><!--Device-DeviceStatus-supportedBusinessIds: int[]-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
