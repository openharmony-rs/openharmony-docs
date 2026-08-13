# Video

Video组件用于播放视频文件并控制其播放状态，支持播放、暂停、进度控制、倍速播放、全屏切换等功能。 > **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > <br> > > Video组件只提供简单的视频播放功能，无法支撑复杂的视频播控场景。复杂开发场景推荐使用[AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md#AVPlayer)播控API和 > XComponent组件开发。 > <br> > > Video组件在使用expandSafeArea扩展安全区域时，组件视频显示内容区域不支持扩展。

## 权限列表 使用网络视频时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。 ###### 子组件 不支持子组件。

## Video

```TypeScript
Video(value: VideoOptions)
```

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoInterface-(value: VideoOptions): VideoAttribute--><!--Device-VideoInterface-(value: VideoOptions): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [VideoOptions](arkts-arkui-videooptions-i.md) | 是 | 视频信息。 |

## 汇总

- [FullscreenInfo](arkts-arkui-fullscreeninfo-i.md)
- [PlaybackInfo](arkts-arkui-playbackinfo-i.md)
- [PosterOptions](arkts-arkui-posteroptions-i.md)
- [PreparedInfo](arkts-arkui-preparedinfo-i.md)
- [VideoOptions](arkts-arkui-videooptions-i.md)
- [PlaybackSpeed](arkts-arkui-playbackspeed-e.md)
- [SeekMode](arkts-arkui-seekmode-e.md)
