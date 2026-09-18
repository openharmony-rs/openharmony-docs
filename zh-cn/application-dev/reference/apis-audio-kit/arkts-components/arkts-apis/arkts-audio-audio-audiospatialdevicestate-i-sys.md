# AudioSpatialDeviceState（系统接口）

空间化设备状态。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## address

```TypeScript
address: string
```

空间化设备地址。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## isHeadTrackingSupported

```TypeScript
isHeadTrackingSupported: boolean
```

空间化设备是否支持头动跟踪。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## isSpatializationSupported

```TypeScript
isSpatializationSupported: boolean
```

空间化设备是否支持空间音频渲染。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## spatialDeviceType

```TypeScript
spatialDeviceType: AudioSpatialDeviceType
```

空间化设备类型。

**类型：** [AudioSpatialDeviceType](arkts-audio-audio-audiospatialdevicetype-e-sys.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。
