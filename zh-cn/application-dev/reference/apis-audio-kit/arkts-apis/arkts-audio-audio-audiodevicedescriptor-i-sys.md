# AudioDeviceDescriptor

描述音频设备。

**起始版本：** 23

<!--Device-audio-interface AudioDeviceDescriptor--><!--Device-audio-interface AudioDeviceDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
import { audioHaptic } from '@kit.AudioKit';
```

## dmDeviceInfo

```TypeScript
readonly dmDeviceInfo?: string
```

Extended information for distributed device, including whether the device supports stereo, Device SN, etc.

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioDeviceDescriptor-readonly dmDeviceInfo?: string--><!--Device-AudioDeviceDescriptor-readonly dmDeviceInfo?: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## dmDeviceType

```TypeScript
readonly dmDeviceType?: int
```

Only [SPEAKER](arkts-audio-audio-devicetype-e.md#speaker) with networkId, [REMOTE_CAST](arkts-audio-audio-devicetype-e.md#remote_cast) or [REMOTE_DAUDIO](arkts-audio-audio-devicetype-e.md#remote_daudio) has dmDeviceType which indicated deviceTypeId.

**类型：** int

**起始版本：** 23

<!--Device-AudioDeviceDescriptor-readonly dmDeviceType?: int--><!--Device-AudioDeviceDescriptor-readonly dmDeviceType?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## highQualityRecordingSupported

```TypeScript
readonly highQualityRecordingSupported?: boolean
```

Whether device supports high quality recording.

**类型：** boolean

**起始版本：** 24

<!--Device-AudioDeviceDescriptor-readonly highQualityRecordingSupported?: boolean--><!--Device-AudioDeviceDescriptor-readonly highQualityRecordingSupported?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## interruptGroupId

```TypeScript
readonly interruptGroupId: int
```

Interrupt group id

**类型：** int

**起始版本：** 23

<!--Device-AudioDeviceDescriptor-readonly interruptGroupId: int--><!--Device-AudioDeviceDescriptor-readonly interruptGroupId: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
readonly networkId: string
```

**类型：** string

**起始版本：** 23

<!--Device-AudioDeviceDescriptor-readonly networkId: string--><!--Device-AudioDeviceDescriptor-readonly networkId: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。

## volumeGroupId

```TypeScript
readonly volumeGroupId: int
```

Volume group id

**类型：** int

**起始版本：** 23

<!--Device-AudioDeviceDescriptor-readonly volumeGroupId: int--><!--Device-AudioDeviceDescriptor-readonly volumeGroupId: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。

