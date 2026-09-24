# Text properties/events

```TypeScript
declare class TextAttribute extends CommonMethod<TextAttribute>
```

In addition to the [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md), the following attributes are supported.

In addition to the [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md), the following events are supported.

**Inheritance/Implementation:** TextAttribute extends CommonMethod<TextAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## baselineOffset

```TypeScript
baselineOffset(value: number | ResourceStr)
```

Sets the offset of the text baseline.

Percentage values follow default display behavior.

A positive value moves the content upwards, while a negative value moves it downwards.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Offset of the text baseline.<br>Unit: fp. Default value: 0.<br>**Since:** 20 |

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: TextSpanType, content: CustomBuilder, responseType: TextResponseType,
    options?: SelectionMenuOptions)
```

Sets the custom selection menu.

The long-press response duration of **bindSelectionMenu** is 600 ms while that of [bindContextMenu](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu) is 800 ms. When both are bound and their triggering methods are set to long press, **bindSelectionMenu** takes precedence.

When the custom menu is too long, it is recommended that nest a [Scroll](arkts-arkui-scroll-comp.md#scroll) component inside to prevent the keyboard from being obscured.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).
> 
> When [editMenuOptions](#editmenuoptions) is used for configuring the text selection menu, the
> system's default style and trigger conditions are preserved.
> 
> In contrast, when [bindSelectionMenu](#bindselectionmenu) is used, both the menu style and the
> trigger conditions are fully customizable.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spanType | [TextSpanType](arkts-arkui-text-comp-textspantype-e.md) | Yes | Span type of the menu.<br>Default value: **TextSpanType.TEXT** |
| content | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Content of the menu. |
| responseType | [TextResponseType](arkts-arkui-text-comp-textresponsetype-e.md) | Yes | Response type of the menu.<br>Default value: **TextResponseType.LONG_PRESS** |
| options | SelectionMenuOptions | No | Options of the menu. |

## caretColor

```TypeScript
caretColor(color: ResourceColor)
```

Sets the color of the text selection handle, also known as the caret, in the text box.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the text selection handle.<br>Default value: **'#007DFF'** |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

Sets whether to enable leading punctuation compression.

> **NOTE:** 
> 
> - Leading punctuation is not compressed by default.
> 
> - For the range of punctuation marks that support leading compression, see [ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable leading punctuation compression.<br>**true**: Leading punctuation compression is enabled. **false**: Leading punctuation compression is disabled. |

## contentTransition

```TypeScript
contentTransition(transition: Optional<ContentTransition>)
```

Applies a transition animation to text content. Supports numeric flip animation via [NumericTextTransition](../arkts-apis/arkts-arkui-numerictexttransition-c.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transition | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ContentTransition](../arkts-apis/arkts-arkui-contenttransition-c.md)&gt; | Yes | Text animation effect. |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

Sets whether copy and paste operations are allowed.

Since API version 20, copied text from the **Text** component includes HTML-formatted content in the pasteboard.

- When the **Text** component contains child elements, only [Span](arkts-arkui-span-comp.md#span) and [ImageSpan](arkts-arkui-imagespan-comp.md#image_span) support HTML-formatted pasteboard content.  
- For styled strings, refer to [toHtml](../arkts-apis/arkts-arkui-styledstring-c.md#tohtml) for supported HTML conversion scope.

When **copyOption** is set to **CopyOptions.InApp** or **CopyOptions.LocalDevice**:

- A long press on the text will display a menu that offers the copy and select-all options.  
- By default, selected text is draggable. To disable dragging, set **draggable** to **false**.  
- To support **Ctrl+C** copying, also set [textSelectable](#textselectable) to  
**TextSelectableMode.SELECTABLE_FOCUSABLE**.

The **Text** component listens for **onClick**, which is a non-bubbling event. To allow parent components to respond to clicks within the **Text** area, use [parallelGesture](arkts-arkui-common-comp-commonmethod-c.md#parallelgesture) on the parent. For implementation guidance, see [Example 7: Setting Text Recognition](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#example-7-setting-text-recognition).

Because widgets do not have the long press event, the menu will not be displayed when users long press text.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | Yes | Whether copy and paste operations are allowed.<br>Default value: **CopyOptions.None** |

## dataDetectorConfig

```TypeScript
dataDetectorConfig(config: TextDataDetectorConfig)
```

Configures text recognition settings, including entity types to detect, display styles for detected entities, and long-press preview options.

This API must be used together with [enableDataDetector](#enabledatadetector). It takes effect only when **enableDataDetector** is set to **true**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [TextDataDetectorConfig](../arkts-apis/arkts-arkui-textdatadetectorconfig-i.md) | Yes | Text recognition configuration. |

## decoration

```TypeScript
decoration(value: DecorationStyleInterface)
```

Style and color of the text decorative line.

> **NOTE:** 
> 
> When the bottom contour of a character intersects with the decoration, underline avoidance is triggered, commonly
> affecting characters like "g", "j", "y", "q", and "p."
> 
> If the decoration color is set to **Color.Transparent**, it inherits the text color of the first character in
> each line. If the decoration color is set to **"#00FFFFFF"**, the line becomes fully transparent.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](../arkts-apis/arkts-arkui-decorationstyleinterface-i.md) | Yes | Style of the text decorative line.<br>Default value:<br>{<br> type: TextDecorationType.None,<br> color: Color.Black,<br> style: TextDecorationStyle.SOLID <br>}<br>**NOTE:** <br>The **style** parameter cannot be used in widgets.<br>**Since:** 12 |

## draggable

```TypeScript
draggable(value: boolean)
```

Sets the drag effect of the selected text.

This attribute cannot be used together with the [onDragStart](arkts-arkui-common-comp-commonmethod-c.md#ondragstart) event.

If set to **true**, **draggable** must be used in conjunction with CopyOptions. When **copyOptions** is set to **CopyOptions.InApp** or **CopyOptions.LocalDevice**, the selected text becomes draggable and can be copied into a text box.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Drag effect of the selected text.<br>**true**: The selected text is draggable. **false**: The selected text is not draggable.<br>Default value: **false** |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

Sets the extended options for the custom menu, including the text content, icon, and callback.

When [disableMenuItems](../../../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablemenuitems20) or

[disableSystemServiceMenuItems](../../../reference/apis-arkui/arkts-apis-uicontext-textmenucontroller.md#disablesystemservicemenuitems20) is used to disable system service menu items in the text selection menu, the disabled menu options will be excluded from the parameter list in the [onCreateMenu](../arkts-apis/arkts-arkui-editmenuoptions-i.md#oncreatemenu) callback of **editMenuOptions**.

> **NOTE:** 
> 
> When [editMenuOptions](#editmenuoptions) is used for configuring the text selection menu, the
> system's default style and trigger conditions are preserved.
> 
> In contrast, when [bindSelectionMenu](#bindselectionmenu) is used, both the menu style and the
> trigger conditions are fully customizable.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | Yes | Extended options of the custom menu. |

## ellipsisMode

```TypeScript
ellipsisMode(value: EllipsisMode)
```

Sets the ellipsis position.

For the settings to work, **overflow** must be set to **TextOverflow.Ellipsis** and **maxLines** must be specified. Setting **ellipsisMode** alone does not take effect.

**EllipsisMode.START** and **EllipsisMode.CENTER** take effect only when text overflows in a single line.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EllipsisMode](../arkts-apis/arkts-arkui-ellipsismode-e.md) | Yes | Ellipsis position.<br>Default value: **EllipsisMode.END** |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

Sets whether to enable automatic spacing between Chinese and Western characters.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable automatic spacing between Chinese and Western characters.<br>**true** to enable, **false** otherwise.<br>Default value: **false** |

## enableDataDetector

```TypeScript
enableDataDetector(enable: boolean)
```

Sets whether to enable special entity detection within the text. Special entities are detected when **enableDataDetector** is set to **true**.

The style of detected entities is as follows: the font color is changed to blue, and a blue underline is added.

> **NOTE:** 
> 
> - This API takes effect only when the device has an underlying text detection capability.
> 
> - When [textOverflow](#textoverflow) is set to **TextOverflow.MARQUEE**, text special entity detection is not performed.

&lt;!--RP2--&gt;&lt;!--RP2End--&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable text recognition.<br>**true**: Enable text recognition. **false**: Disable text recognition.<br>Default value: **false** |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

Sets whether to enable haptic feedback.

To enable haptic feedback, you must declare the **ohos.permission.VIBRATE** permission under **requestPermissions** in the [module.json5](../../../quick-start/module-configuration-file.md) file of the project.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable haptic feedback.<br>**true** to enable, **false** otherwise.<br> Default value: **true** |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

Sets whether to enable entity recognition for selected text. This API only works on devices that provide text recognition.

When **enableSelectedDataDetector** is set to **true**, all entity types are recognized by default.

This feature is only effective when CopyOptions is set to **CopyOptions.LocalDevice** or **CopyOptions.CrossDevice**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean &#124; undefined | Yes | Whether to enable entity recognition for selected text.<br>**true**: Entity recognition is enabled. **false**: Entity recognition is disabled. Default value: **true** |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

Adapts the line height to the actual text height for overlapped multi-line text. This API takes effect only when the line height is less than the actual text height. If this API is not set, the line height does not adapt to the actual text height by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the line height adapts to the actual text height.<br>**true**: Line height adapts to the actual text height. **false**: Line height does not adapt to the actual text height. |

## font

```TypeScript
font(value: Font)
```

Sets the text style, covering the font size, font width, font family, and font style.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text style. |

<a id="font-1"></a>

## font

```TypeScript
font(fontValue: Font, options?: FontSettingOptions)
```

Sets the font style, with support for font settings.

It is only effective for the **Text** component, not for its child components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontValue | Font | Yes | Sets the text style. |
| options | [FontSettingOptions](../arkts-apis/arkts-arkui-fontsettingoptions-i.md) | No | Font settings. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color.<br>Default value: **'#e6182431'**<br>Default value for wearables: **'#c5ffffff'** |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

Sets the font family.

> **NOTE:** 
> 
> You can use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to register custom fonts.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font family. Default font: **'HarmonyOS Sans'**<br>To specify multiple fonts, separate them with commas (,), and fonts are applied in priority order. Example: **'Arial, HarmonyOS Sans'**. |

## fontFeature

```TypeScript
fontFeature(value: string)
```

Sets the font feature, for example, monospaced digits.

Format: normal \| \&lt;feature-tag-value\&gt;

Format of **\&lt;feature-tag-value\&gt;**: \&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ]

There can be multiple **\&lt;feature-tag-value\&gt;** values, which are separated by commas (,).

For example, the input format for monospaced clock fonts is "ss01" on.

> **NOTE:** 
> 
> The **Text** component cannot contain both text and the child component **Span** or **ImageSpan**. If both of
> them exist, only the content in **Span** or **ImageSpan** is displayed.
> 
> The typesetting engine rounds down the value of [width](arkts-arkui-common-comp-commonmethod-c.md#width) to ensure that
> the value is an integer. If the typesetting engine rounds up the value instead, the right side of the text may be
> clipped.
> 
> When multiple **Text** components are placed in the [Row](arkts-arkui-row-comp.md#row) container with no specific layout or space
> allocation settings configured, the components are laid out based on the maximum size of the container. To make
> sure the sum of the components' main axis sizes does not exceed the main axis size of the container, you can set
> [layoutWeight](arkts-arkui-common-comp-commonmethod-c.md#layoutweight) or use the [flex layout](arkts-arkui-common-comp.md#common).
> 
> The system's default font supports the following ligatures: Th, fb, ff, fb, ffb, ffh, ffi, ffk, ffl, fh, fi, fk,
> fl, rf, rt, rv, rx, ry. These ligatures may cause unexpected effects of spans and styled strings. Disabling the
> ligature feature can avoid this issue.
> 
> Text rendering behavior is closely tied to the font file in use. For instance, the system's default font supports
> 8-punctuation compression only for left-side punctuation marks. Right-side punctuation, including exclamation
> marks, enumeration commas, and question marks, is not affected by this feature.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Font feature. |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

Sets the text size.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font size. If **fontSize** is of the number type, the unit fp is used. This parameter cannot be set in percentage.<br>Default value: **16fp**<br>Default value on wearable devices: **15fp** |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style.<br>Default value: **FontStyle.Normal** |

## fontVariations

```TypeScript
fontVariations(fontVariations: Array<FontVariation>)
```

Set the font variation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontVariations | Array&lt;[FontVariation](../arkts-apis/arkts-arkui-fontvariation-t.md)&gt; | Yes | Indicates the text font variation. |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

Sets the font weight. If the value is too large, the text may be clipped depending on the font.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight. For the number type, the value range is [100, 900], at an interval of 100. The default value is **400**. A larger value indicates a heavier font weight. For the string type, only strings that represent a number, for example, **400**, and the following enumerated values of **FontWeight** are supported: **bold**, **bolder**, **lighter**, **regular**, and **medium**.<br>Default value: **FontWeight.Normal**<br>Default value on wearable devices: **FontWeight.Regular**<br>The Resource type is supported since API version 20.<br>**Since:** 20 |

<a id="fontweight-1"></a>

## fontWeight

```TypeScript
fontWeight(weight: number | FontWeight | ResourceStr, options?: FontSettingOptions)
```

Sets the text font weight, with support for font settings.

It is only effective for the **Text** component, not for its child components.&lt;!--RP4--&gt;&lt;!--RP4End--&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| weight | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**. For the string type, only strings that represent a number, for example, **400**, and the following enumerated values of **FontWeight** are supported: **bold**, **bolder**, **lighter**, **regular**, and **medium**.<br>The Resource type is supported since API version 20.<br>**Since:** 20 |
| options | [FontSettingOptions](../arkts-apis/arkts-arkui-fontsettingoptions-i.md) | No | Font setting options.<br>When **enableVariableFontWeight** in **options** is set to **false**, variable font weight adjustment is disabled. If **weight** is set to a value at intervals of 100 within [100, 900], the font weight uses the specified value. If **weight** is set to a value that is not a multiple of 100, the default value **400** is used.<br>When **enableVariableFontWeight** in **options** is set to **true**, variable font weight adjustment is enabled. If **weight** is set to any integer within [100, 900], the font weight uses the specified value. |

## halfLeading

```TypeScript
halfLeading(halfLeading: boolean)
```

Whether half leading is enabled. Half leading refers to splitting the leading in half and applying it equally to the top and bottom of the line.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| halfLeading | boolean | Yes | Whether half leading is enabled. Half leading refers to splitting the leading in half and applying it equally to the top and bottom of the line.<br>**true**: Half leading is enabled. **false**: Half leading is not enabled.<br>Default value: **false** |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(value: TextHeightAdaptivePolicy)
```

