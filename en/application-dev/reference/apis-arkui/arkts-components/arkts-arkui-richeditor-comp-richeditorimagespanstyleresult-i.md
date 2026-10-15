# RichEditorImageSpanStyleResult

```TypeScript
declare interface RichEditorImageSpanStyleResult
```

Provides the image span style information returned by the backend.

**Since:** 10

<!--Device-unnamed-declare interface RichEditorImageSpanStyleResult--><!--Device-unnamed-declare interface RichEditorImageSpanStyleResult-End-->

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

<!--Device-RichEditorImageSpanStyleResult-layoutStyle?: RichEditorLayoutStyle--><!--Device-RichEditorImageSpanStyleResult-layoutStyle?: RichEditorLayoutStyle-End-->

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

<!--Device-RichEditorImageSpanStyleResult-objectFit: ImageFit--><!--Device-RichEditorImageSpanStyleResult-objectFit: ImageFit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resizable

```TypeScript
resizable?: ResizableOptions
```

Image resizing options.

**Type:** [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-RichEditorImageSpanStyleResult-resizable?: ResizableOptions--><!--Device-RichEditorImageSpanStyleResult-resizable?: ResizableOptions-End-->

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

<!--Device-RichEditorImageSpanStyleResult-size: [number, number]--><!--Device-RichEditorImageSpanStyleResult-size: [number, number]-End-->

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

<!--Device-RichEditorImageSpanStyleResult-verticalAlign: ImageSpanAlignment--><!--Device-RichEditorImageSpanStyleResult-verticalAlign: ImageSpanAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
