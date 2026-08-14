# OnVideoSizeChangeHandler

```TypeScript
type OnVideoSizeChangeHandler = (width: int, height: int) => void
```

视频播放宽高变化事件回调方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-media-type OnVideoSizeChangeHandler = (width: int, height: int) => void--><!--Device-media-type OnVideoSizeChangeHandler = (width: int, height: int) => void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | int | 是 | 视频宽度，单位为像素（px）。 |
| height | int | 是 | 视频高度，单位为像素（px）。 |

