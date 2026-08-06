# VideoSizeEvent

```TypeScript
type VideoSizeEvent = (width: int, height: int) => void
```

The video size event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-avSession-type VideoSizeEvent = (width: int, height: int) => void--><!--Device-avSession-type VideoSizeEvent = (width: int, height: int) => void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | int | 是 | 视频宽度。 取值范围为全体整数 取值限定为整数。  |
| height | int | 是 | video width 取值范围为全体整数 取值限定为整数。  |

