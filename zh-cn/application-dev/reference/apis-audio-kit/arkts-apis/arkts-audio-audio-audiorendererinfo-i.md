# AudioRendererInfo

音频渲染器信息。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-audio-interface AudioRendererInfo--><!--Device-audio-interface AudioRendererInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## content

```TypeScript
content?: ContentType
```

音频内容类型。 API version 8、9为必填参数，从API version 10开始为可选参数，默认值为CONTENT\_TYPE\_UNKNOWN。 从API version 8开始支持，从API version 10开始废弃，建议使用usage替代。

**类型：** ContentType

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 10

**替代接口：** ohos.multimedia.audio.AudioRendererInfo#usage

<!--Device-AudioRendererInfo-content?: ContentType--><!--Device-AudioRendererInfo-content?: ContentType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## rendererFlags

```TypeScript
rendererFlags: int
```

播放流行为标志。 设置为0即可。

**类型：** int

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioRendererInfo-rendererFlags: int--><!--Device-AudioRendererInfo-rendererFlags: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## usage

```TypeScript
usage: StreamUsage
```

音频流使用类型。

**类型：** StreamUsage

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioRendererInfo-usage: StreamUsage--><!--Device-AudioRendererInfo-usage: StreamUsage-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## volumeMode

```TypeScript
volumeMode?: AudioVolumeMode
```

音频的音量模式。默认值为SYSTEM\_GLOBAL。

**类型：** AudioVolumeMode

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-AudioRendererInfo-volumeMode?: AudioVolumeMode--><!--Device-AudioRendererInfo-volumeMode?: AudioVolumeMode-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

