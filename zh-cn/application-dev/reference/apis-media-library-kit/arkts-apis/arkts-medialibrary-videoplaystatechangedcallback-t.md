# videoPlayStateChangedCallback

```TypeScript
export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void
```

大图页视频播放状态改变时的回调事件。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void--><!--Device-unnamed-export type videoPlayStateChangedCallback = (state: VideoPlayerState) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [VideoPlayerState](arkts-medialibrary-file-photopickercomponent-videoplayerstate-e.md) | 是 | 视频播放状态。 |
