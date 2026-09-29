# AdsBlockedDetails

```TypeScript
declare interface AdsBlockedDetails
```

Provides detailed information about the blocked ads when ads are blocked.

**Since:** 12

<!--Device-unnamed-declare interface AdsBlockedDetails--><!--Device-unnamed-declare interface AdsBlockedDetails-End-->

**System capability:** SystemCapability.Web.Webview.Core

## adsBlocked

```TypeScript
adsBlocked: Array<string>
```

URLs or dompaths of the blocked ads. If multiple ads have the same URLs, duplicate elements may exist.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AdsBlockedDetails-adsBlocked: Array<string>--><!--Device-AdsBlockedDetails-adsBlocked: Array<string>-End-->

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL of the page where ads are blocked.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AdsBlockedDetails-url: string--><!--Device-AdsBlockedDetails-url: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
