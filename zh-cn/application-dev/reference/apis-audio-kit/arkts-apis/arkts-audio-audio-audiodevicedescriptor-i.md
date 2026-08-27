# AudioDeviceDescriptor

描述音频设备。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Audio.Device

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## address

```TypeScript
readonly address: string
```

设备静态MAC地址。如果是蓝牙设备，需要申请权限ohos.permission.USE_BLUETOOTH。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## capabilities

```TypeScript
readonly capabilities?: Array<AudioStreamInfo>
```

设备支持的音频流能力。SystemCapability.Multimedia.Audio.Device

**类型：** Array&lt;[AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)&gt;

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Device

## channelCounts

```TypeScript
readonly channelCounts: Array<number>
```

支持的通道数。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## channelMasks

```TypeScript
readonly channelMasks: Array<number>
```

支持的通道掩码。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## deviceRole

```TypeScript
readonly deviceRole: DeviceRole
```

设备角色。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [DeviceRole](arkts-audio-audio-devicerole-e.md)

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## deviceType

```TypeScript
readonly deviceType: DeviceType
```

设备类型。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** DeviceType

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## displayName

```TypeScript
readonly displayName: string
```

设备显示名。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## encodingTypes

```TypeScript
readonly encodingTypes?: Array<AudioEncodingType>
```

支持的编码类型。SystemCapability.Multimedia.Audio.Core从API version 12开始，该接口支持在原子化服务中使用。

**类型：** Array&lt;[AudioEncodingType](arkts-audio-audio-audioencodingtype-e.md)&gt;

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## id

```TypeScript
readonly id: number
```

唯一的设备id。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## model

```TypeScript
readonly model?: string
```

设备的具体型号类别。SystemCapability.Multimedia.Audio.Device

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Device

## name

```TypeScript
readonly name: string
```

设备名称。如果是蓝牙设备，需要申请权限ohos.permission.USE_BLUETOOTH。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## sampleRates

```TypeScript
readonly sampleRates: Array<number>
```

支持的采样率。SystemCapability.Multimedia.Audio.Device从API version 12开始，该接口支持在原子化服务中使用。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## spatializationSupported

```TypeScript
readonly spatializationSupported?: boolean
```

设备是否支持空间音频。true表示支持空间音频，false表示不支持空间音频。SystemCapability.Multimedia.Audio.Spatialization

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization
