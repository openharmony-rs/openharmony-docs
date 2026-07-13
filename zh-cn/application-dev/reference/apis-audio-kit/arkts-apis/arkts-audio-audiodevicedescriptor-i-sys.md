# AudioDeviceDescriptor

描述音频设备。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Audio.Device

## dmDeviceInfo

```TypeScript
readonly dmDeviceInfo?: string
```

Extended information for distributed device, including whether the device supports
stereo, Device SN, etc.

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## dmDeviceType

```TypeScript
readonly dmDeviceType?: number
```

Only {@link DeviceType.SPEAKER} with networkId, {@link DeviceType.REMOTE_CAST}
or {@link DeviceType.REMOTE_DAUDIO} has dmDeviceType which indicated deviceTypeId.

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## highQualityRecordingSupported

```TypeScript
readonly highQualityRecordingSupported?: boolean
```

Whether device supports high quality recording.

**类型：** boolean

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## interruptGroupId

```TypeScript
readonly interruptGroupId: number
```

Interrupt group id

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
readonly networkId: string
```

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。

## volumeGroupId

```TypeScript
readonly volumeGroupId: number
```

Volume group id

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

**系统接口：** 此接口为系统接口。

