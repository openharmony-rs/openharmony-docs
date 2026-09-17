# ScrollOffset

Represents the current scrolling offset of a web page.

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## x

```TypeScript
x: number
```

Horizontal scroll offset of the web page. The value is the difference between the x-coordinate of the left edge of the web page and the x-coordinate of the left edge of the Web component.

When the web page is over-scrolled to the right, the value is negative.

When the web page is not over-scrolled or is over-scrolled to the left, the value is 0 or positive.

Unit: vp.

**Type:** number

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Web.Webview.Core

## y

```TypeScript
y: number
```

Vertical scroll offset of the web page. The value is the difference between the y-coordinate of the top edge of the web page and the y-coordinate of the top edge of the Web component.

When the web page is over-scrolled downward, the value is negative.

When the web page is not over-scrolled or is over-scrolled upward, the value is 0 or positive.

Unit: vp.

**Type:** number

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Web.Webview.Core
