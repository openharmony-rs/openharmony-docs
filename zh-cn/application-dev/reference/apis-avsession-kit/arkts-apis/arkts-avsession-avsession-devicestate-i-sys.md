# DeviceState（系统接口）

投播设备的连接状态。

**起始版本：** 20

<!--Device-avSession-interface DeviceState--><!--Device-avSession-interface DeviceState-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## deviceId

```TypeScript
readonly deviceId: string
```

投播设备ID。

**类型：** string

**起始版本：** 20

<!--Device-DeviceState-readonly deviceId: string--><!--Device-DeviceState-readonly deviceId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## deviceState

```TypeScript
readonly deviceState: number
```

投播设备连接状态码。

**类型：** number

**起始版本：** 20

<!--Device-DeviceState-readonly deviceState: int--><!--Device-DeviceState-readonly deviceState: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## radarErrorCode

```TypeScript
readonly radarErrorCode: number
```

系统雷达错误码。

**类型：** number

**起始版本：** 20

<!--Device-DeviceState-readonly radarErrorCode: int--><!--Device-DeviceState-readonly radarErrorCode: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## reasonCode

```TypeScript
readonly reasonCode: number
```

投播设备连接错误码。

**类型：** number

**起始版本：** 20

<!--Device-DeviceState-readonly reasonCode: int--><!--Device-DeviceState-readonly reasonCode: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

