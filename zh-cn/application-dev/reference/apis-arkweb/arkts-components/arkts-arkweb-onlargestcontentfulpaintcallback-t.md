# OnLargestContentfulPaintCallback

```TypeScript
type OnLargestContentfulPaintCallback = (largestContentfulPaint: LargestContentfulPaint) => void
```

网页绘制页面最大内容度量信息的回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| largestContentfulPaint | LargestContentfulPaint | 是 | 网页绘制页面最大内容度量的详细信息。 |

