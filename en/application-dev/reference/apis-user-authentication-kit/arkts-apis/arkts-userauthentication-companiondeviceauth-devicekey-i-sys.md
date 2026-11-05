# DeviceKey (System API)

```TypeScript
interface DeviceKey
```

Defines the device identifier. It is used to uniquely identify a device and its user, and contains information such as the device ID type, device ID, device user ID, and device sub-identity credential ID.

**Since:** 23

<!--Device-companionDeviceAuth-interface DeviceKey--><!--Device-companionDeviceAuth-interface DeviceKey-End-->

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

<!--Device-DeviceKey-deviceId: string--><!--Device-DeviceKey-deviceId: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceIdType

```TypeScript
deviceIdType: number
```

Device ID type. It is used to specify the type of the device business ID and can be extended based on [DeviceIdType](arkts-userauthentication-companiondeviceauth-deviceidtype-e-sys.md). For example, you can use **UNIFIED_DEVICE_ID(1)** to indicate the unified device ID or use the vendor-defined value (≥ 10000).

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceKey-deviceIdType: int--><!--Device-DeviceKey-deviceIdType: int-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceSubProfileId

```TypeScript
deviceSubProfileId?: number
```

Device sub-identity credential ID. A non-negative integer that identifies a sub-identity credential on the device and distinguishes different sub-identity credentials under the same user on the same device.

**Type:** number

**Default:** -1

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceKey-deviceSubProfileId?: int--><!--Device-DeviceKey-deviceSubProfileId?: int-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceUserId

```TypeScript
deviceUserId: number
```

Device user ID. A non-negative integer that identifies a user on the device and distinguishes different users on the device.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceKey-deviceUserId: int--><!--Device-DeviceKey-deviceUserId: int-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
