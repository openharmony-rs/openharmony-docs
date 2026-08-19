# DeviceInfo（系统接口）

表示设备信息。

**起始版本：** 26.0.0

<!--Device-userStatus-export interface DeviceInfo--><!--Device-userStatus-export interface DeviceInfo-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示设备ID。设备唯一标识符，用于标识和区分不同设备，字符串长度范围[0,64]。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceInfo-deviceId: string--><!--Device-DeviceInfo-deviceId: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## deviceName

```TypeScript
deviceName: string
```

表示设备名称。用户可自定义的设备显示名称，用于在界面中展示设备信息，字符串长度范围[0,64]。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceInfo-deviceName: string--><!--Device-DeviceInfo-deviceName: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## deviceType

```TypeScript
deviceType: DeviceType
```

表示设备类型。

**类型：** DeviceType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceInfo-deviceType: DeviceType--><!--Device-DeviceInfo-deviceType: DeviceType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
networkId: string
```

表示设备网络ID。用于设备组网和跨设备通信的唯一网络标识，字符串长度范围[0,64]。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceInfo-networkId: string--><!--Device-DeviceInfo-networkId: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

