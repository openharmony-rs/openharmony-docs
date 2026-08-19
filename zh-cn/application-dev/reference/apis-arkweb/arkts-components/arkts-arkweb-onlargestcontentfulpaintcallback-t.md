# OnLargestContentfulPaintCallback

```TypeScript
type OnLargestContentfulPaintCallback = (largestContentfulPaint: LargestContentfulPaint) => void
```

当网页绘制最大内容区域时触发的回调，用于获取最大内容绘制的性能度量信息。适用于需要监控网页加载性能、优化页面渲染速度等场景。与OnFirstMeaningfulPaintCallback关注主要内容加载完成、 OnFirstScreenPaintCallback关注首屏可见内容渲染完成相比，本回调关注最大内容元素的绘制时间，适合评估页面渲染完成度和性能瓶颈。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnLargestContentfulPaintCallback = (largestContentfulPaint: LargestContentfulPaint) => void--><!--Device-unnamed-type OnLargestContentfulPaintCallback = (largestContentfulPaint: LargestContentfulPaint) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| largestContentfulPaint | [LargestContentfulPaint](arkts-arkweb-largestcontentfulpaint-i.md) | 是 | 网页绘制页面最大内容度量的详细信息。 |

