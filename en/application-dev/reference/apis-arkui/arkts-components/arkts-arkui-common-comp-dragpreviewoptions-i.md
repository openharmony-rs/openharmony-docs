# DragPreviewOptions

```TypeScript
declare interface DragPreviewOptions
```

Preview image processing mode and badge count during dragging.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DragPreviewMode | Array<DragPreviewMode>
```

How the background image is processed when the component is dragged.

Default value: **DragPreviewMode.AUTO**

If **DragPreviewMode.AUTO** is set concurrently with other enumerated values, **DragPreviewMode.AUTO** takes precedence and the other values are ignored.

**Type:** [DragPreviewMode](arkts-arkui-common-comp-dragpreviewmode-e.md) &#124; Array&lt;[DragPreviewMode](arkts-arkui-common-comp-dragpreviewmode-e.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modifier

```TypeScript
modifier?: ImageModifier
```

Drag preview style modifier. It applies image component attributes and styles to configure preview appearance (see Example 6). Supported effects: opacity, shadow, background blur, and rounded corners. Text drag previews only support default styling.

1. Opacity

Use [opacity](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-opacity.md#opacity). The value ranges from 0 to 1. If this parameter is set to **0** or left empty, the default opacity 0.95 is used. If this parameter is set to **1** or an abnormal value, the opacity is 1.

2. Shadow

Use [shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow).

3. Background blur

Use [backgroundEffect](arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect) or [backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle). If both are set, the latter setting takes precedence.

4. Rounded corners

Use [border](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#border) or [borderRadius](arkts-arkui-common-comp-commonmethod-c.md#borderradius). Modifier settings override mode settings.

Default value: empty (unmodifiable).

**Type:** [ImageModifier](arkts-arkui-common-comp-imagemodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## numberBadge

```TypeScript
numberBadge?: boolean | number
```

Whether to display the number badge or the number displayed on the badge. For a number badge, the value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. Values outside this range will be processed as the default state. If the value specified is a floating-point number, only the integer part is displayed.

**NOTE:** 

When multiple items are dragged, use this API to set the number of items dragged.

Default value: **true**.

**Type:** boolean &#124; number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sizeChangeEffect

```TypeScript
sizeChangeEffect?: DraggingSizeChangeEffect
```

Transition effect between the floating image and drag preview.

Default value: **DraggingSizeChangeEffect.DEFAULT**.

**Type:** [DraggingSizeChangeEffect](arkts-arkui-common-comp-draggingsizechangeeffect-e.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
