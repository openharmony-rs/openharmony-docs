# DeviceKey (System API)

Defines the device service ID. It uniquely identifies a device and its user, including the device ID type, device ID, user ID, and sub-profile ID.

**Since:** 23

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## deviceId

```TypeScript
deviceId: string
```

Device ID. It is a string that uniquely identifies a device. The format is determined by the value of **deviceIdType**.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceIdType

```TypeScript
deviceIdType: number
```

Enumerates device ID types. They are used to specify the type of the device service ID and can be extended based on [DeviceIdType](arkts-userauthentication-companiondeviceauth-deviceidtype-e-sys.md). For example, you can use **UNIFIED_DEVICE_ID(1)** to indicate the unified device ID or use the vendor-defined value (≥ 10000).

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceSubProfileId

```TypeScript
deviceSubProfileId?: number
```

Device sub-profile ID. It is an integer greater than or equal to 0 and is used to distinguish different sub-profile under the same user on the same device. The value should be an integer. Default value: The default value is -1.

**Type:** number

**Default:** -1

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceUserId

```TypeScript
deviceUserId: number
```

Device user ID. It is an integer greater than or equal to 0 and is used to distinguish different users on the device.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
