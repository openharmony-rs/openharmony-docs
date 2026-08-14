# OnBufferingUpdateHandler

```TypeScript
type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: int) => void
```

播放缓存事件回调方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-media-type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: int) => void--><!--Device-media-type OnBufferingUpdateHandler = (infoType: BufferingInfoType, value: int) => void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| infoType | [BufferingInfoType](arkts-media-multimedia-media-bufferinginfotype-e.md) | 是 | 缓存时间类型。 |
| value | int | 是 | 缓存时间类型的值。 |

