# DeviceStatus（系统接口）

设备状态信息。用于描述伴随设备的当前状态，包括设备业务标识、用户名、型号信息、设备名、在线状态以及支持的业务ID列表等。

**起始版本：** 23

<!--Device-companionDeviceAuth-interface DeviceStatus--><!--Device-companionDeviceAuth-interface DeviceStatus-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## deviceKey

```TypeScript
deviceKey: DeviceKey
```

设备关键信息。包含设备ID类型、设备ID和设备用户ID，作为设备的唯一标识。

**类型：** DeviceKey

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceStatus-deviceKey: DeviceKey--><!--Device-DeviceStatus-deviceKey: DeviceKey-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## deviceModelInfo

```TypeScript
deviceModelInfo: string
```

设备模型信息。设备的型号标识，如产品型号、设备类型等信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceStatus-deviceModelInfo: string--><!--Device-DeviceStatus-deviceModelInfo: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## deviceName

```TypeScript
deviceName: string
```

设备名。设备的名称或别名，用于在设备列表中展示给用户。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceStatus-deviceName: string--><!--Device-DeviceStatus-deviceName: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## deviceUserName

```TypeScript
deviceUserName: string
```

设备用户名。设备上当前用户的显示名称，用于在设备选择界面展示。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceStatus-deviceUserName: string--><!--Device-DeviceStatus-deviceUserName: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## isOnline

```TypeScript
isOnline: boolean
```

设备在线状态。true表示设备处于在线状态，可以与主设备通信；false表示设备处于离线状态，无法进行认证交互。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceStatus-isOnline: boolean--><!--Device-DeviceStatus-isOnline: boolean-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## supportedBusinessIds

```TypeScript
supportedBusinessIds: number[]
```

设备支持的业务ID列表。表示该设备支持的业务场景范围，如解锁锁屏、解锁应用锁等。不同设备因认证安全性差异，支持的业务范围不同。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceStatus-supportedBusinessIds: int[]--><!--Device-DeviceStatus-supportedBusinessIds: int[]-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

