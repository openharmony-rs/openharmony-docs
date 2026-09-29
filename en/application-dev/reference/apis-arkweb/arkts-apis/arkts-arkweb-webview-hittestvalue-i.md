# HitTestValue

```TypeScript
interface HitTestValue
```

Provides the element information of the area being clicked. For the sample code, see [getLastHitTest](arkts-arkweb-webview-webviewcontroller-c.md#getlasthittest).

**Since:** 9

<!--Device-webview-interface HitTestValue--><!--Device-webview-interface HitTestValue-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## extra

```TypeScript
extra: string
```

Extra information of the area being clicked. If the area being clicked is an image or a link, the extra information is the URL of the image or link.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HitTestValue-extra: string--><!--Device-HitTestValue-extra: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## type

```TypeScript
type: WebHitTestType
```

Element type of the area being clicked.

**Type:** [WebHitTestType](arkts-arkweb-webview-webhittesttype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HitTestValue-type: WebHitTestType--><!--Device-HitTestValue-type: WebHitTestType-End-->

**System capability:** SystemCapability.Web.Webview.Core
