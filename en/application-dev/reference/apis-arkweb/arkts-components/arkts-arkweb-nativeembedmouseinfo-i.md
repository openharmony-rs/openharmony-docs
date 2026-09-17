# NativeEmbedMouseInfo

Provides detailed information about clicking or touching and holding a same-layer tag using the mouse or touchpad, including the tag ID and mouse event. It is suitable for scenarios where handling same-layer element mouse interaction is required, improving mouse experience customization and flexibility.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## embedId

```TypeScript
embedId?: string
```

Unique ID of the same-layer tag.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## mouseEvent

```TypeScript
mouseEvent?: MouseEvent
```

Information about clicking or touching and holding using the mouse or touchpad.

**Type:** MouseEvent

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## result

```TypeScript
result?: EventResult
```

Mouse event consumption result.

**Type:** [EventResult](arkts-arkweb-eventresult-c.md)

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core
