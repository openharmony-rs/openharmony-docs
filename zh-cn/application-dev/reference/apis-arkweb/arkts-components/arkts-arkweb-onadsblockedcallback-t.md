# OnAdsBlockedCallback

```TypeScript
type OnAdsBlockedCallback = (details: AdsBlockedDetails) => void
```

当页面发生广告过滤时触发此回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnAdsBlockedCallback = (details: AdsBlockedDetails) => void--><!--Device-unnamed-type OnAdsBlockedCallback = (details: AdsBlockedDetails) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| details | [AdsBlockedDetails](arkts-arkweb-adsblockeddetails-i.md) | 是 | 发生广告拦截时，广告资源信息。 |

