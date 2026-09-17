# WebRotateEffect

Enumerates the modes in which the component's content is rendered to fit the new size during its width and height animation process when the component is rotated.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## TOPLEFT_EFFECT

```TypeScript
TOPLEFT_EFFECT = 0
```

The component's content stays at the final size and always aligned with the upper left corner of the component. This value is used by default.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## RESIZE_COVER_EFFECT

```TypeScript
RESIZE_COVER_EFFECT = 1
```

While maintaining its aspect ratio in the final state, the component's content is scaled to cover the component's entire content box. It is always aligned with the center of the component, so that its middle part is displayed.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core
