# AudioRendererInfo

音频渲染器信息。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Core

## content

```TypeScript
content?: ContentType
```

音频内容类型。

API version 8、9为必填参数，从API version 10开始为可选参数，默认值为CONTENT_TYPE_UNKNOWN。

从API version 8开始支持，从API version 10开始废弃，建议使用usage替代。

**类型：** ContentType

**起始版本：** 8

**废弃版本：** 10

**替代接口：** usage

**系统能力：** SystemCapability.Multimedia.Audio.Core

## rendererFlags

```TypeScript
rendererFlags: number
```

播放流行为标志。

设置为0即可。

**类型：** number

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## usage

```TypeScript
usage: StreamUsage
```

音频流使用类型。

**类型：** StreamUsage

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## volumeMode

```TypeScript
volumeMode?: AudioVolumeMode
```

音频的音量模式。默认值为SYSTEM_GLOBAL。

**类型：** AudioVolumeMode

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Audio.Volume

