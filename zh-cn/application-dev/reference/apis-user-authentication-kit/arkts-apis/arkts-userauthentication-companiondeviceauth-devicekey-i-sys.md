# DeviceKey（系统接口）

设备业务标识。用于唯一标识一个设备及其用户，包含设备ID类型、设备ID和设备用户ID等信息。

**起始版本：** 23

<!--Device-companionDeviceAuth-interface DeviceKey--><!--Device-companionDeviceAuth-interface DeviceKey-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## deviceId

```TypeScript
deviceId: string
```

设备ID。设备的唯一标识字符串，具体格式由deviceIdType决定。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKey-deviceId: string--><!--Device-DeviceKey-deviceId: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## deviceIdType

```TypeScript
deviceIdType: number
```

设备ID类型。用于指定设备业务标识的类型，可在[DeviceIdType](arkts-userauthentication-companiondeviceauth-deviceidtype-e-sys.md)基础上自定义扩展，如使用UNIFIED_DEVICE_ID(1)表示统一设备ID，或使用厂商自定义值（≥10000）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKey-deviceIdType: int--><!--Device-DeviceKey-deviceIdType: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## deviceUserId

```TypeScript
deviceUserId: number
```

设备用户ID。设备上的用户标识，为大于等于0的正整数，用于区分设备上的不同用户。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKey-deviceUserId: int--><!--Device-DeviceKey-deviceUserId: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

