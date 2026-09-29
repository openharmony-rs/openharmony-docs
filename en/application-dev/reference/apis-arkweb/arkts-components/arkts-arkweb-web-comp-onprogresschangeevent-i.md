# OnProgressChangeEvent

```TypeScript
declare interface OnProgressChangeEvent
```

Defines the callback information triggered when the web page loading progress changes, including the new progress value. It is suitable for scenarios where monitoring page loading progress is required, improving loading process visibility and user experience.

**Since:** 12

<!--Device-unnamed-declare interface OnProgressChangeEvent--><!--Device-unnamed-declare interface OnProgressChangeEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## newProgress

```TypeScript
newProgress: number
```

New loading progress, which is an integer in the range [0, 100].

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnProgressChangeEvent-newProgress: number--><!--Device-OnProgressChangeEvent-newProgress: number-End-->

**System capability:** SystemCapability.Web.Webview.Core
