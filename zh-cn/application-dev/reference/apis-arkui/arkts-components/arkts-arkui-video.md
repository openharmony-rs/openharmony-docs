# Video

用于播放视频文件并控制其播放状态的组件。 

> **说明：**

<br/>
>  Video组件只提供简单的视频播放功能，无法支撑复杂的视频播控场景。复杂开发场景推荐使用[AVPlayer]{@link @ohos.multimedia.media:media.AVPlayer}播控API和[XComponent]{@link xcomponent}组件开发。<br/>
>  Video组件在使用expandSafeArea扩展安全区域时，组件视频显示内容区域不支持扩展。


## Video

```TypeScript
Video(value: VideoOptions)
```

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | VideoOptions | 是 | 视频信息。 |

## 汇总

- [FullscreenInfo](arkts-arkui-video-fullscreeninfo-i.md)
- [PlaybackInfo](arkts-arkui-video-playbackinfo-i.md)
- [PosterOptions](arkts-arkui-video-posteroptions-i.md)
- [PreparedInfo](arkts-arkui-video-preparedinfo-i.md)
- [VideoOptions](arkts-arkui-video-videooptions-i.md)
- [PlaybackSpeed](arkts-arkui-video-playbackspeed-e.md)
- [SeekMode](arkts-arkui-video-seekmode-e.md)
