# AudioDeviceDescriptor

描述音频设备。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Audio.Device

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## dmDeviceInfo

```TypeScript
readonly dmDeviceInfo?: string
```

分布式设备扩展信息，包括设备是否支持立体声、设备序列号等。

此接口仅可在Stage模型下使用。

SystemCapability.Multimedia.Audio.Core

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## dmDeviceType

```TypeScript
readonly dmDeviceType?: number
```

设备的子类型ID。

SystemCapability.Multimedia.Audio.Core

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## highQualityRecordingSupported

```TypeScript
readonly highQualityRecordingSupported?: boolean
```

是否支持高品质录音。true表示支持，false表示不支持。

SystemCapability.Multimedia.Audio.Core

**类型：** boolean

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## interruptGroupId

```TypeScript
readonly interruptGroupId: number
```

设备所处的焦点组ID。

SystemCapability.Multimedia.Audio.Device

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
readonly networkId: string
```

设备组网的ID。

SystemCapability.Multimedia.Audio.Device

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。

## volumeGroupId

```TypeScript
readonly volumeGroupId: number
```

设备所处的音量组ID。

SystemCapability.Multimedia.Audio.Device

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。
