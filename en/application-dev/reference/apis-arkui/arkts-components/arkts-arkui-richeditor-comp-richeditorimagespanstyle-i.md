# RichEditorImageSpanStyle

```TypeScript
declare interface RichEditorImageSpanStyle
```

Image style.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutStyle

```TypeScript
layoutStyle?: RichEditorLayoutStyle
```

Image layout style. Default value: {"borderRadius":"","margin":""}

**Type:** [RichEditorLayoutStyle](arkts-arkui-richeditor-comp-richeditorlayoutstyle-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

Image scaling type.

Default value: ImageFit.Cover.

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
size?: [Dimension, Dimension]
```

Width and height of the image, in vp by default. Default value: related to the value of objectFit. Different objectFit values have different default sizes. When objectFit is set to Cover, the image height is the component height minus the top and bottom padding of the component, and the image width is the component width minus the left and right padding of the component. Setting the size in percentage is not supported.

**Type:** [Dimension, Dimension]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## verticalAlign

```TypeScript
verticalAlign?: ImageSpanAlignment
```

Vertical alignment mode of the image.

Default value: ImageSpanAlignment.BOTTOM

**Type:** [ImageSpanAlignment](../arkts-apis/arkts-arkui-imagespanalignment-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
