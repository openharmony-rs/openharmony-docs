# OnAdsBlockedCallback

```TypeScript
type OnAdsBlockedCallback = (details: AdsBlockedDetails) => void
```

Defines a callback invoked when ads are blocked on the web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| details | [AdsBlockedDetails](arkts-arkweb-adsblockeddetails-i.md) | Yes | Detailed information about the blocked ads when ads are blocked. |
