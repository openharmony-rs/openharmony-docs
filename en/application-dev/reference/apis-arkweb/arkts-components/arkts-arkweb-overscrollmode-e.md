# OverScrollMode

Enumerates whether to enable overscroll mode.

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## NEVER

```TypeScript
NEVER = 0
```

Web overscroll mode disabled. Applicable to pages that do not require additional scrolling effects, such as scenarios where the content height matches the container height.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## ALWAYS

```TypeScript
ALWAYS = 1
```

Web overscroll mode enabled. Applicable to pages that require enhanced scrolling feedback, such as list pages or scenarios that require clear scroll boundary indication.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
