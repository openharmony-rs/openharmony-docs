# OnDetectBlankScreenCallback

```TypeScript
type OnDetectBlankScreenCallback = (event: BlankScreenDetectionEventInfo) => void
```

检测到白屏时触发此回调。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

<!--Device-unnamed-type OnDetectBlankScreenCallback = (event: BlankScreenDetectionEventInfo) => void--><!--Device-unnamed-type OnDetectBlankScreenCallback = (event: BlankScreenDetectionEventInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [BlankScreenDetectionEventInfo](arkts-arkweb-blankscreendetectioneventinfo-i.md) | 是 | 检测到白屏时的详细信息。 |

