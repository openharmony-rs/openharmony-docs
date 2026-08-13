# OnFirstScreenPaintCallback

```TypeScript
export type OnFirstScreenPaintCallback = (firstScreenPaint: FirstScreenPaint) => void
```

The callback reports the time required for the first screen painting of the current web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export type OnFirstScreenPaintCallback = (firstScreenPaint: FirstScreenPaint) => void--><!--Device-unnamed-export type OnFirstScreenPaintCallback = (firstScreenPaint: FirstScreenPaint) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstScreenPaint | [FirstScreenPaint](arkts-na-web-firstscreenpaint-i.md) | 是 | the first screen paint info. |

