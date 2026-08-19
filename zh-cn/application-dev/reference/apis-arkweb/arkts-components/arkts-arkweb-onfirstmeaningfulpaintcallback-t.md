# OnFirstMeaningfulPaintCallback

```TypeScript
type OnFirstMeaningfulPaintCallback = (firstMeaningfulPaint: FirstMeaningfulPaint) => void
```

网页首次绘制页面主要内容度量的回调，当网页加载完页面主要内容时会触发此回调。与OnLargestContentfulPaintCallback关注最大内容元素绘制时间、OnFirstScreenPaintCallback关注首屏可见内 容渲染完成相比，本回调更关注主要内容是否加载完成，适合评估用户可见内容的加载体验。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnFirstMeaningfulPaintCallback = (firstMeaningfulPaint: FirstMeaningfulPaint) => void--><!--Device-unnamed-type OnFirstMeaningfulPaintCallback = (firstMeaningfulPaint: FirstMeaningfulPaint) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstMeaningfulPaint | [FirstMeaningfulPaint](arkts-arkweb-firstmeaningfulpaint-i.md) | 是 | 绘制页面主要内容度量的详细信息。 |

