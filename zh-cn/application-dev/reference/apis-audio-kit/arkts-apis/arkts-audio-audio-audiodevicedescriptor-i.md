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

## address

```TypeScript
readonly address: string
```

设备静态MAC地址。 如果是蓝牙设备，需要申请权限ohos.permission.USE_BLUETOOTH。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly address: string--><!--Device-AudioDeviceDescriptor-readonly address: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## capabilities

```TypeScript
readonly capabilities?: Array<AudioStreamInfo>
```

设备支持的音频流能力。

**类型：** Array&lt;[AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)&gt;

**起始版本：** 23

<!--Device-AudioDeviceDescriptor-readonly capabilities?: Array<AudioStreamInfo>--><!--Device-AudioDeviceDescriptor-readonly capabilities?: Array<AudioStreamInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## channelCounts

```TypeScript
readonly channelCounts: Array<int>
```

支持的通道数。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly channelCounts: Array<int>--><!--Device-AudioDeviceDescriptor-readonly channelCounts: Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## channelMasks

```TypeScript
readonly channelMasks: Array<int>
```

支持的通道掩码。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly channelMasks: Array<int>--><!--Device-AudioDeviceDescriptor-readonly channelMasks: Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## deviceRole

```TypeScript
readonly deviceRole: DeviceRole
```

设备角色。

**类型：** [DeviceRole](arkts-audio-audio-devicerole-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly deviceRole: DeviceRole--><!--Device-AudioDeviceDescriptor-readonly deviceRole: DeviceRole-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## deviceType

```TypeScript
readonly deviceType: DeviceType
```

设备类型。

**类型：** DeviceType

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly deviceType: DeviceType--><!--Device-AudioDeviceDescriptor-readonly deviceType: DeviceType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## displayName

```TypeScript
readonly displayName: string
```

设备显示名。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly displayName: string--><!--Device-AudioDeviceDescriptor-readonly displayName: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## encodingTypes

```TypeScript
readonly encodingTypes?: Array<AudioEncodingType>
```

支持的编码类型。

**类型：** Array&lt;[AudioEncodingType](arkts-audio-audio-audioencodingtype-e.md)&gt;

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly encodingTypes?: Array<AudioEncodingType>--><!--Device-AudioDeviceDescriptor-readonly encodingTypes?: Array<AudioEncodingType>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## id

```TypeScript
readonly id: int
```

唯一的设备id。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly id: int--><!--Device-AudioDeviceDescriptor-readonly id: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## model

```TypeScript
readonly model?: string
```

设备的具体型号类别。

**类型：** string

**起始版本：** 23

<!--Device-AudioDeviceDescriptor-readonly model?: string--><!--Device-AudioDeviceDescriptor-readonly model?: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## name

```TypeScript
readonly name: string
```

设备名称。 如果是蓝牙设备，需要申请权限ohos.permission.USE_BLUETOOTH。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly name: string--><!--Device-AudioDeviceDescriptor-readonly name: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## sampleRates

```TypeScript
readonly sampleRates: Array<int>
```

支持的采样率。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioDeviceDescriptor-readonly sampleRates: Array<int>--><!--Device-AudioDeviceDescriptor-readonly sampleRates: Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## spatializationSupported

```TypeScript
readonly spatializationSupported?: boolean
```

设备是否支持空间音频。true表示支持空间音频，false表示不支持空间音频。

**类型：** boolean

**起始版本：** 23

<!--Device-AudioDeviceDescriptor-readonly spatializationSupported?: boolean--><!--Device-AudioDeviceDescriptor-readonly spatializationSupported?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

