# NativeEmbedTouchInfo

```TypeScript
declare interface NativeEmbedTouchInfo
```

Provides detailed information about finger touch on a same-layer tag, including the tag ID and touch event. It is suitable for scenarios where handling same-layer element touch interaction is required, improving touch experience customization and flexibility.

@interface NativeEmbedTouchInfo [since 11 - 11]

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## embedId

```TypeScript
embedId?: string
```

Unique ID of the same-layer tag.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## result

```TypeScript
result?: EventResult
```

Gesture event consumption result.

**Type:** [EventResult](arkts-arkweb-web-comp-eventresult-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## touchEvent

```TypeScript
touchEvent?: TouchEvent
```

Touch action information.

**Type:** TouchEvent

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
