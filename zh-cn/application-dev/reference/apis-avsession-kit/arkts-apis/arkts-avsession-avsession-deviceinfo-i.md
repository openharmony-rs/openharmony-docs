# DeviceInfo

播放设备的相关信息。

**起始版本：** 10

<!--Device-avSession-interface DeviceInfo--><!--Device-avSession-interface DeviceInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## audioCapabilities

```TypeScript
audioCapabilities?: AudioCapabilities
```

播放设备支持的音频能力。

**类型：** AudioCapabilities

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-audioCapabilities?: AudioCapabilities--><!--Device-DeviceInfo-audioCapabilities?: AudioCapabilities-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## castCategory

```TypeScript
castCategory: AVCastCategory
```

投播的类别。

**类型：** AVCastCategory

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-castCategory: AVCastCategory--><!--Device-DeviceInfo-castCategory: AVCastCategory-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## deviceId

```TypeScript
deviceId: string
```

播放设备的ID。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-deviceId: string--><!--Device-DeviceInfo-deviceId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## deviceName

```TypeScript
deviceName: string
```

播放设备的名称。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-deviceName: string--><!--Device-DeviceInfo-deviceName: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## deviceType

```TypeScript
deviceType: DeviceType
```

播放设备的类型。

**类型：** DeviceType

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-deviceType: DeviceType--><!--Device-DeviceInfo-deviceType: DeviceType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## manufacturer

```TypeScript
manufacturer?: string
```

播放设备生产厂家。

**类型：** string

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-manufacturer?: string--><!--Device-DeviceInfo-manufacturer?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## modelName

```TypeScript
modelName?: string
```

播放设备型号名称。

**类型：** string

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-modelName?: string--><!--Device-DeviceInfo-modelName?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## supportedDrmCapabilities

```TypeScript
supportedDrmCapabilities?: Array<string>
```

播放设备支持的DRM能力。

**类型：** Array<string>

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-supportedDrmCapabilities?: Array<string>--><!--Device-DeviceInfo-supportedDrmCapabilities?: Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## supportedProtocols

```TypeScript
supportedProtocols?: number
```

播放设备支持的协议。

默认为TYPE_LOCAL,具体取值来自[ProtocolType](arkts-avsession-avsession-protocoltype-e.md)，可以是ProtocolType中的某个协议或者多个协议的组合。

设备仅支持一种协议，返回对应枚举值；设备支持多种协议，返回对应枚举值之和。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-supportedProtocols?: int--><!--Device-DeviceInfo-supportedProtocols?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## supportedPullClients

```TypeScript
supportedPullClients?: Array<number>
```

支持拉端客户端的ID集合（只有支持4K投播的设备会返回此字段）。

**类型：** Array<number>

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DeviceInfo-supportedPullClients?: Array<int>--><!--Device-DeviceInfo-supportedPullClients?: Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

