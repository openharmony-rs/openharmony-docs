# Text properties/events

```TypeScript
declare class TextAttribute extends CommonMethod<TextAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** TextAttribute extends CommonMethod<TextAttribute>

**Since:** 7

<!--Device-unnamed-declare class TextAttribute extends CommonMethod<TextAttribute>--><!--Device-unnamed-declare class TextAttribute extends CommonMethod<TextAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## baselineOffset

```TypeScript
baselineOffset(value: number | ResourceStr)
```

Sets the offset of the text baseline. It can be used to adjust the baseline alignment between the text and other elements (such as images and icons), or used in special typesetting scenarios that require precise vertical alignment, such as mixed text and images, mathematical formulas, and chemical formulas. If this API is not used, the default offset is 0.

A positive value moves the content upwards, while a negative value moves it downwards.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-baselineOffset(value: number | ResourceStr): TextAttribute--><!--Device-TextAttribute-baselineOffset(value: number | ResourceStr): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Offset of the text baseline. If the value is set to a percentage, the value is displayed as 0.<br>Unit: fp. <br>The Resource type is supported since API version 20.<br>**Since:** 20 |

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: TextSpanType, content: CustomBuilder, responseType: TextResponseType,
    options?: SelectionMenuOptions)
```

Sets the custom selection menu. If this API is not used, the default menu type is **TextSpanType.TEXT** and the response type is **TextResponseType.LONG_PRESS**.

The long-press response duration of **bindSelectionMenu** is 600 ms while that of [bindContextMenu](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu) is 800 ms. When both are bound and their triggering methods are set to long press, **bindSelectionMenu** takes precedence.

When the custom menu is too long, it is recommended that nest a [Scroll](arkts-arkui-scroll-comp.md) component inside to prevent the keyboard from being obscured.

Since API version 26.0.0, when the text component calls this API, the image preview menu takes effect if the **menuType** attribute in **options** is set to **MenuType.PREVIEW_MENU**.

To use the image preview menu, set **spanType** to **TextSpanType.IMAGE**, **responseType** to **TextResponseType.LONG_PRESS**, and **menuType** in **options** to **MenuType.PREVIEW_MENU**.

