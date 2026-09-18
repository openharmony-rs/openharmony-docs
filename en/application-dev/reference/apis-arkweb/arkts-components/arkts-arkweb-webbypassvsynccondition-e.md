# WebBypassVsyncCondition

Enumerates whether to allow the rendering process to bypass the vsync scheduling.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

The rendering process does not bypass the vsync scheduling. Default value.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## SCROLLBY_FROM_ZERO_OFFSET

```TypeScript
SCROLLBY_FROM_ZERO_OFFSET = 1
```

When scrollBy (which supports only scroll with an offset) is used and the web page scroll offset is 0, the rendering process skips vsync scheduling and draws directly.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core
