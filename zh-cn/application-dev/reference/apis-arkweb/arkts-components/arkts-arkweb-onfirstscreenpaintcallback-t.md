# OnFirstScreenPaintCallback

```TypeScript
type OnFirstScreenPaintCallback = (firstScreenPaint: FirstScreenPaint) => void
```

检测到首屏渲染结束时会触发此回调。与OnFirstMeaningfulPaintCallback关注主要内容加载完成、OnLargestContentfulPaintCallback关注最大内容元素绘制时间相比，本回调更关注首屏可见内 容的渲染完成时间，适合评估用户首次视觉体验。

**起始版本：** 23

<!--Device-unnamed-type OnFirstScreenPaintCallback = (firstScreenPaint: FirstScreenPaint) => void--><!--Device-unnamed-type OnFirstScreenPaintCallback = (firstScreenPaint: FirstScreenPaint) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstScreenPaint | [FirstScreenPaint](arkts-arkweb-firstscreenpaint-i.md) | 是 | 检测到首屏渲染时的详细信息。 |