When [copyOption](#copyoption) is set to **CopyOptions.None**, the setting of the image preview menu does not take effect.

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

<!--Device-TextAttribute-bindSelectionMenu(spanType: TextSpanType, content: CustomBuilder, responseType: TextResponseType,    options?: SelectionMenuOptions): TextAttribute--><!--Device-TextAttribute-bindSelectionMenu(spanType: TextSpanType, content: CustomBuilder, responseType: TextResponseType,    options?: SelectionMenuOptions): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spanType | [TextSpanType](arkts-arkui-text-comp-textspantype-e.md) | Yes | Span type of the menu. |
| content | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Content of the menu. |
| responseType | [TextResponseType](arkts-arkui-text-comp-textresponsetype-e.md) | Yes | Response type of the menu. |
| options | SelectionMenuOptions | No | Options of the selection menu, which are used to customize the menu behavior. The options include callback configuration items such as menu appearance, disappearance, display, and hiding.<br>Default value: If this parameter is not set, the default selection menu configuration is used. |

## caretColor

```TypeScript
caretColor(color: ResourceColor)
```

Sets the color of the handle for the selected area in the text component. If this API is not used, the default color of the handle for the selected area is **'#007DFF'** (blue).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TextAttribute-caretColor(color: ResourceColor): TextAttribute--><!--Device-TextAttribute-caretColor(color: ResourceColor): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the text selection handle. |

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

<!--Device-TextAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextAttribute--><!--Device-TextAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable leading punctuation compression.<br>The value **true** indicates to enable leading punctuation compression, and **false** indicates the opposite. The value **undefined** indicates that leading punctuation compression is disabled. |

## contentTransition

```TypeScript
contentTransition(transition: Optional<ContentTransition>)
```

Applies a transition animation to text content. The numeric flip animation is supported via [NumericTextTransition](../arkts-apis/arkts-arkui-numerictexttransition-c.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAttribute-contentTransition(transition: Optional<ContentTransition>): TextAttribute--><!--Device-TextAttribute-contentTransition(transition: Optional<ContentTransition>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transition | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ContentTransition](../arkts-apis/arkts-arkui-contenttransition-c.md)&gt; | Yes | Text animation, which is used to set the transition animation effect when the text content changes. You can set this parameter to [NumericTextTransition](../arkts-apis/arkts-arkui-numerictexttransition-c.md) to implement the flip animation effect when the number changes. <br>If the value is **undefined**, there is no flipping effect. |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

Sets whether copy and paste operations are allowed. If this API is not used, the default value is **CopyOptions.None**, indicating that the text cannot be copied or pasted.

The features of multiple attributes depend on the settings of **copyOption**, including [selection](#selection), [setTextSelection](arkts-arkui-text-comp-textcontroller-c.md#settextselection), [draggable](#draggable), [enableSelectedDataDetector](#enableselecteddatadetector), and [textSelectable](#textselectable). For details about the dependency conditions, see the description of each attribute.

Since API version 20, copied text from the **Text** component includes HTML-formatted content in the pasteboard.

- When the **Text** component contains child elements, only [Span](arkts-arkui-span-comp.md) and [ImageSpan](arkts-arkui-imagespan-comp.md) support HTML-formatted pasteboard content.  
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

<!--Device-TextAttribute-copyOption(value: CopyOptions): TextAttribute--><!--Device-TextAttribute-copyOption(value: CopyOptions): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | Yes | Whether copy and paste operations are allowed. |

## dataDetectorConfig

```TypeScript
dataDetectorConfig(config: TextDataDetectorConfig)
```

Configures text recognition settings, including entity types to detect, display styles for detected entities, and long-press preview options.

This API must be used together with [enableDataDetector](#enabledatadetector). It takes effect only when **enableDataDetector** is set to **true**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-dataDetectorConfig(config: TextDataDetectorConfig): TextAttribute--><!--Device-TextAttribute-dataDetectorConfig(config: TextDataDetectorConfig): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [TextDataDetectorConfig](../arkts-apis/arkts-arkui-textdatadetectorconfig-i.md) | Yes | Text recognition configuration object, which is used to configure the specific behavior of text recognition. You can configure the types of entities to recognize (such as phone numbers, websites, email addresses, addresses, and dates), display styles for the entities, and whether to enable long-press for preview. This parameter must be used together with [enableDataDetector](#enabledatadetector). |

## decoration

```TypeScript
decoration(value: DecorationStyleInterface)
```

Style and color of the text decorative line. If this API is not used, the default text decorative line style is as follows:

{

&nbsp;type:&nbsp;TextDecorationType.None,

&nbsp;color:&nbsp;Color.Black,

&nbsp;style:&nbsp;TextDecorationStyle.SOLID&nbsp;

}

> **NOTE:** 
> 
> When the bottom contour of a character intersects with the decoration, underline avoidance is triggered, commonly
> affecting characters like "g", "j", "y", "q", and "p."
> 
> When the decorative line color is set to **Color.Transparent**, the decorative line is displayed as the text
> color of the first character in each line. When the color is set to the transparent hexadecimal value
> **"#00FFFFFF"**, the decorative line is displayed in transparent color.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-decoration(value: DecorationStyleInterface): TextAttribute--><!--Device-TextAttribute-decoration(value: DecorationStyleInterface): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](../arkts-apis/arkts-arkui-decorationstyleinterface-i.md) | Yes | Style of the text decorative line.<br>**NOTE:** <br>The **style** parameter cannot be used in widgets.<br>**Since:** 12 |

## draggable

```TypeScript
draggable(value: boolean)
```

Sets the drag effect of the selected text. If this API is not used, the selected text cannot be dragged by default.

This attribute cannot be used together with the [onDragStart](arkts-arkui-common-comp-commonmethod-c.md#ondragstart) event.

If set to **true**, **draggable** must be used in conjunction with CopyOptions. When **copyOptions** is set to **CopyOptions.InApp** or **CopyOptions.LocalDevice**, the selected text becomes draggable and can be copied into a text box.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAttribute-draggable(value: boolean): TextAttribute--><!--Device-TextAttribute-draggable(value: boolean): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Drag effect of the selected text.<br>**true**: The selected text is draggable. **false**: The selected text is not draggable. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

Sets the extended options for the custom menu, including the text content, icon, and callback.

When [disableMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablemenuitems) or [disableSystemServiceMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablesystemservicemenuitems) is used to disable system service menu items in the text selection menu, the disabled menu options will be excluded from the parameter list in the [onCreateMenu](../arkts-apis/arkts-arkui-editmenuoptions-i.md#oncreatemenu) callback of **editMenuOptions**.

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

<!--Device-TextAttribute-editMenuOptions(editMenu: EditMenuOptions): TextAttribute--><!--Device-TextAttribute-editMenuOptions(editMenu: EditMenuOptions): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | Yes | Extended menu options, which are used to customize the extended items of the text selection menu. You can set the text content, icon, and callback method of the extended items, and add custom menu items. |

## ellipsisMode

```TypeScript
ellipsisMode(value: EllipsisMode)
```

Sets the ellipsis position. If this API is not used, the default ellipsis position is at the end of the line (**EllipsisMode.END**).

The **ellipsisMode** attribute must be used together with the **TextOverflow.Ellipsis** value of **overflow** and the **maxLines** attribute. Setting the **ellipsisMode** attribute alone does not take effect.

The **EllipsisMode.START** and **EllipsisMode.CENTER** attributes take effect only when the text in a single line is too long.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-ellipsisMode(value: EllipsisMode): TextAttribute--><!--Device-TextAttribute-ellipsisMode(value: EllipsisMode): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EllipsisMode](../arkts-apis/arkts-arkui-ellipsismode-e.md) | Yes | Ellipsis position. |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

Sets whether to enable automatic spacing between Chinese and Western characters. If this API is not called, automatic spacing between Chinese and Western characters is disabled by default.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextAttribute--><!--Device-TextAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable automatic spacing between Chinese and Western characters.<br>**true** to enable, **false** otherwise. <br>If the value is **undefined**, automatic spacing between Chinese and Western characters is disabled. |

## enableDataDetector

```TypeScript
enableDataDetector(enable: boolean)
```

Sets whether to recognize special text entities, such as phone numbers, websites, email addresses, addresses, and dates. This API is applicable to scenarios that require intelligent recognition and interaction, such as chat messages, comments, and articles. If this API is not called, special text entities are not recognized by default. Special entities are detected when **enableDataDetector** is set to **true**.

The style of detected entities is as follows: the font color is changed to blue, and a blue underline is added.

> **NOTE:** 
> 
> - This API takes effect only when the device has an underlying text detection capability.
> 
> - When [textOverflow](#textoverflow) is set to **TextOverflow.MARQUEE**, text special entity detection is not performed.

<!--RP2--><!--RP2End-->

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-enableDataDetector(enable: boolean): TextAttribute--><!--Device-TextAttribute-enableDataDetector(enable: boolean): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether special text entities can be recognized.<br>The value **true** indicates yes, and **false** indicates no. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

Sets whether to enable haptic feedback. If this API is not called, haptic feedback is enabled by default.

To enable haptic feedback, you must declare the **ohos.permission.VIBRATE** permission under **requestPermissions** in the [module.json5](../../../quick-start/module-configuration-file.md) file of the project.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-TextAttribute-enableHapticFeedback(isEnabled: boolean): TextAttribute--><!--Device-TextAttribute-enableHapticFeedback(isEnabled: boolean): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable haptic feedback.<br>**true** to enable, **false** otherwise. |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

Sets whether to enable entity recognition for selected text. This API only works on devices that provide text recognition. If this API is not called, entity recognition is enabled for selected text by default.

After this feature is enabled, the entities such as email address, phone number, website URL, date, and address in the selection area can be recognized, and the corresponding AI menu items can be displayed in the text selection menu. By default, the AI menu feature is enabled.

When the AI menu feature is enabled, selecting text in the component allows the text selection menu to display corresponding AI menu items, including **url** (opening a link), **email** (creating an email), **phoneNumber** (making a call), **address** (navigating), and **dateTime** (creating a new event) in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

When the AI menu is active, the corresponding menu item is displayed only if the selected range contains exactly one complete AI entity. This menu item does not appear at the same time as the **askAI** menu item in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

This feature is only effective when CopyOptions is set to **CopyOptions.LocalDevice** or **CopyOptions.CrossDevice**.

This attribute is invalid in the cross-node selection scenario of [SelectionContainer](arkts-arkui-selectioncontainer-comp.md). The corresponding AI menu item is not displayed in the text selection menu.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-TextAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextAttribute--><!--Device-TextAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean &#124; undefined | Yes | Whether to enable entity recognition for selected text.<br>**true**: Entity recognition is enabled. **false**: Entity recognition is disabled. Default value: **true** <br>A value of **undefined** is treated as the default value. |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

Adapts the line height to the actual text height for overlapped multi-line text. This API takes effect only when the line height is less than the actual text height. If this API is not set, the line height does not adapt to the actual text height by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextAttribute--><!--Device-TextAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the line height adapts to the actual text height.<br>**true**: Line height adapts to the actual text height. **false**: Line height does not adapt to the actual text height. <br>**undefined**: Line height does not adapt to the actual text height. |

## font

```TypeScript
font(value: Font)
```

Sets the text style, If this API is not called, the default font style is used.

covering the font size, font width, font family, and font style.

It is only effective for the **Text** component, not for its child components.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAttribute-font(value: Font): TextAttribute--><!--Device-TextAttribute-font(value: Font): TextAttribute-End-->

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

<!--Device-TextAttribute-font(fontValue: Font, options?: FontSettingOptions): TextAttribute--><!--Device-TextAttribute-font(fontValue: Font, options?: FontSettingOptions): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontValue | Font | Yes | Sets the text style. |
| options | [FontSettingOptions](../arkts-apis/arkts-arkui-fontsettingoptions-i.md) | No | Font settings.<br>Default value: If this parameter is not set, the default font configuration is used. For details, see **FontSettingOptions**. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color. If this API is not called, the default text color is **'#e6182431'** (dark gray, with 90% opacity). On wearables, the default text color is **'#c5ffffff'** (white, with 77% opacity).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-fontColor(value: ResourceColor): TextAttribute--><!--Device-TextAttribute-fontColor(value: ResourceColor): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color. |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

Sets the font family. If this API is not called, the default font is **'HarmonyOS Sans'**. The default font on wearables is also **'HarmonyOS Sans'**.

> **NOTE:** 
> 
> You can use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to register custom fonts.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-fontFamily(value: string | Resource): TextAttribute--><!--Device-TextAttribute-fontFamily(value: string | Resource): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font family. To specify multiple fonts, separate them with commas (,), and fonts are applied in priority order. Example: **'Arial, HarmonyOS Sans'**. |

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
> When multiple **Text** components are placed in the [Row](arkts-arkui-row-comp.md) container with no specific layout or space
> allocation settings configured, the components are laid out based on the maximum size of the container. To make
> sure the sum of the components' main axis sizes does not exceed the main axis size of the container, you can set
> [layoutWeight](arkts-arkui-common-comp-commonmethod-c.md#layoutweight) or use the [flex layout](arkts-arkui-common-comp.md).
> 
> The system's default font supports the following ligatures: Th, fb, ff, fb, ffb, ffh, ffi, ffk, ffl, fh, fi, fk,
> fl, rf, rt, rv, rx, ry. These ligatures may cause unexpected effects of spans and styled strings. Disabling the
> ligature feature can avoid this issue.
> 
> Text rendering behavior is closely tied to the font file in use. For example, the 8-punctuation compression
> feature requires that the characters in the font file support the ss08 feature. Otherwise, the characters cannot
> be compressed. In the current default system font, the punctuation marks on the right, exclamation marks, commas,
> and question marks do not take effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-TextAttribute-fontFeature(value: string): TextAttribute--><!--Device-TextAttribute-fontFeature(value: string): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Text feature effect. The format is normal &#124; &lt;feature-tag-value&gt;. The format of &lt;feature- tag-value&gt; is &lt;string&gt; [&lt;integer&gt; &#124; on &#124; off]. Multiple values are separated by commas (,). For example, "ss01"on. |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

Sets the text size. If this API is not called, the default font size is 16 fp. The default font size on wearables is 15 fp.

> **NOTE:** 
> 
> When the adaptive font size is used, the **fontSize** settings do not take effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-fontSize(value: number | string | Resource): TextAttribute--><!--Device-TextAttribute-fontSize(value: number | string | Resource): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font size. If **fontSize** is of the number type, the unit fp is used. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported. This parameter cannot be set in percentage. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style. If this API is not called, the default font style is **FontStyle.Normal**. The default font style on wearables is also **FontStyle.Normal**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-fontStyle(value: FontStyle): TextAttribute--><!--Device-TextAttribute-fontStyle(value: FontStyle): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style. |

## fontVariations

```TypeScript
fontVariations(fontVariations: Array<FontVariation>)
```

Sets font variations.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.1.

<!--Device-TextAttribute-fontVariations(fontVariations: Array<FontVariation>): TextAttribute--><!--Device-TextAttribute-fontVariations(fontVariations: Array<FontVariation>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontVariations | Array&lt;[FontVariation](../arkts-apis/arkts-arkui-fontvariation-t.md)&gt; | Yes | Array of font variations, where each member represents a distinct font variation. The **fontVariations** attribute takes precedence over [fontWeight](#fontweight). |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

Sets the font weight. If the value is too large, the text may be clipped depending on the font. If this API is not called, the default font weight is **FontWeight.Normal**. The default font weight on wearables is **FontWeight.Regular**.

It is only effective for the **Text** component, not for its child components.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextAttribute--><!--Device-TextAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight of the text.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**. For the string type, only strings of the number type are supported, for example, **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**. If the value is too large, truncation may occur in different fonts. If the input value exceeds the value range or does not meet the interval requirements, the default value is used. <br>The Resource type is supported since API version 20.<br>**Since:** 20 |

<a id="fontweight-1"></a>

## fontWeight

```TypeScript
fontWeight(weight: number | FontWeight | ResourceStr, options?: FontSettingOptions)
```

Sets the text font weight, with support for font settings. If the value is too large, truncation may occur in different fonts. The [fontVariations](#fontvariations) attribute has a higher priority than this attribute. If both are set, the value of **fontVariations** takes effect. If this API is not called, the default text font weight is **FontWeight.Normal**. The default text font weight on wearables is **FontWeight.Regular**.

It is only effective for the **Text** component, not for its child components.<!--RP4--><!--RP4End-->

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-TextAttribute-fontWeight(weight: number | FontWeight | ResourceStr, options?: FontSettingOptions): TextAttribute--><!--Device-TextAttribute-fontWeight(weight: number | FontWeight | ResourceStr, options?: FontSettingOptions): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| weight | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**. For the string type, only strings of the number type are supported, for example, **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**. If the value is too large, truncation may occur in different fonts. <br>If the input value exceeds the value range, the default value is used. If the input value does not meet the interval requirements, and **enableVariableFontWeight** of **fontWeightConfigs** is set to **true**, the input value is used. If **enableVariableFontWeight** is set to **false**, the default value is used. <br>The Resource type is supported since API version 20.<br>**Since:** 20 |
| options | [FontSettingOptions](../arkts-apis/arkts-arkui-fontsettingoptions-i.md) | No | Font configuration options, which are used to enable the variable font weight adjustment feature. This parameter is required (set **enableVariableFontWeight** to **true**) when the font weight attribute of a variable font needs to be fine-tuned. If this parameter is not passed, the default font configuration is used (variable font weight adjustment is disabled, and only font weights that are multiples of 100 are supported).<br>If **enableVariableFontWeight** is set to **false**, variable font weight adjustment is disabled: If the value of **weight** is a multiple of 100, the font weight is the value of **weight**. If the value of **weight** is not a multiple of 100, the font weight is 400. If **enableVariableFontWeight** is set to **true**, variable font weight adjustment is enabled: The font weight is the value of **weight** when **weight** is set to any integer. |

## halfLeading

```TypeScript
halfLeading(halfLeading: boolean)
```

Sets whether half leading is enabled. Half leading refers to splitting the leading in half and applying it equally to the top and bottom of the line. If this API is not called, half leading is disabled by default.

> **NOTE:** 
> 
> If this parameter and [textVerticalAlign](#textverticalalign) are set at the same time,
> **halfLeading** does not take effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-halfLeading(halfLeading: boolean): TextAttribute--><!--Device-TextAttribute-halfLeading(halfLeading: boolean): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| halfLeading | boolean | Yes | Whether half leading is enabled. Half leading refers to splitting the leading in half and applying it equally to the top and bottom of the line. If this parameter and [textVerticalAlign](#textverticalalign) are set at the same time, **halfLeading** does not take effect. <br>**true**: Half leading is enabled. **false**: Half leading is not enabled. |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(value: TextHeightAdaptivePolicy)
```

Sets the font size adjustment strategy for adaptive text layout. If this API is not called, the default text height adaptation mode is **TextHeightAdaptivePolicy.MAX_LINES_FIRST**.

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

<!--Device-TextAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextAttribute--><!--Device-TextAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md) | Yes | How the adaptive height is determined for the text. |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

Sets whether to add spacing to the first and last lines to avoid text truncation. If this attribute is not set, no spacing is added by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAttribute-includeFontPadding(include: Optional<boolean>): TextAttribute--><!--Device-TextAttribute-includeFontPadding(include: Optional<boolean>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to add spacing to the first and last lines to avoid text truncation.<br>**true**: Spacing is added to the first and last lines. **false**: Spacing is not added to the first and last lines. <br>**undefined**: Spacing is not added to the first and last lines. |

## incrementalUpdatePolicy

```TypeScript
incrementalUpdatePolicy(policy: IncrementalUpdatePolicy | undefined)
```

Sets the incremental update policy for text rendering. If this API is not called, the default value is **IncrementalUpdatePolicy.NONE**.

This API takes effect only when the text content contains a styled string (**StyledString**).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAttribute-incrementalUpdatePolicy(policy: IncrementalUpdatePolicy | undefined): TextAttribute--><!--Device-TextAttribute-incrementalUpdatePolicy(policy: IncrementalUpdatePolicy | undefined): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [IncrementalUpdatePolicy](../arkts-apis/arkts-arkui-incrementalupdatepolicy-e.md) &#124; undefined | Yes | Incremental update policy for text rendering.<br>If this parameter is set to **undefined**, the value **IncrementalUpdatePolicy.NONE** is used. |

## letterSpacing

```TypeScript
letterSpacing(value: number | ResourceStr)
```

Sets the letter spacing for a text style. If this API is not called, the default letter spacing is 0.

If the value specified is a percentage or **0**, the default value is used. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

Negative values compress text. Excessive compression may reduce content area to zero, hiding content.

This setting applies to every character, including those at line endings.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-letterSpacing(value: number | ResourceStr): TextAttribute--><!--Device-TextAttribute-letterSpacing(value: number | ResourceStr): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Letter spacing. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>The Resource type is supported since API version 20.<br>**Since:** 20 |

## lineBreakStrategy

```TypeScript
lineBreakStrategy(strategy: LineBreakStrategy)
```

Sets the line break rule. This attribute takes effect only when [wordBreak](#wordbreak) is not **WordBreak.BREAK_ALL**. Hyphens are not supported. If this API is not called, the default line break rule is **LineBreakStrategy.GREEDY**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextAttribute--><!--Device-TextAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [LineBreakStrategy](../arkts-apis/arkts-arkui-linebreakstrategy-e.md) | Yes | Line break rule. For details, see **LineBreakStrategy**. |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

Set the line height.

If this parameter and [lineHeightMultiple](#lineheightmultiple) are set at the same time and **lineHeightMultiple** is set to a valid value, the setting of **lineHeight** does not take effect and **lineHeightMultiple** is used.

If the value is less than or equal to **0**, the line height is unrestricted and adapts to the font size. When the value is a number, the unit is fp. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

> **NOTE:** 
> 
> If certain characters have significantly taller glyphs than others in the same line, layout anomalies such as
> clipping, overlapping, or misalignment may occur. In this case, adjust component attributes such as height and
> line height to ensure proper layout rendering.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-lineHeight(value: number | string | Resource): TextAttribute--><!--Device-TextAttribute-lineHeight(value: number | string | Resource): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Line height of the text. If the value is of the number type, the unit is fp. |

## lineHeightMultiple

```TypeScript
lineHeightMultiple(value: number | undefined)
```

Sets the line height of text in multiple mode.

The line height equals the input parameter **value** multiplied by **fontHeight**.

> **NOTE:** 
> 
> When **lineHeightMultiple** is set to a valid value and [lineHeight](#lineheight) or
> [lineSpacing](#linespacing) is set at the same time, only
> **lineHeightMultiple** takes effect. If the value of **lineHeightMultiple** is less than 0, it does not take
> effect. In this case, use [lineHeight](#lineheight) and
> [lineSpacing](#linespacing) to set the line height and line spacing.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

<!--Device-TextAttribute-lineHeightMultiple(value: number | undefined): TextAttribute--><!--Device-TextAttribute-lineHeightMultiple(value: number | undefined): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; undefined | Yes | Line height multiple.<br>Value range: [0, +∞) <br>**NOTE:** <br>- Values less than 0 does not take effect. <br>- Value **0** functions the same as **1**, leaving line height unchanged. <br>- Decimal values are supported. <br>- If the value is **undefined**, the default line height is used. |

## lineSpacing

```TypeScript
lineSpacing(value: LengthMetrics)
```

Sets the line spacing for the text. If the value specified is less than 0, the default value **0** is used. If this API is not called, the default line spacing is 0.

If this parameter and [lineHeightMultiple](#lineheightmultiple) are set at the same time and **lineHeightMultiple** is set to a valid value, the setting of **lineSpacing** does not take effect and **lineHeightMultiple** is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-lineSpacing(value: LengthMetrics): TextAttribute--><!--Device-TextAttribute-lineSpacing(value: LengthMetrics): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Line spacing.<br>The value range is [0, +∞). If the value is less than 0, the default value **0** is used. |

<a id="linespacing-1"></a>

## lineSpacing

```TypeScript
lineSpacing(value: LengthMetrics, options?: LineSpacingOptions)
```

Sets the line spacing for the text. When **LineSpacingOptions** is not specified, line spacing is applied above the first line and below the last line by default.

If this parameter and [lineHeightMultiple](#lineheightmultiple) are set at the same time and **lineHeightMultiple** is set to a valid value, the setting of **lineSpacing** does not take effect and **lineHeightMultiple** is used.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAttribute-lineSpacing(value: LengthMetrics, options?: LineSpacingOptions): TextAttribute--><!--Device-TextAttribute-lineSpacing(value: LengthMetrics, options?: LineSpacingOptions): TextAttribute-End-->

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

<!--Device-TextAttribute-marqueeOptions(options: Optional<TextMarqueeOptions>): TextAttribute--><!--Device-TextAttribute-marqueeOptions(options: Optional<TextMarqueeOptions>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextMarqueeOptions](arkts-arkui-text-comp-textmarqueeoptions-i.md)&gt; | Yes | Marquee animation properties such as enable/disable, step size, loop count, and direction. <br>If the value is **undefined**, the default value in [TextMarqueeOptions](arkts-arkui-text-comp-textmarqueeoptions-i.md) is used. |

## maxFontScale

```TypeScript
maxFontScale(scale: number | Resource)
```

Sets the maximum font scale factor for text.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-maxFontScale(scale: number | Resource): TextAttribute--><!--Device-TextAttribute-maxFontScale(scale: number | Resource): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Maximum font scale factor for text.<br>Value range: [1, +∞) <br>**NOTE:** <br>Values less than 1 are treated as **1**. Other invalid values are ineffective by default. |

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

<!--Device-TextAttribute-maxFontSize(value: number | string | Resource): TextAttribute--><!--Device-TextAttribute-maxFontSize(value: number | string | Resource): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Maximum font size. <br>The value must be greater than 0 and greater than or equal to the value of **minFontSize**. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>**NOTE:** <br>If the value is less than or equal to 0 or less than the value of **minFontSize**, the adaptive font size does not take effect. In this case, the value of **fontSize** takes effect. |

## maxLineHeight

```TypeScript
maxLineHeight(value: LengthMetrics | undefined)
```

Sets the maximum line height of text. If the value is less than or equal to 0, the maximum line height is unrestricted. If this API is not called, the maximum line height is unrestricted (the value is **undefined**).

If **maxLineHeight** is less than **minLineHeight**, **maxLineHeight** takes effect using the value of **minLineHeight**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

<!--Device-TextAttribute-maxLineHeight(value: LengthMetrics | undefined): TextAttribute--><!--Device-TextAttribute-maxLineHeight(value: LengthMetrics | undefined): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics &#124; undefined | Yes | Maximum line height of text. Percentage values are not supported.<br>Values less than or equal to 0 are treated as **0**. When the value is set to **0**, the maximum line height is unrestricted. <br>If the value is **undefined**, this parameter does not take effect. |

## maxLines

```TypeScript
maxLines(value: number)
```

Sets the maximum number of lines for text. If this parameter and [minLines](#minlines) are set at the same time, the display range of the minimum number of lines does not exceed the value of **maxLines**.

By default, text is automatically folded. If this attribute is specified, the text will not exceed the specified number of lines. If there is extra text, you can use [textOverflow](#textoverflow) to specify how it is displayed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-maxLines(value: number): TextAttribute--><!--Device-TextAttribute-maxLines(value: number): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of lines of the text.<br>**NOTE:** <br>Value range: [0, *INT32_MAX*] <br>If this parameter is set to **0**, no text content is displayed. |

## minFontScale

```TypeScript
minFontScale(scale: number | Resource)
```

Sets the minimum font scale factor for text.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-minFontScale(scale: number | Resource): TextAttribute--><!--Device-TextAttribute-minFontScale(scale: number | Resource): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Minimum font scale factor for text.<br>Value range: [0, 1] <br>**NOTE:** <br>Values less than 0 are treated as 0, and values greater than 1 are treated as 1. Other invalid values do not take effect by default. |

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

<!--Device-TextAttribute-minFontSize(value: number | string | Resource): TextAttribute--><!--Device-TextAttribute-minFontSize(value: number | string | Resource): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Minimum font size. <br>The value must be greater than **0**. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>**NOTE:** <br>If the value is less than or equal to 0, the adaptive font size does not take effect. In this case, the value of **fontSize** takes effect. |

## minLineHeight

```TypeScript
minLineHeight(value: LengthMetrics | undefined)
```

Sets the minimum line height of text. If the value is less than or equal to 0, the default value **0** is used. If the value of [maxLineHeight](#maxlineheight) is less than that of **minLineHeight**, the value of **minLineHeight** takes effect.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

<!--Device-TextAttribute-minLineHeight(value: LengthMetrics | undefined): TextAttribute--><!--Device-TextAttribute-minLineHeight(value: LengthMetrics | undefined): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics &#124; undefined | Yes | Minimum line height of text. Percentage values are not supported.<br>Values less than or equal to 0 are treated as **0**. <br>If the value is **undefined**, this parameter does not take effect. |

## minLines

```TypeScript
minLines(minLines: Optional<number>)
```

Sets the minimum number of lines for text.

If the actual text height is less than the height for the minimum number of lines, the component uses the height corresponding to the minimum number of lines.

If this parameter and [maxLines](#maxlines) are set at the same time, the display height corresponding to the minimum number of lines does not exceed the height limit corresponding to the maximum number of lines.

If [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) is set for the text, the component height is confined within the [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) bounds.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

<!--Device-TextAttribute-minLines(minLines: Optional<number>): TextAttribute--><!--Device-TextAttribute-minLines(minLines: Optional<number>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minLines | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Minimum number of lines of the text. <br>Value range: [0, *INT32_MAX*]. <br>Values less than 0 are clamped to **0**. <br>If the value is **undefined**, the minimum number of lines is not limited. <br>**NOTE:** <br>If this parameter and [maxLines](#maxlines) are set at the same time, the display height corresponding to the minimum number of lines does not exceed the height limit corresponding to the maximum number of lines. |

## onCopy

```TypeScript
onCopy(callback: (value: string) => void)
```

Called when data is copied to the pasteboard, which is displayed when the text box is long pressed. Currently, only text can be copied.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAttribute-onCopy(callback: (value: string) => void): TextAttribute--><!--Device-TextAttribute-onCopy(callback: (value: string) => void): TextAttribute-End-->

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

<!--Device-TextAttribute-onMarqueeStateChange(callback: Callback<MarqueeState>): TextAttribute--><!--Device-TextAttribute-onMarqueeStateChange(callback: Callback<MarqueeState>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[MarqueeState](arkts-arkui-text-comp-marqueestate-e.md)&gt; | Yes | The callback parameter specifies the state that triggers the callback. The state is defined by the **MarqueeState** enumeration, for example, starting scrolling, completing a scrolling, completing scrolling, or stopping scrolling. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void)
```

Called when the text selection position changes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void): TextAttribute--><!--Device-TextAttribute-onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void): TextAttribute-End-->

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

> **NOTE:** 
> 
> **onWillCopy** and **onCopy** form the **will/did** time sequence mode:
> 
> - **onWillCopy** is triggered before the copy operation is performed. You can return **false** to intercept the copy operation. If **true** is returned, the copy operation is allowed and **onCopy** is triggered.
> 
> - **onCopy** is triggered after the copy operation is complete and cannot be intercepted.
> 
> - The two APIs can be used together. **onWillCopy** is used for interception and control, and **onCopy** is used to obtain the copy result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAttribute-onWillCopy(callback: Callback<string, boolean>): TextAttribute--><!--Device-TextAttribute-onWillCopy(callback: Callback<string, boolean>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; | Yes | The string type indicates the text to be copied.<br>The boolean type indicates whether the text can be copied. The value **true** means yes and **false** means no. |

## optimizeTrailingSpace

```TypeScript
optimizeTrailingSpace(optimize: Optional<boolean>)
```

Sets whether to optimize trailing spaces at line endings during text layout, resolving alignment display issues caused by trailing spaces. If this API is not called, trailing spaces at the end of each line are not optimized by default.

When **Text.optimizeTrailingSpace** is set to **true**:

* Trailing space optimization applies to multi-line text, single-line text, and text and image layouts (particularly noticeable with **TextAlign.Center** or **TextAlign.End**).  
* For text containing only spaces, decoration lines, shadows, and background colors follow the space text display.  
* Leading spaces are not optimized. When text with trailing spaces wraps, trailing spaces on each line are optimized based on component width.

When optimizing pure space text by setting [optimizeTrailingSpace](#optimizetrailingspace) to **true**, you cannot simultaneously set [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [decoration](#decoration), and [textAlign](#textalign) attributes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAttribute-optimizeTrailingSpace(optimize: Optional<boolean>): TextAttribute--><!--Device-TextAttribute-optimizeTrailingSpace(optimize: Optional<boolean>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| optimize | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to optimize trailing spaces.<br>**true** to optimize, **false** otherwise. <br>If the value is **undefined**, trailing spaces are not optimized. |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

Sets whether to enable orphan character optimization during text typesetting. If this attribute is not set, orphan character optimization is disabled by default.

Orphan character optimization improves the text layout by handling the orphan character (the first Chinese character of the last line of a paragraph) more efficiently. When enabled, it adjusts line breaks to avoid orphan characters as much as possible. This feature takes effect only when [wordBreak](#wordbreak) is not **BREAK_ALL** and [locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the first [TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the text to be typeset is either **"zh-Hans"** or **"zh-Hant"**.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextAttribute--><!--Device-TextAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable orphan character optimization for the last line of the paragraph.<br>**true**: Orphan character optimization is enabled. **false**: Orphan character optimization is disabled. <br>When the value is **undefined** or **null**, orphan character optimization is disabled. |

## privacySensitive

```TypeScript
privacySensitive(supported: boolean)
```

Sets whether to enable privacy mode on widgets. If this API is not called, privacy mode is not enabled on widgets by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-TextAttribute-privacySensitive(supported: boolean): TextAttribute--><!--Device-TextAttribute-privacySensitive(supported: boolean): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supported | boolean | Yes | Whether to enable privacy mode on widgets. <br>The value **true** indicates to enable privacy mode on widgets. In privacy mode, the text will be masked with hyphens (-). The value **false** indicates to disable privacy mode on widgets. In privacy mode, the text is displayed properly. <br>**NOTE:** <br>The value **null** means not to enable privacy mode on widgets. <br>Enabling privacy mode requires support from the widget framework. You can use [obscured](arkts-arkui-common-comp-commonmethod-c.md#obscured) to set how the component content is obscured. |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

Sets whether to enable hanging punctuation at line ends. Hanging punctuation is disabled by default if this API is not specified.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAttribute-punctuationOverflow(enabled: Optional<boolean>): TextAttribute--><!--Device-TextAttribute-punctuationOverflow(enabled: Optional<boolean>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable punctuation hanging at the end of a line.<br>**true**: enable punctuation hanging. **false**: disable punctuation hanging. When the value is **undefined** or **null**, hanging punctuation is disabled. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: ResourceColor)
```

Sets the highlight color of the selected text. If opacity is not set or is set to fully opaque, the default opacity is 20%. If this API is not called, the default highlight color of the selected text is '#007DFF' (blue).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TextAttribute-selectedBackgroundColor(color: ResourceColor): TextAttribute--><!--Device-TextAttribute-selectedBackgroundColor(color: ResourceColor): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Highlight color of the selected text. |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

Sets the drag preview style for selected text.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextAttribute--><!--Device-TextAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) &#124; undefined | Yes | Drag preview style for selected text.<br>If this parameter is set to **undefined**, the drag preview follows the theme: white in light mode and black in dark mode. |

## selection

```TypeScript
selection(selectionStart: number, selectionEnd: number)
```

Sets text selection. If this API is not called, no text selection is set by default (both **selectionStart** and **selectionEnd** are set to **-1**).

The selected text is highlighted, with selection handles and the text selection menu displayed.

If [copyOption](#copyoption) is set to **CopyOptions.None**, the setting of the **selection** attribute does not take effect.

If [textOverflow](#textoverflow) is set to **TextOverflow.MARQUEE**, the setting of the **selection** attribute does not take effect.

If the value of **selectionStart** is greater than or equal to that of **selectionEnd**, no text will be selected. The value range is [0, textSize], where **textSize** indicates the maximum number of characters in the text content. If the value is less than 0, the value **0** will be used. If the value is greater than **textSize**, **textSize** will be used.

If the selection range falls within a truncated or invisible area, selection is ignored. When [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) is set to **false**, the text outside the parent component can be selected.

You can obtain the selection range change result through the [onTextSelectionChange](#ontextselectionchange) API.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAttribute-selection(selectionStart: number, selectionEnd: number): TextAttribute--><!--Device-TextAttribute-selection(selectionStart: number, selectionEnd: number): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the selected text.<br>Value range: [0, textSize], where **textSize** indicates the maximum number of characters in the text content. If the value of the input parameter is less than 0, the value **0** is used. If the value of the input parameter is greater than that of **textSize**, the value of **textSize** is used. |
| selectionEnd | number | Yes | End position of the selected text.<br>Value range: [0, textSize], where **textSize** indicates the maximum number of characters in the text content. If the value of the input parameter is less than 0, the value **0** is used. If the value of the input parameter is greater than that of **textSize**, the value of **textSize** is used. |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle)
```

The text can be displayed in the [RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md), [LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md), or [ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md) effect. The priority of **shaderStyle** is higher than that of [fontColor](#fontcolor) and AI recognition. You are advised to use [fontColor](#fontcolor) for solid colors.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAttribute-shaderStyle(shader: ShaderStyle): TextAttribute--><!--Device-TextAttribute-shaderStyle(shader: ShaderStyle): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) | Yes | Shader effect. <br>[RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md), [LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md), or [ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md) is processed based on the input parameters, and the gradient color effect is displayed on the text. <br>**NOTE:** <br>If [RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md) is used and the **center** parameter (from [RadialGradientOptions](arkts-arkui-common-comp-radialgradientoptions-i.md)) is outside the component bounds, setting **repeating** to **true** enhances the gradient effect. |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

Sets the text stroke color.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

<!--Device-TextAttribute-strokeColor(color: Optional<ResourceColor>): TextAttribute--><!--Device-TextAttribute-strokeColor(color: Optional<ResourceColor>): TextAttribute-End-->

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

<!--Device-TextAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextAttribute--><!--Device-TextAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextAttribute-End-->

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

<!--Device-TextAttribute-strokeWidth(width: Optional<LengthMetrics>): TextAttribute--><!--Device-TextAttribute-strokeWidth(width: Optional<LengthMetrics>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Text stroke width. When the unit of **LengthMetrics** is **px**:<br>Values &lt; 0: solid text.<br>Values &gt; 0: outlined text. <br>Default value: **0** (no stroke). |

## tailIndents

```TypeScript
tailIndents(value: Optional<LengthMetrics | Array<LengthMetrics>>)
```

Sets the indent of the text tail. If this API is not called, the default indent of the text tail is 0 fp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAttribute-tailIndents(value: Optional<LengthMetrics | Array<LengthMetrics>>): TextAttribute--><!--Device-TextAttribute-tailIndents(value: Optional<LengthMetrics | Array<LengthMetrics>>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics &#124; Array&lt;LengthMetrics&gt;&gt; | Yes | Tail indentation of each line of text. If a single **LengthMetrics** value is provided, all lines share the same tail indentation. If an array is provided, the *i*th element specifies the tail indentation for the *i*th line. If the number of text lines exceeds the array length, the last element in the array is used for the remaining lines. The value cannot be in percentage.<br>The value must be greater than or equal to 0. If the value is a negative number, the default value is used. |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

Sets the horizontal alignment of the text. If this API is not called, the default horizontal alignment mode of text paragraphs is **TextAlign.Start**. The default value is **TextAlign.Center** on wearables.

When [textOverflow](#textoverflow) is set to **TextOverflow.MARQUEE** and the text is scrollable, the **textAlign** attribute does not take effect.

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

<!--Device-TextAttribute-textAlign(value: TextAlign): TextAttribute--><!--Device-TextAttribute-textAlign(value: TextAlign): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextAlign](../arkts-apis/arkts-arkui-textalign-e.md) | Yes | Horizontal alignment of the text. <br>**NOTE:** <br>When **TextAlign** is set to **TextAlign.JUSTIFY**, the [wordBreak](#wordbreak) attribute must be configured according to the text content. The last line of text aligns to the start horizontally and does not participate in justification. |

## textCase

```TypeScript
textCase(value: TextCase)
```

Sets the text case. If this API is not called, the default text case is **TextCase.Normal**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-textCase(value: TextCase): TextAttribute--><!--Device-TextAttribute-textCase(value: TextCase): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextCase](../arkts-apis/arkts-arkui-textcase-e.md) | Yes | Text case. |

## textContentAlign

```TypeScript
textContentAlign(textContentAlign: Optional<TextContentAlign>)
```

Sets the vertical alignment of the text content area within the component.

This API takes effect only when the height of the text content exceeds the component's height.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-TextAttribute-textContentAlign(textContentAlign: Optional<TextContentAlign>): TextAttribute--><!--Device-TextAttribute-textContentAlign(textContentAlign: Optional<TextContentAlign>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| textContentAlign | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextContentAlign](../arkts-apis/arkts-arkui-textcontentalign-e.md)&gt; | Yes | Vertical alignment of the text content area within the component.<br>If the value is **undefined** or invalid, alignment defaults to **Center**. |

## textDirection

```TypeScript
textDirection(direction: TextDirection | undefined)
```

Specifies the text layout direction. If this attribute is not set, the default text layout direction follows the component layout direction.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAttribute-textDirection(direction: TextDirection | undefined): TextAttribute--><!--Device-TextAttribute-textDirection(direction: TextDirection | undefined): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [TextDirection](../arkts-apis/arkts-arkui-textdirection-e.md) &#124; undefined | Yes | Text layout direction.<br>If this parameter is set to **undefined**, the text layout direction follows the component layout direction as defined by **TextDirection.DEFAULT**. |

## textIndent

```TypeScript
textIndent(value: Length)
```

Sets the indent of the first line text. If this API is not called, the default indent of the first line text is 0.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAttribute-textIndent(value: Length): TextAttribute--><!--Device-TextAttribute-textIndent(value: Length): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Indent of the first line text. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>The value must be greater than or equal to 0. If the value is a negative number, the default value is used. |

## textOverflow

```TypeScript
textOverflow(options: TextOverflowOptions)
```

Sets the display mode for overflowing text.

When [TextOverflowOptions](arkts-arkui-text-comp-textoverflowoptions-i.md) is set to **TextOverflow.None**, **TextOverflow.Clip**, or **TextOverflow.Ellipsis**:

- **TextOverflow.None** or **TextOverflow.Clip**: Text is truncated when it exceeds the maximum number of lines.  
- **TextOverflow.Ellipsis**: An ellipsis (...) is used to represent text overflow.  
- This must be used with [maxLines](#maxlines) for the settings to take effect.  
- Line breaking behavior is controlled by [wordBreak](#wordbreak). By default, it uses  
**WordBreak.BREAK_WORD**, which breaks text by word (for example, English text is broken at word boundaries). To break text by character, set **wordBreak** to **WordBreak.BREAK_ALL**.  
- Line wrapping behavior is governed by [lineBreakStrategy](#linebreakstrategy) which takes  
effect only when [wordBreak](#wordbreak) is not **WordBreak.BREAK_ALL**. Hyphens are not supported.  
- Since API version 11, it is recommended that you configure both [textOverflow](#textoverflow)  
and [wordBreak](#wordbreak) to control truncation behavior. For details, see [Example 4: Setting Text Wrapping and Line Breaking](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#example-4-setting-text-wrapping-and-line-breaking) <!--RP1--><!--RP1End-->.

When **TextOverflowOptions** is set to **TextOverflow.MARQUEE**:

- Text scrolls horizontally within a single line.  
- The [maxLines](#maxlines), [copyOption](#copyoption), and [selection](#selection) attributes do not take effect, and special text entities cannot be recognized (that is, the attributes do not take effect when **enable** in [enableDataDetector](#enabledatadetector) is set to **true**).  
- The [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) attribute of the **Text** component defaults to **true**.  
- [CustomSpan](../arkts-apis/arkts-arkui-customspan-c.md) is not supported in marquee mode.  
- Behavior of [textAlign](#textalign): If the text does not scroll, **textAlign** applies; if  
the text scrolls, **textAlign** is ignored.  
- Since API version 12, **TextOverflow.MARQUEE** is available for the **ImageSpan** component, where the text and  
images are allowed to scroll within a single line.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-TextAttribute-textOverflow(options: TextOverflowOptions): TextAttribute--><!--Device-TextAttribute-textOverflow(options: TextOverflowOptions): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextOverflowOptions](arkts-arkui-text-comp-textoverflowoptions-i.md) | Yes | Configuration object for the display mode of extra-long text. It contains the overflow attribute, which specifies the display behavior such as truncation, ellipsis, or marquee.<br>**Since:** 18 |

## textSelectable

```TypeScript
textSelectable(mode: TextSelectableMode)
```

Sets whether the text is selectable and focusable. If this API is not called, the default text can be selected but cannot be focused (**TextSelectableMode.SELECTABLE_UNFOCUSABLE**).

This attribute must be used in conjunction with [copyOption](#copyoption). If **copyOption** is set to **CopyOptions.None**, the **textSelectable** attribute does not take effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAttribute-textSelectable(mode: TextSelectableMode): TextAttribute--><!--Device-TextAttribute-textSelectable(mode: TextSelectableMode): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [TextSelectableMode](../arkts-apis/arkts-arkui-textselectablemode-e.md) | Yes | Whether the text is selectable and focusable. |

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

<!--Device-TextAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): TextAttribute--><!--Device-TextAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; Array&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt; | Yes | Text shadow effect, which is used to configure the visual effect of the text shadow. **ShadowOptions** contains configuration items such as **radius** (shadow radius), **color** (shadow color), **offsetX** (horizontal offset), and **offsetY** (vertical offset). Intelligent color extraction is not supported for the **type**, **fill**, and **color** fields. Since API version 11, input parameters can be passed in an array to implement multiple text shadows.<br>**Since:** 11 |

## textVerticalAlign

```TypeScript
textVerticalAlign(textVerticalAlign: Optional<TextVerticalAlign>)
```

Sets the vertical alignment of the text. If this API is not called, the default vertical alignment of the text is **TextVerticalAlign.BASELINE**.

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

<!--Device-TextAttribute-textVerticalAlign(textVerticalAlign: Optional<TextVerticalAlign>): TextAttribute--><!--Device-TextAttribute-textVerticalAlign(textVerticalAlign: Optional<TextVerticalAlign>): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| textVerticalAlign | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextVerticalAlign](../arkts-apis/arkts-arkui-textverticalalign-e.md)&gt; | Yes | Vertical alignment of the text.<br>Default value: **TextVerticalAlign.BASELINE** <br>If this parameter is set to **undefined**, the text is aligned with the baseline, which is equivalent to **TextVerticalAlign.BASELINE**. |

## wordBreak

```TypeScript
wordBreak(value: WordBreak)
```

Sets the word break rule. If this API is not called, the default word break rule is **WordBreak.BREAK_WORD**.

By default, when **wordBreak** is not called or is set to **WordBreak.BREAK_WORD**, text is broken by word. (for example, English text is broken at word boundaries).

To break text by character, with the excess part displayed as an ellipsis (...), use **WordBreak.BREAK_ALL** in combination with **{overflow: TextOverflow.Ellipsis}** and **maxLines**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAttribute-wordBreak(value: WordBreak): TextAttribute--><!--Device-TextAttribute-wordBreak(value: WordBreak): TextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [WordBreak](../arkts-apis/arkts-arkui-wordbreak-e.md) | Yes | Word break rule. |
