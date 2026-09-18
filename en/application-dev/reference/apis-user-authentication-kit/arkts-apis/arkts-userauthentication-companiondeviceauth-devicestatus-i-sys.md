# DeviceStatus (System API)

Defines the device status information. It describes the current status of the companion device, including the device service ID, user name, model information, device name, online status, list of supported service IDs, and device sub-profile name.

**Since:** 23

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

Key device information. It uniquely identifies a device, including the device ID type, device ID, and device user ID, and device sub-profile ID.

**Type:** [DeviceKey](arkts-userauthentication-companiondeviceauth-devicekey-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

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

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceSubProfileName

```TypeScript
deviceSubProfileName?: string
```

Device sub-profile name. It corresponds to the nickname of the distributed account, serving as the display name of the foreground sub-profile on the device, and is displayed on the device selection screen. Default value: The default value is "".

**Type:** string

**Default:** ""

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

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

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## supportedBusinessIds

```TypeScript
supportedBusinessIds: number[]
```

List of service IDs supported by the device. It indicates the service scenarios supported by the device, such as unlocking the screen lock and unlocking the application lock. The service scenarios supported by a device vary depending on the authentication security.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
