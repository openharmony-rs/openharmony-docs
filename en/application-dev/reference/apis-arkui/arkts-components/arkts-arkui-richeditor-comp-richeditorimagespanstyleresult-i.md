# RichEditorImageSpanStyleResult

```TypeScript
declare interface RichEditorImageSpanStyleResult
```

Provides the image span style information returned by the backend.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: RichEditorLayoutStyle
```

Image layout style.

**Type:** [RichEditorLayoutStyle](arkts-arkui-richeditor-comp-richeditorlayoutstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit: ImageFit
```

Scale mode of the image.

**Type:** [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resizable

```TypeScript
resizable?: ResizableOptions
```

Image resizing options.

**Type:** [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: [number, number]
```

Width and height of the image, in px. Default value depends on the **objectFit** setting. If the value of **objectFit** is **Cover**, the image height is the component height minus the top and bottom paddings, and the image width is the component width minus the left and right paddings.

**Type:** [number, number]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign: ImageSpanAlignment
```

Vertical alignment mode of the image.

**Type:** [ImageSpanAlignment](../arkts-apis/arkts-arkui-imagespanalignment-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
