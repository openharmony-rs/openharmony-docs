# ViewportFit

Enumerates the viewport types available for **viewport-fit** in the web page **\&lt;meta&gt;** tag.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## AUTO

```TypeScript
AUTO = 0
```

Default value. The entire web page is visible. This is suitable for scenarios where the web page needs to be fully displayed within the visible area, and is recommended for most common web pages.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## CONTAINS

```TypeScript
CONTAINS = 1
```

The initial layout viewport and visual viewport are within the largest rectangle that fits the device display. This is suitable for scenarios where content must be completely within the safe area, such as preventing important content from being obscured by a notch.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## COVER

```TypeScript
COVER = 2
```

The initial layout viewport and visual viewport are within the bounding rectangle of the device's physical screen. This is suitable for scenarios where web page content needs to extend to the screen edges, such as full-screen background effects or immersive experiences.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