Sets the font size adjustment strategy for adaptive text layout.

The available modes are as follows:

- **MAX_LINES_FIRST**: prioritizes using the [maxLines](#maxlines) attribute to control text  
height. If the **maxLines** setting results in a layout beyond the layout constraints, the text will shrink to a font size between [minFontSize](#minfontsize) and [maxFontSize](#maxfontsize) to allow for more content to be shown.  
- **MIN_FONT_SIZE_FIRST**: prioritizes using the **minFontSize** attribute to control text height. If the text fits  
on one line at **minFontSize**, the system attempts to increase the font size between **minFontSize** and **maxFontSize** to fill the line with the largest available font size. If the text cannot fit on a single line even at **minFontSize**, it sticks with **minFontSize**.  
- **LAYOUT_CONSTRAINT_FIRST**: prioritizes using layout constraints to control text height. If the resultant layout  
is beyond the layout constraints, the text will shrink to a font size between **minFontSize** and **maxFontSize** to respect the layout constraints. If the text still extends beyond the layout constraints after shrinking to **minFontSize**, the lines that exceed the constraints are deleted.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md) | Yes | How the adaptive height is determined for the text.<br>Default value: **TextHeightAdaptivePolicy.MAX_LINES_FIRST** |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

Sets whether to add spacing to the first and last lines to avoid text truncation. If this attribute is not set, no spacing is added by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to add spacing to the first and last lines to avoid text truncation.<br>**true**: Spacing is added to the first and last lines. **false**: Spacing is not added to the first and last lines. |

## incrementalUpdatePolicy

```TypeScript
incrementalUpdatePolicy(policy: IncrementalUpdatePolicy | undefined)
```

Sets the incremental update policy for text rendering.

This API takes effect only when Text content contains a StyledString. Default value is IncrementalUpdatePolicy.NONE.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [IncrementalUpdatePolicy](../arkts-apis/arkts-arkui-incrementalupdatepolicy-e.md) &#124; undefined | Yes | Indicates the incremental update policy. Passing `undefined` resets it to the default value. |

## letterSpacing

```TypeScript
letterSpacing(value: number | ResourceStr)
```

Sets the letter spacing for a text style.

If the value specified is a percentage or **0**, the default value is used. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

Negative values compress text. Excessive compression may reduce content area to zero, hiding content.

This setting applies to every character, including those at line endings.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Letter spacing.<br>Default value: **0**<br>Unit: fp<br>The Resource type is supported since API version 20.<br>**Since:** 20 |

## lineBreakStrategy

```TypeScript
lineBreakStrategy(strategy: LineBreakStrategy)
```

Sets the line break rule. This attribute takes effect only when [wordBreak](#wordbreak) is not **WordBreak.BREAK_ALL**. Hyphens are not supported.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [LineBreakStrategy](../arkts-apis/arkts-arkui-linebreakstrategy-e.md) | Yes | Line break rule.<br>Default value: **LineBreakStrategy.GREEDY** |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

Sets the text line height.

If the value is less than or equal to **0**, the line height is unrestricted and adapts to the font size. When the value is a number, the unit is fp. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

> **NOTE:** 
> 
> If certain characters have significantly taller glyphs than others in the same line, layout anomalies such as
> clipping, overlapping, or misalignment may occur. In this case, adjust component attributes such as height and
> line height to ensure proper layout rendering.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Text line height. |

## lineHeightMultiple

```TypeScript
lineHeightMultiple(value: number | undefined)
```

Sets the line height of text in multiple mode.

The line height equals the input parameter **value** multiplied by **fontHeight**.

> **NOTE:** 
> 
> When both this API and [lineHeight](#lineheight) are set, only **lineHeightMultiple** takes
> effect.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; undefined | Yes | Multiplier for the line height.<br>Value range: ≥ 0<br>Values ≤ 0 are treated as **0**. When the value is set to **0**, the default line height is used. Decimal values are supported. |

## lineSpacing

```TypeScript
lineSpacing(value: LengthMetrics)
```

Sets the line spacing of the text. If the value specified is less than or equal to 0, the default value **0** is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Line spacing. Default value: **0** |

<a id="linespacing-1"></a>

## lineSpacing

```TypeScript
lineSpacing(value: LengthMetrics, options?: LineSpacingOptions)
```

Sets the line spacing for text. When **LineSpacingOptions** is not specified, line spacing is applied above the first line and below the last line by default.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Line spacing. Values less than or equal to 0 are treated as the default value **0**. |
| options | [LineSpacingOptions](../arkts-apis/arkts-arkui-linespacingoptions-i.md) | No | Line spacing configuration options.<br>Default value: **{ onlyBetweenLines: false }** |

## marqueeOptions

```TypeScript
marqueeOptions(options: Optional<TextMarqueeOptions>)
```

Sets the marquee effect for text.

The **marqueeOptions** settings take effect only when **textOverflow** is set to **TextOverflow.MARQUEE**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextMarqueeOptions](arkts-arkui-text-comp-textmarqueeoptions-i.md)&gt; | Yes | Marquee animation properties such as enable/disable, step size, loop count, and direction. |

## maxFontScale

```TypeScript
maxFontScale(scale: number | Resource)
```

Sets the maximum font scale factor for text.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Maximum font scale factor for text.<br>Value range: [1, +∞)<br>**NOTE:** <br>Values less than 1 are treated as **1**. Other invalid values are ineffective by default. |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

Sets the maximum font size.

For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

For the setting to take effect, this attribute must be used together with [minFontSize](#minfontsize) and [maxLines](#maxlines), or layout constraint settings.

When the adaptive font size is used, the **fontSize** settings do not take effect.

If the value of **maxFontSize** is less than or equal to 0 or is less than the value of **minFontSize**, the adaptive font sizing feature is disabled. In such cases, the [fontSize](#fontsize) attribute is used instead. If **fontSize** is not set, the default value will apply.

Since API version 18, adaptive font sizing is supported on child components and styled strings, and text segments without an explicitly defined font size will automatically adjust based on the available space.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Maximum font size.<br>Unit: fp |

## maxLineHeight

```TypeScript
maxLineHeight(value: LengthMetrics | undefined)
```

Sets the maximum line height of text. If the value is less than or equal to 0, the maximum line height is unrestricted.

If **maxLineHeight** is less than **minLineHeight**, **maxLineHeight** takes effect using the value of **minLineHeight**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics &#124; undefined | Yes | Maximum line height of text. Percentage values are not supported.<br> Values less than or equal to 0 are treated as **0**. When the value is set to **0**, the maximum line height is unrestricted. |

## maxLines

```TypeScript
maxLines(value: number)
```

Sets the maximum number of lines for text.

By default, text is automatically folded. If this attribute is specified, the text will not exceed the specified number of lines. If there is extra text, you can use [textOverflow](#textoverflow) to specify how it is displayed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of lines of the text.<br>**NOTE:** <br>Value range: [0, *INT32_MAX*]<br>If this parameter is set to **0**, no text content is displayed. |

## minFontScale

```TypeScript
minFontScale(scale: number | Resource)
```

Sets the minimum font scale factor for text.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Minimum font scale factor for text.<br>Value range: [0, 1]<br>**NOTE:** <br> Values less than 0 are treated as 0, and values greater than 1 are treated as 1. Other invalid values do not take effect by default. |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

Sets the minimum font size.

For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

For the setting to take effect, this attribute must be used together with [maxFontSize](#maxfontsize) and [maxLines](#maxlines), or layout constraint settings.

When the adaptive font size is used, the **fontSize** settings do not take effect.

If the value of **minFontSize** is less than or equal to 0, the adaptive font sizing feature is disabled. In such cases, the [fontSize](#fontsize) attribute is used instead. If **fontSize** is not set, the default value will apply.

Since API version 18, adaptive font sizing is supported on child components and styled strings, and text segments without an explicitly defined font size will automatically adjust based on the available space.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Minimum font size.<br>Unit: fp |

## minLineHeight

```TypeScript
minLineHeight(value: LengthMetrics | undefined)
```

Sets the minimum line height of text. If the value is less than or equal to 0, the default value **0** is used.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics &#124; undefined | Yes | Minimum line height of text. Percentage values are not supported.<br> Values less than or equal to 0 are treated as **0**. |

## minLines

```TypeScript
minLines(minLines: Optional<number>)
```

Sets the minimum number of lines for text.

If the actual text height is less than the height for the minimum number of lines, the component uses the height corresponding to the minimum number of lines.

When this API and [maxLines](#maxlines) are both set, the minimum line height cannot exceed the maximum line height.

If [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) is set for the text, the component height is confined within the [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) bounds.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minLines | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Minimum number of lines of the text.<br>Value range: [0, *INT32_MAX*]<br> Values less than 0 are clamped to **0**. |

## onCopy

```TypeScript
onCopy(callback: (value: string) => void)
```

Called when data is copied to the pasteboard, which is displayed when the text box is long pressed. Currently, only text can be copied.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: string) =&gt; void | Yes | Callback of the listened event. |

## onMarqueeStateChange

```TypeScript
onMarqueeStateChange(callback: Callback<MarqueeState>)
```

Called when the marquee animation reaches the specified state.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[MarqueeState](arkts-arkui-text-comp-marqueestate-e.md)&gt; | Yes | Callback that receives a **MarqueeState** enum value, which indicates the current state of the marquee animation. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void)
```

Called when the text selection position changes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (selectionStart: number, selectionEnd: number) =&gt; void | Yes | Callback of the listened event. |

## onWillCopy

```TypeScript
onWillCopy(callback: Callback<string, boolean>)
```

Called before the copy operation is performed.

**Since**: 26.0.0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; | Yes | The string type indicates the text to be copied.<br>The boolean type indicates whether the text can be copied. The value **true** means yes and **false** means no. |

## optimizeTrailingSpace

```TypeScript
optimizeTrailingSpace(optimize: Optional<boolean>)
```

Sets whether to optimize trailing spaces at line endings during text layout, resolving alignment display issues caused by trailing spaces.

When **Text.optimizeTrailingSpace** is set to **true**:

* Trailing space optimization applies to multi-line text, single-line text, and text and image layouts (particularly noticeable with **TextAlign.Center** or **TextAlign.End**).  
* For text containing only spaces, decoration lines, shadows, and background colors follow the space text display.  
* Leading spaces are not optimized. When text with trailing spaces wraps, trailing spaces on each line are optimized based on component width.

When optimizing pure space text by setting [optimizeTrailingSpace](#optimizetrailingspace) to **true**, you cannot simultaneously set [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [decoration](#decoration), and [textAlign](#textalign) attributes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| optimize | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to optimize trailing spaces.<br>**true** to optimize, **false** otherwise.<br>Default value: **false** |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

Sets whether to enable orphan character optimization during text typesetting. If this attribute is not set, orphan character optimization is disabled by default.

Orphan character optimization improves the text layout by handling the orphan character (the first Chinese character of the last line of a paragraph) more efficiently. When enabled, it adjusts line breaks to avoid orphan characters as much as possible. This feature takes effect only when [wordBreak](#wordbreak) is not **BREAK_ALL** and [locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the first [TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the text to be typeset is either **"zh-Hans"** or **"zh-Hant"**.

**Since**: 26.0.0

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable orphan character optimization for the last line of the paragraph.<br>**true**: Orphan character optimization is enabled. **false**: Orphan character optimization is disabled.<br>When the value is **undefined** or **null**, orphan character optimization is disabled. |

## privacySensitive

```TypeScript
privacySensitive(supported: boolean)
```

Sets whether to enable privacy mode on widgets.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supported | boolean | Yes | Whether to enable privacy mode on widgets.<br>Default value: **false**. The value **true** means to enable privacy mode, in which case text is obscured with hyphens (-).<br>**NOTE:** <br>The value **null** means not to enable privacy mode on widgets.<br>Enabling privacy mode requires support from the widget framework. You can use [obscured](arkts-arkui-common-comp-commonmethod-c.md#obscured) to set how the component content is obscured. |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

Whether to enable punctuation overflow at line ends.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the feature, the default value is false. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: ResourceColor)
```

Sets the background color of the selected text. If the opacity is not set, a 20% opacity will be used.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the selected text.<br>Default value: **'#007DFF'** |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

Applies a transition animation to text content. Supports numeric flip animation via [NumericTextTransition](../arkts-apis/arkts-arkui-numerictexttransition-c.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) &#124; undefined | Yes | Drag preview style for selected text.<br>If this parameter is set to **undefined**, the drag preview follows the theme: white in light mode and black in dark mode. |

## selection

```TypeScript
selection(selectionStart: number, selectionEnd: number)
```

Sets text selection.

The selected text is highlighted, with selection handles and the text selection menu displayed.

If [copyOption](#copyoption) is set to **CopyOptions.None**, the setting of the **selection** attribute does not take effect.

If [textOverflow](#textoverflow) is set to **TextOverflow.MARQUEE**, the setting of the **selection** attribute does not take effect.

If the value of **selectionStart** is greater than or equal to that of **selectionEnd**, no text will be selected. The value range is [0, textSize], where **textSize** indicates the maximum number of characters in the text content. If the value is less than 0, the value **0** will be used. If the value is greater than **textSize**, **textSize** will be used.

If the selection range falls within a truncated or invisible area, selection is ignored. When [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) is set to **false**, the text outside the parent component can be selected.

You can obtain the selection range change result through the [onTextSelectionChange](#ontextselectionchange) API.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the selected text.<br>Default value: **-1** |
| selectionEnd | number | Yes | End position of the selected text.<br>Default value: **-1** |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle)
```

Applies gradient or solid color effects to text. Supports [RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md), [LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md), and [ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md). **shaderStyle** takes precedence over [fontColor](arkts-arkui-symbolspan-comp-attribute.md#fontcolor) and AI-based styling. For solid colors, prefer using [fontColor](arkts-arkui-symbolspan-comp-attribute.md#fontcolor).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) | Yes | Shader effect.<br>Based on the input, the system applies a radial gradient ([RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md)), linear gradient ([LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md)), or solid color ([ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md)). <br>**NOTE:** <br>If [RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md) is used and the **center** parameter (from [RadialGradientOptions](arkts-arkui-common-comp-radialgradientoptions-i.md)) is outside the component bounds, setting **repeating** to **true** enhances the gradient effect. |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

Sets the text stroke color.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Stroke color.<br>Default value: font color. Invalid values are treated as the default value. |

## strokeJoinStyle

```TypeScript
strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined)
```

Sets the join style of the text stroke.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strokeJoinStyle | [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md) &#124; undefined | Yes | Join style of the text stroke.<br>If the value is **undefined**, the join style is set to the default value **StrokeJoinStyle.MITER_JOIN**. For details, see [StrokeJoinStyle](../../../reference/apis-arkui/arkui-ts/ts-text-common.md#strokejoinstyle). |

## strokeWidth

```TypeScript
strokeWidth(width: Optional<LengthMetrics>)
```

Sets the text stroke width.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Text stroke width. When the unit of **LengthMetrics** is **px**:<br>Values &lt; 0: solid text.<br>Values &gt; 0: outlined text. <br>Default value: **0** (no stroke). |

## tailIndents

```TypeScript
tailIndents(value: Optional<LengthMetrics | Array<LengthMetrics>>)
```

Specify the tail indentation for each line in a text block.

<p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>When a single LengthMetrics value is provided, all lines share the same tail indent. <br>When an array is provided, the i-th element specifies the tail indent for the i-th line. If the number of text lines exceeds the array length, the last element in the array is used for the remaining lines. <br>Negative values are treated as 0. <br>If the value is set to undefined, the default value 0 is used. </p>

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics &#124; Array&lt;LengthMetrics&gt;&gt; | Yes | The tail indent value(s).Default value is 0. |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

Sets the horizontal alignment of the text.

The text takes up the full width of the **Text** component.

The vertical position of the text paragraph can be controlled by the [align](arkts-arkui-common-comp-commonmethod-c.md#align) attribute, but the horizontal position cannot be controlled by **align** in this component. The specific effects are as follows:

- **Alignment.TopStart**, **Alignment.Top**, **Alignment.TopEnd**: Content aligns to the top.  
- **Alignment.Start**, **Alignment.Center**, **Alignment.End**: Content is centered vertically.  
- **Alignment.BottomStart**, **Alignment.Bottom**, **Alignment.BottomEnd:** Content aligns to the bottom.

When **textAlign** is set to **TextAlign.JUSTIFY**, the [wordBreak](#wordbreak) property must be configured according to the text content. The last line of text aligns to the start horizontally and does not participate in justification.

> **NOTE:** 
> 
> **textAlign** only adjusts the overall text layout and does not affect character display order. For character
> display order adjustment, see
> [Bidirectional Text Layout and Alignment](../../../ui/arkts-internationalization.md#bidirectional-text-layout-and-alignment).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextAlign](../arkts-apis/arkts-arkui-textalign-e.md) | Yes | Horizontal alignment of the text.<br>Default value: **TextAlign.Start**<br>Default value on wearable devices: **TextAlign.Center** |

## textCase

```TypeScript
textCase(value: TextCase)
```

Sets the text case.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextCase](../arkts-apis/arkts-arkui-textcase-e.md) | Yes | Text case.<br>Default value: **TextCase.Normal** |

## textContentAlign

```TypeScript
textContentAlign(textContentAlign: Optional<TextContentAlign>)
```

Sets the vertical alignment of the text content area within the component.

This API takes effect only when the height of the text content exceeds the component's height.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| textContentAlign | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextContentAlign](../arkts-apis/arkts-arkui-textcontentalign-e.md)&gt; | Yes | Vertical alignment of the text.<br>If the value is **undefined** or invalid, alignment defaults to **Center**. |

## textDirection

```TypeScript
textDirection(direction: TextDirection | undefined)
```

Specifies the text layout direction. If this attribute is not set, the default text layout direction follows the component layout direction.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [TextDirection](../arkts-apis/arkts-arkui-textdirection-e.md) &#124; undefined | Yes | Text layout direction.<br>If this parameter is set to **undefined**, the text layout direction follows the component layout direction as defined by **TextDirection.DEFAULT**. |

## textIndent

```TypeScript
textIndent(value: Length)
```

Sets the indent of the first line text.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Indent of the first line text.<br>Default value: **0**<br>Unit: fp |

## textOverflow

```TypeScript
textOverflow(options: TextOverflowOptions)
```

Sets the display mode for overflowing text.

When [TextOverflowOptions](arkts-arkui-text-comp-textoverflowoptions-i.md) is set to **TextOverflow.None**, **TextOverflow.Clip**, or **TextOverflow.Ellipsis**:

- **TextOverflow.None** or **TextOverflow.Clip**: Text is truncated when it exceeds the maximum number of lines.  
- **TextOverflow.Ellipsis**: Overflowing text is replaced with an ellipsis (...).  
- This must be used with [maxLines](#maxlines) for the settings to take effect.  
- Line breaking behavior is controlled by [wordBreak](#wordbreak). By default, it uses  
**WordBreak.BREAK_WORD**, which breaks text by word (for example, English text is broken at word boundaries). To break text by character, set **wordBreak** to **WordBreak.BREAK_ALL**.  
- Line wrapping behavior is governed by [lineBreakStrategy](#linebreakstrategy) which takes  
effect only when [wordBreak](#wordbreak) is not **WordBreak.BREAK_ALL**. Hyphens are not supported.  
- Since API version 11, it is recommended that you configure both [textOverflow](#textoverflow)  
and [wordBreak](#wordbreak) to control truncation behavior. For details, see [Example 4](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#example-4-setting-text-wrapping-and-line-breaking) &lt;!--RP1--&gt;&lt;!--RP1End--&gt;.

When **TextOverflowOptions** is set to **TextOverflow.MARQUEE**:

- Text scrolls horizontally within a single line.  
- [maxLines](#maxlines) and[copyOption](#copyoption) are ignored.  
- The [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) attribute of the **Text** component defaults to **true**.  
- [CustomSpan](../arkts-apis/arkts-arkui-customspan-c.md) is not supported in marquee mode.  
- Behavior of [textAlign](#textalign): If the text does not scroll, **textAlign** applies; if  
the text scrolls, **textAlign** is ignored.  
- Since API version 12, **TextOverflow.MARQUEE** is available for the **ImageSpan** component, where the text and  
images are allowed to scroll within a single line.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextOverflowOptions](arkts-arkui-text-comp-textoverflowoptions-i.md) | Yes | Display mode when the text is too long.<br>**Since:** 18 |

## textSelectable

```TypeScript
textSelectable(mode: TextSelectableMode)
```

Sets whether the text is selectable and focusable.

This attribute must be used in conjunction with [copyOption](#copyoption).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [TextSelectableMode](../arkts-apis/arkts-arkui-textselectablemode-e.md) | Yes | Whether the text is selectable and focusable.<br>Default value: **TextSelectableMode.SELECTABLE_UNFOCUSABLE** |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

Sets the text shadow.

Intelligent color extraction is not supported for the **type**, **fill**, and **color** fields of the **ShadowOptions** object.

Since API version 11, this API supports input parameters in an array to implement multiple text shadows.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; Array&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt; | Yes | Text shadow.<br>**Since:** 11 |

## textVerticalAlign

```TypeScript
textVerticalAlign(textVerticalAlign: Optional<TextVerticalAlign>)
```

Sets the vertical alignment of the text.

> **NOTE:** 
> 
> - When this API and [halfLeading](#halfleading) are both set, **halfLeading** does not take effect.
> 
> - The effect of this attribute is noticeable only when the same font size is used in a paragraph and [lineHeight](#lineheight) is set, or when different font sizes are mixed in a paragraph.Otherwise, the effect is the same regardless of whether this attribute is set or which enum value is used. The
> **SuperscriptStyle** in TextStyle takes effect only when the value of
> TextVerticalAlign is set to **TextVerticalAlign.BASELINE**. In other vertical
> alignment modes, the superscript and subscript texts are displayed in the same way as the normal text.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| textVerticalAlign | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextVerticalAlign](../arkts-apis/arkts-arkui-textverticalalign-e.md)&gt; | Yes | Vertical alignment of the text.<br>Default value: **TextVerticalAlign.BASELINE** |

## wordBreak

```TypeScript
wordBreak(value: WordBreak)
```

Sets the word break rule.

By default, when **wordBreak** is not called or is set to **WordBreak.BREAK_WORD**, text is broken by word. (for example, English text is broken at word boundaries).

To break text by character, with the excess part displayed as an ellipsis (...), use **WordBreak.BREAK_ALL** in combination with **{overflow: TextOverflow.Ellipsis}** and **maxLines**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [WordBreak](../arkts-apis/arkts-arkui-wordbreak-e.md) | Yes | Word break rule.<br>Default value: **WordBreak.BREAK_WORD** |
