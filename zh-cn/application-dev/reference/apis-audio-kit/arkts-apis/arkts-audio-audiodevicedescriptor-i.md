# AudioDeviceDescriptor

描述音频设备。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Audio.Device

## address

```TypeScript
readonly address: string
```

设备静态MAC地址。

如果是蓝牙设备，需要申请权限ohos.permission.USE_BLUETOOTH。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## capabilities

```TypeScript
readonly capabilities?: Array<AudioStreamInfo>
```

设备支持的音频流能力。

**类型：** Array<AudioStreamInfo>

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Device

## channelCounts

```TypeScript
readonly channelCounts: Array<number>
```

支持的通道数。

**类型：** Array<number>

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## channelMasks

```TypeScript
readonly channelMasks: Array<number>
```

支持的通道掩码。

**类型：** Array<number>

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## deviceRole

```TypeScript
readonly deviceRole: DeviceRole
```

设备角色。

**类型：** DeviceRole

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## deviceType

```TypeScript
readonly deviceType: DeviceType
```

设备类型。

**类型：** DeviceType

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## displayName

```TypeScript
readonly displayName: string
```

设备显示名。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## encodingTypes

```TypeScript
readonly encodingTypes?: Array<AudioEncodingType>
```

支持的编码类型。

**类型：** Array<AudioEncodingType>

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## id

```TypeScript
readonly id: number
```

唯一的设备id。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## model

```TypeScript
readonly model?: string
```

设备的具体型号类别。

**类型：** string

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Device

## name

```TypeScript
readonly name: string
```

设备名称。

如果是蓝牙设备，需要申请权限ohos.permission.USE_BLUETOOTH。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## sampleRates

```TypeScript
readonly sampleRates: Array<number>
```

支持的采样率。

**类型：** Array<number>

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## spatializationSupported

```TypeScript
readonly spatializationSupported?: boolean
```

设备是否支持空间音频。true表示支持空间音频，false表示不支持空间音频。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

