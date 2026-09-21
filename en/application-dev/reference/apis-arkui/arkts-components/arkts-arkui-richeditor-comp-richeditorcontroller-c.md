# RichEditorController

```TypeScript
declare class RichEditorController extends RichEditorBaseController
```

Implements the **RichEditor** component controller. Inherits from [RichEditorBaseController](arkts-arkui-richeditor-comp-richeditorbasecontroller-c.md).

> **NOTE:** 
> 
> When the content length exceeds the height of the component's display area, the insertion APIs (such as
> [addTextSpan](#addtextspan), [addImageSpan](#addimagespan),
> [addBuilderSpan](#addbuilderspan), and
> [addSymbolSpan](#addsymbolspan)) are called. The component automatically scrolls to keep
> the end of the inserted content visible.

## Objects to Import

```ts
controller: RichEditorController = new RichEditorController();
```

**Inheritance/Implementation:** RichEditorController extends [RichEditorBaseController](arkts-arkui-richeditor-comp-richeditorbasecontroller-c.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addBuilderSpan

```TypeScript
addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number
```

Adds a custom layout (**BuilderSpan**) to **RichEditor**.

> **NOTE:** 
> 
> - When a placeholder span is added to the **RichEditor** component, the placeholder span calls the system
> **measure** method to calculate its actual width, height, and position.
> 
> - You can use [RichEditorBuilderSpanOptions](arkts-arkui-richeditor-comp-richeditorbuilderspanoptions-i.md) to set the index of this builder in **RichEditor** (one character counts as one unit).
> 
> - This placeholder span cannot be focused, supports dragging, and supports some universal attributes. Its placeholder and deletion capabilities are equivalent to those of **ImageSpan**, and its length is regarded as one character.
> 
> - You can set a custom menu through [bindSelectionMenu](arkts-arkui-richeditor-comp-attribute.md#bindselectionmenu).
> 
> - The **builderSpan** information cannot be obtained through [getSpans](#getspans),[getSelection](#getselection), [onSelect](arkts-arkui-richeditor-comp-attribute.md#onselect), or [aboutToDelete](arkts-arkui-richeditor-comp-attribute.md#abouttodelete).
> 
> - The builder cannot be updated through [updateSpanStyle](#updatespanstyle) or [updateParagraphStyle](#updateparagraphstyle).
> 
> - Copying or pasting this builder node does not take effect.
> 
> - The layout constraints of the builder are passed in by **RichEditor**. If the outermost component in the builder does not have its size set, the size of **RichEditor** is used as the maxSize.
> 
> - The gesture-related event mechanism of the builder is the same as that of universal gesture events. If pass-through is not set in the builder, only the child components in the builder respond.
> 
> - If the component cursor is blinking, the cursor position is updated to after the newly inserted builder after insertion.
> 
> - For the node text of [addBuilderSpan](#addbuilderspan), the [enableDataDetector](arkts-arkui-richeditor-comp-attribute.md#enabledatadetector),[dataDetectorConfig](arkts-arkui-richeditor-comp-attribute.md#datadetectorconfig), and [enableSelectedDataDetector](arkts-arkui-richeditor-comp-attribute.md#enableselecteddatadetector) functions do not take effect.Only the following universal attributes are supported: [size](arkts-arkui-common-comp-commonmethod-c.md#size),[padding](arkts-arkui-common-comp-commonmethod-c.md#padding), [margin](arkts-arkui-common-comp-commonmethod-c.md#margin),[aspectRatio](arkts-arkui-common-comp-commonmethod-c.md#aspectratio), [borderStyle](arkts-arkui-common-comp-commonmethod-c.md#borderstyle),[borderWidth](arkts-arkui-common-comp-commonmethod-c.md#borderwidth), [borderColor](arkts-arkui-common-comp-commonmethod-c.md#bordercolor),[borderRadius](arkts-arkui-common-comp-commonmethod-c.md#borderradius),[backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor),[backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle),[opacity](arkts-arkui-common-comp.md#common), [blur](arkts-arkui-common-comp-commonmethod-c.md#blur),[backdropBlur](arkts-arkui-common-comp-commonmethod-c.md#backdropblur),[shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow),[grayscale](arkts-arkui-common-comp-commonmethod-c.md#grayscale),[brightness](arkts-arkui-common-comp-commonmethod-c.md#brightness),[saturate](arkts-arkui-common-comp-commonmethod-c.md#saturate), [contrast](arkts-arkui-common-comp-commonmethod-c.md#contrast),[invert](arkts-arkui-common-comp-commonmethod-c.md#invert),[sepia](arkts-arkui-common-comp-commonmethod-c.md#sepia),[hueRotate](arkts-arkui-common-comp-commonmethod-c.md#huerotate),[colorBlend](arkts-arkui-common-comp-commonmethod-c.md#colorblend),[linearGradientBlur](arkts-arkui-common-comp-commonmethod-c.md#lineargradientblur),[clip](arkts-arkui-common-comp-commonmethod-c.md#clip), [mask](arkts-arkui-common-comp-commonmethod-c.md#mask),[foregroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#foregroundblurstyle),[accessibilityGroup](arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup),[accessibilityText](arkts-arkui-common-comp-commonmethod-c.md#accessibilitytext),[accessibilityDescription](arkts-arkui-common-comp-commonmethod-c.md#accessibilitydescription),[accessibilityLevel](arkts-arkui-common-comp-commonmethod-c.md#accessibilitylevel),[sphericalEffect](arkts-arkui-common-comp-commonmethod-c.md#sphericaleffect),[lightUpEffect](arkts-arkui-common-comp-commonmethod-c.md#lightupeffect),[pixelStretchEffect](arkts-arkui-common-comp-commonmethod-c.md#pixelstretcheffect).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Custom layout content, used to create a BuilderSpan placeholder component in RichEditor. |
| options | [RichEditorBuilderSpanOptions](arkts-arkui-richeditor-comp-richeditorbuilderspanoptions-i.md) | No | Builder options. Pass this parameter when you need to set the offset position or accessibility attributes of the builder; when omitted, the builder is added to the end of all content. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the added **builderSpan** among all spans. |

## addImageSpan

```TypeScript
addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number
```

Adds image content. If the component cursor is blinking, the cursor position is updated to after the newly inserted image after insertion. When the controller is not bound to a component or the component bound to the controller is released, this API call does not take effect.

This API is a synchronous API. Adding network images directly under poor network conditions may block the UI thread and result in screen freezing. To avoid potential loading issues, do not directly add a network image.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Image content. |
| options | [RichEditorImageSpanOptions](arkts-arkui-richeditor-comp-richeditorimagespanoptions-i.md) | No | Image options.<br>Pass this parameter when you need to set the image style, offset position, or paragraph style; if it is not passed, the image is inserted at the end of the content using the default style. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the added **ImageSpan** among all spans. |

## addRichEditorBuilderSpan

```TypeScript
addRichEditorBuilderSpan(value: RichEditorBuilderSpan, info?: BuilderSpanInfo): number
```

Adds a custom layout (BuilderSpan) in **RichEditor**, providing identity recognition and lifecycle awareness capabilities.

> **NOTE:** 
> 
> - The [onAttach](arkts-arkui-richeditor-comp-richeditorbuilderspan-i.md#onattach) and [onDetach](arkts-arkui-richeditor-comp-richeditorbuilderspan-i.md#ondetach) callbacks in the BuilderSpan object receive a [BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md) object containing the span's id and offset.
> 
> - This interface is not supported when the **RichEditor** component is constructed with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md).
> 
> - Undo/redo does not restore BuilderSpan objects. When restored via undo, removed BuilderSpans degrade to whitespace text Spans.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorBuilderSpan](arkts-arkui-richeditor-comp-richeditorbuilderspan-i.md) | Yes | BuilderSpan object, containing the builder, lifecycle callbacks, and accessibility configuration. |
| info | [BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md) | No | Identity and position information of the BuilderSpan. **info.id** is used to identify the BuilderSpan, **info.offset** specifies the insertion position. When omitted, the BuilderSpan is appended to the end with id as **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index position of the added BuilderSpan among all Spans. |

## addSymbolSpan

```TypeScript
addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number
```

Adds an icon symbol (**SymbolSpan**) to **RichEditor**. If the component cursor is blinking, the cursor position is updated to after the newly inserted **SymbolSpan** after insertion.

**SymbolSpan** does not support gestures, copy operations, or drag processing.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Reference to the SymbolSpan icon resource, used to specify a system preset or custom Symbol icon. |
| options | [RichEditorSymbolSpanOptions](arkts-arkui-richeditor-comp-richeditorsymbolspanoptions-i.md) | No | Symbol options.<br>Pass this parameter when you need to set the offset position or style of the SymbolSpan; if it is not passed, the SymbolSpan is inserted at the end of the content with the default style. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the added **SymbolSpan** among all spans. |

## addTextSpan

```TypeScript
addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): number
```

Adds text content. If the component cursor is blinking, the cursor position is updated to after the newly inserted text after insertion. When the controller is not bound to a component or the component bound to the controller is released, this API call does not take effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text content.<br>The Resource type is supported since API version 20.<br>**Since:** 20 |
| options | [RichEditorTextSpanOptions](arkts-arkui-richeditor-comp-richeditortextspanoptions-i.md) | No | Text options.<br>Pass this parameter when you need to set information such as the offset position, text style, and paragraph style. If this parameter is not passed, the text is inserted at the end of the content using the default style. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the added **TextSpan** among all spans. |

## deleteSpans

```TypeScript
deleteSpans(value?: RichEditorRange): void
```

Deletes the text and images within the specified range. This API does not take effect when the controller is not bound to a component or the component bound to the controller is released.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | No | Range of the target spans. If this parameter is omitted, all text and image spans are deleted. |

## fromStyledString

```TypeScript
fromStyledString(value: StyledString): Array<RichEditorSpan>
```

Converts a styled string to a span.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | Yes | Styled string before conversion. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[RichEditorSpan](arkts-arkui-richeditor-comp-richeditorspan-t.md)&gt; | Text and image span information obtained after parsing the styled string. It can be used to query the content, style, and position of each span in the styled string.<br>Returns undefined when the controller is not bound to a component or the component bound to the controller is released. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. |

## getParagraphs

```TypeScript
getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>
```

Obtains the paragraph information within a specified range.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | No | Range of the paragraph to obtain.<br>If omitted, information about all paragraphs is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[RichEditorParagraphResult](arkts-arkui-richeditor-comp-richeditorparagraphresult-i.md)&gt; | Paragraph information within the selection range, including the style and start/end positions of each paragraph. It can be used to query paragraph layout attributes or update paragraph styles.<br>Returns undefined when the controller is not bound to a component or the component bound to the controller is released. |

## getRichEditorBuilderSpans

```TypeScript
getRichEditorBuilderSpans(value?: RichEditorRange): Array<BuilderSpanInfo>
```

Obtains the identity and position information of BuilderSpans within the specified range.

> **NOTE:** 
> 
> - This interface is not supported when the **RichEditor** component is constructed with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md).
> 
> - BuilderSpans created via the legacy [addBuilderSpan](#addbuilderspan)interface have **undefined** as their id (anonymous) in the returned [BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md).
> 
> - The **offset** field in the returned [BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md) reflects the current actual offset position and is dynamically updated as text content changes.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | No | Range of target BuilderSpans.<br>When omitted, returns all BuilderSpan information. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[BuilderSpanInfo](arkts-arkui-richeditor-comp-builderspaninfo-i.md)&gt; | Array of BuilderSpan identity and position information.<br>Returns **undefined** when the controller is not bound to a component or the component bound to the controller is released. |

## getSelection

```TypeScript
getSelection(): RichEditorSelection
```

Obtains the range and span information of the selection. If no text is selected, this API returns the information about the span where the caret is located.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RichEditorSelection](arkts-arkui-richeditor-comp-richeditorselection-i.md) | Detailed information about the start and end positions of the selection range and the selected text and images.<br>Returns undefined when the controller is not bound to a component or the component bound to the controller is released. |

## getSpans

```TypeScript
getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>
```

Obtains span information.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | No | Range of the span to obtain.<br>If omitted, information about all spans is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[RichEditorImageSpanResult](arkts-arkui-richeditor-comp-richeditorimagespanresult-i.md) &#124; [RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md)&gt; | Detailed information about the text and image spans within the specified range, including the position, content, style, and other attributes of each span. It can be used to query and manipulate the text and image content in the component.<br>Returns undefined when the controller is not bound to a component or the component bound to the controller is released. |

## toStyledString

```TypeScript
toStyledString(value: RichEditorRange): StyledString
```

Converts the component content within the given range to a styled string. **SymbolSpan** and **BuilderSpan** cannot be converted.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) | Yes | Source range. |

**Return value:**

| Type | Description |
| --- | --- |
| [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | Styled string obtained after converting the content in the specified range of the component. It can be used to transfer rich text content across components or perform style editing operations.<br>If the controller is not bound to a component or the component bound to the controller is released, **undefined** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. |

## updateParagraphStyle

```TypeScript
updateParagraphStyle(value: RichEditorParagraphStyleOptions): void
```

Updates the paragraph style.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorParagraphStyleOptions](arkts-arkui-richeditor-comp-richeditorparagraphstyleoptions-i.md) | Yes | Paragraph style options. |

## updateSpanStyle

```TypeScript
updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void
```

Updates the style of text, images, or **SymbolSpan**.

If only part of a span is updated, the span is split into multiple spans based on the updated part and the unupdated part. When the controller is not bound to a component or the component bound to the controller is released, this API call does not take effect.

Calling this API will not close the custom context menu on selection by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdatetextspanstyleoptions-i.md) &#124; [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdateimagespanstyleoptions-i.md) &#124; [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditor-comp-richeditorupdatesymbolspanstyleoptions-i.md) | Yes | Style options of the text, image, or symbol span.<br>**Since:** 11 |
