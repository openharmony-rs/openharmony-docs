# NativeEmbedMouseInfo

```TypeScript
declare interface NativeEmbedMouseInfo
```

Provides detailed information about clicking or touching and holding a same-layer tag using the mouse or touchpad, including the tag ID and mouse event. It is suitable for scenarios where handling same-layer element mouse interaction is required, improving mouse experience customization and flexibility.

**Since:** 20

<!--Device-unnamed-declare interface NativeEmbedMouseInfo--><!--Device-unnamed-declare interface NativeEmbedMouseInfo-End-->

**System capability:** SystemCapability.Web.Webview.Core

## embedId

```TypeScript
embedId?: string
```

Unique ID of the same-layer tag.

**Type:** string

**Since:** 20

<!--Device-NativeEmbedMouseInfo-embedId?: string--><!--Device-NativeEmbedMouseInfo-embedId?: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## mouseEvent

```TypeScript
mouseEvent?: MouseEvent
```

Information about clicking or touching and holding using the mouse or touchpad.

**Type:** MouseEvent

**Since:** 20

<!--Device-NativeEmbedMouseInfo-mouseEvent?: MouseEvent--><!--Device-NativeEmbedMouseInfo-mouseEvent?: MouseEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## result

```TypeScript
result?: EventResult
```

Mouse event consumption result.

**Type:** [EventResult](arkts-arkweb-web-comp-eventresult-c.md)

**Since:** 20

<!--Device-NativeEmbedMouseInfo-result?: EventResult--><!--Device-NativeEmbedMouseInfo-result?: EventResult-End-->

**System capability:** SystemCapability.Web.Webview.Core
