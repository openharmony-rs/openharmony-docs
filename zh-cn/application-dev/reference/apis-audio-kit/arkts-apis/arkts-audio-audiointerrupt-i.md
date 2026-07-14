# AudioInterrupt

音频监听事件传入的参数。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，无替代接口。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** AudioRendererOptions

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## contentType

```TypeScript
contentType: ContentType
```

音频打断媒体类型。

**类型：** ContentType

**起始版本：** 7

**废弃版本：** 9

**替代接口：** rendererInfo

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## pauseWhenDucked

```TypeScript
pauseWhenDucked: boolean
```

音频打断时是否可以暂停音频播放。true表示音频播放可以在音频打断期间暂停，false表示音频播放不可以在音频打断期间暂停。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hintType

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## streamUsage

```TypeScript
streamUsage: StreamUsage
```

音频流使用类型。

**类型：** StreamUsage

**起始版本：** 7

**废弃版本：** 9

**替代接口：** rendererInfo

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

