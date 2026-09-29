# TextPicker properties/events

```TypeScript
declare class TextPickerAttribute extends CommonMethod<TextPickerAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** TextPickerAttribute extends CommonMethod<TextPickerAttribute>

**Since:** 8

<!--Device-unnamed-declare class TextPickerAttribute extends CommonMethod<TextPickerAttribute>--><!--Device-unnamed-declare class TextPickerAttribute extends CommonMethod<TextPickerAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop(value: boolean)
```

Sets whether to enable loop scrolling.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerAttribute-canLoop(value: boolean): TextPickerAttribute--><!--Device-TextPickerAttribute-canLoop(value: boolean): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether circular scrolling is supported.<br>- true: Circular scrolling is supported. <br>- false: Circular scrolling is not supported. <br>Default value: true |

<a id="canloop-1"></a>

## canLoop

```TypeScript
canLoop(isLoop: Optional<boolean>)
```

Sets whether to enable loop scrolling. Compared with [canLoop&lt;sup&gt;10+&lt;/sup&gt;](#canloop), this API supports the **undefined** type for the **isLoop** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-canLoop(isLoop: Optional<boolean>): TextPickerAttribute--><!--Device-TextPickerAttribute-canLoop(isLoop: Optional<boolean>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether cyclic scrolling is supported.<br>- true: Cyclic scrolling is supported. <br>- false: Cyclic scrolling is not supported. <br>Default value: true <br>When the value of isLoop is undefined, the default value is used. |

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight(value: number | string)
```

Sets the height of the picker items.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerAttribute-defaultPickerItemHeight(value: number | string): TextPickerAttribute--><!--Device-TextPickerAttribute-defaultPickerItemHeight(value: number | string): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Height of the selected item.<br>Value range: <br>number type: [0, +∞), in vp. <br>string type: only the string form of a number type value is supported, for example, "56". <br>Default value: 56 vp for the selected item and 36 vp for the unselected item. <br>**Note:** <br>After this parameter is set, the height of both the selected item and the unselected item is the set value. <br>When the value of value is negative, the default value is used. |

<a id="defaultpickeritemheight-1"></a>

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight(height: Optional<number | string>)
```

Sets the height of the picker items. Compared with [defaultPickerItemHeight](#defaultpickeritemheight), this API supports the **undefined** type for the **height** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-defaultPickerItemHeight(height: Optional<number | string>): TextPickerAttribute--><!--Device-TextPickerAttribute-defaultPickerItemHeight(height: Optional<number | string>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; string&gt; | Yes | Height of the selection item.<br>Value range: <br>number type: [0, +∞), in vp. <br>string type: only the string form of a number type value is supported, for example, "56". <br>Default value: 56 vp for the selected item and 36 vp for unselected items. <br>**Note:** <br>1. After this parameter is set, the height of both the selected item and unselected items is the set value. <br>2. When the value of height is undefined, the previous value is retained. |

## defaultTextStyle

```TypeScript
defaultTextStyle(style: TextPickerTextStyle)
```

Sets the text style of the items when the text style change animation during the scrolling process is disabled. This setting takes effect only when [disableTextStyleAnimation](#disabletextstyleanimation) is set to **true**.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextPickerAttribute-defaultTextStyle(style: TextPickerTextStyle): TextPickerAttribute--><!--Device-TextPickerAttribute-defaultTextStyle(style: TextPickerTextStyle): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md) | Yes | Text style of each item when the text style change animation during the sliding process is disabled. <br>Default value: same as the default value of the [Text](arkts-arkui-text-comp.md) component. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

Sets the sensitivity to the digital crown rotation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): TextPickerAttribute--><!--Device-TextPickerAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Crown response sensitivity. <br>Default value: **CrownSensitivity.MEDIUM**, which indicates a moderate response speed. Different sensitivity values affect the correspondence between the crown scrolling speed and the selected item switching speed. For the effect of each enum value, see [CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md). |

## disableTextStyleAnimation

```TypeScript
disableTextStyleAnimation(disabled: boolean)
```

Sets whether to disable the animation effect of text style changes during scrolling.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextPickerAttribute-disableTextStyleAnimation(disabled: boolean): TextPickerAttribute--><!--Device-TextPickerAttribute-disableTextStyleAnimation(disabled: boolean): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| disabled | boolean | Yes | Whether to disable the animation of text style changes during scrolling. <br>- true: Disables the animation of text style changes. <br>- false: Does not disable the animation of text style changes. <br>Default value: false <br>**Note:** <br>When set to true, there is no animation of font size, font weight, or font color changes during scrolling, and the text is displayed in the style set by [defaultTextStyle](#defaulttextstyle). If [defaultTextStyle](#defaulttextstyle) is not set, the default style of the [Text](arkts-arkui-text-comp.md) component is used. When set to false, the system default animation of text style changes during scrolling is used. |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

Sets the text color, font size, and font weight of edge items (the second item above or below the selected item).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerAttribute-disappearTextStyle(value: PickerTextStyle): TextPickerAttribute--><!--Device-TextPickerAttribute-disappearTextStyle(value: PickerTextStyle): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the edge items.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>} <br>} <br>**Note:** If this method is not called to set the style, the default value is used. |

<a id="disappeartextstyle-1"></a>

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

Sets the text color, font size, and font weight of edge items (the second item above or below the selected item). Compared with [disappearTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#disappeartextstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the edge items.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>} <br>} <br>When the value of style is undefined, the default value is used. |

<a id="disappeartextstyle-2"></a>

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

Sets the text color, font size, font weight, maximum font size, minimum font size, and truncation mode of edge items (the second item above or below the selected item). Compared with [disappearTextStyle&lt;sup&gt;18+&lt;/sup&gt;](#disappeartextstyle-1), the style parameter adds support for the [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md) type.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) &#124; [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)&gt; | Yes | Text color, font size, font weight, maximum font size, minimum font size, and overflow handling of the edge items.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>}, <br>minFontSize: 0, <br>maxFontSize: 0, <br>overflow: TextOverflow.Clip <br>} <br>When the value of style is undefined, the default value is used. |

## divider

```TypeScript
divider(value: DividerOptions | null)
```

Sets the divider style. If not explicitly set, the divider uses the default style.

If the sum of **startMargin** and **endMargin** in [DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md) exceeds the component's width, both margins are automatically reset to 0.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerAttribute-divider(value: DividerOptions | null): TextPickerAttribute--><!--Device-TextPickerAttribute-divider(value: DividerOptions | null): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md) &#124; null | Yes |  |

<a id="divider-1"></a>

## divider

```TypeScript
divider(textDivider: Optional<DividerOptions | null>)
```

Sets the divider style. If not explicitly set, the divider uses the default style. Compared with [divider&lt;sup&gt;12+&lt;/sup&gt;](#divider), this API supports the **undefined** type for the **textDivider** parameter.

If the sum of **startMargin** and **endMargin** in [DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md) exceeds the component's width, both margins are automatically reset to 0.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-divider(textDivider: Optional<DividerOptions | null>): TextPickerAttribute--><!--Device-TextPickerAttribute-divider(textDivider: Optional<DividerOptions | null>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| textDivider | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md) &#124; null&gt; | Yes | Default value: <br>{<br>strokeWidth: '2px', <br>startMargin: 0, <br>endMargin: 0, <br>color: '#33000000'<br>} <br>1. When the value of textDivider is undefined, the default value is used. <br>2. When textDivider is set to a valid [DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md), the divider is displayed in the specified style. <br>3. When textDivider is set to null, the divider is not displayed. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

Sets whether to enable haptic feedback.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-enableHapticFeedback(enable: Optional<boolean>): TextPickerAttribute--><!--Device-TextPickerAttribute-enableHapticFeedback(enable: Optional<boolean>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable haptic feedback.<br>- true: Enables haptic feedback. <br>- false: Disables haptic feedback. <br>Default value: true <br>After it is set to true, whether it takes effect depends on whether the system hardware supports it. If the hardware does not support haptic feedback, enabling this feature does not produce a haptic feedback effect, nor does it throw an exception. |

## gradientHeight

```TypeScript
gradientHeight(value: Dimension)
```

Sets the height of the fade effect applied to the top and bottom edges of the content area. If no setting is specified, a default fade effect is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerAttribute-gradientHeight(value: Dimension): TextPickerAttribute--><!--Device-TextPickerAttribute-gradientHeight(value: Dimension): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Fade height of the upper and lower edges of the content area.<br>Default value: 36vp <br>Value range: [0, +∞), percentage supported. <br>**NOTE:** <br>1. When value is set to a percentage, 100% indicates half the height of TextPicker. <br>2. When value is set to 0, the fade effect is not displayed. <br>3. When value is set to a number that exceeds half the height of TextPicker, the default value is used. <br>4. When the value is negative, the default value is used. |

<a id="gradientheight-1"></a>

## gradientHeight

```TypeScript
gradientHeight(height: Optional<Dimension>)
```

Sets the height of the fade effect applied to the top and bottom edges of the content area. If no setting is specified, a default fade effect is used. Compared with [gradientHeight&lt;sup&gt;12+&lt;/sup&gt;](#gradientheight), this API supports the **undefined** type for the **height** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-gradientHeight(height: Optional<Dimension>): TextPickerAttribute--><!--Device-TextPickerAttribute-gradientHeight(height: Optional<Dimension>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt; | Yes | Fade height of the upper and lower edges of the content area.<br>Default value: 36vp <br>Value range: [0, +∞), percentage supported. <br>**Note:** <br>1. When height is set to a percentage, 100% means half the height of the TextPicker. <br>2. When height is set to 0, the fade effect is not displayed. <br>3. When height is set to a number that exceeds half the height of the TextPicker, the default value is used. <br>4. When the value of height is undefined or negative, the default value is used. |

## onChange

```TypeScript
onChange(callback: (value: string[], index: number[]) => void)
```

Triggered when the options settle at the selected item position after the text content of TextPicker is scrolled. It is triggered when the user scrolls the picker and the selected item changes. It cannot be triggered by modifying the two-way bound state variable (such as selected). When a text list or an image-plus-text list is displayed, the value is the text value of the selected item. When an image list is displayed, the value is empty.

This callback is triggered only after the scroll animation completes. To obtain real-time index changes, use [onEnterSelectedArea](#onenterselectedarea) instead.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerAttribute-onChange(callback: (value: string | string[], index: number | number[]) => void): TextPickerAttribute--><!--Device-TextPickerAttribute-onChange(callback: (value: string | string[], index: number | number[]) => void): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: string[], index: number[]) =&gt; void | Yes |  |

<a id="onchange-1"></a>

## onChange

```TypeScript
onChange(callback: Optional<OnTextPickerChangeCallback>)
```

Triggered when the options settle at the selected item position after the text content of TextPicker is scrolled. It is triggered when the user scrolls the picker and the selected item changes. It cannot be triggered by modifying the two-way bound state variable (such as selected). When a text list or an image-plus-text list is displayed, the value is the text value of the selected item. When an image list is displayed, the value is empty. Compared with [onChange](#onchange), the callback parameter adds support for the undefined type.

This callback is triggered only after the scroll animation completes. To obtain real-time index changes, use [onEnterSelectedArea](#onenterselectedarea) instead.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-onChange(callback: Optional<OnTextPickerChangeCallback>): TextPickerAttribute--><!--Device-TextPickerAttribute-onChange(callback: Optional<OnTextPickerChangeCallback>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnTextPickerChangeCallback](arkts-arkui-textpicker-comp-ontextpickerchangecallback-t.md)&gt; | Yes | Callback invoked when the text content of the TextPicker is selected by swiping.<br>If the value of callback is undefined, the callback is not used. |

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea(callback: TextPickerEnterSelectedAreaCallback)
```

Triggered when an option enters the selection zone during text picker scrolling (when the scroll distance exceeds half the selected item's height).

> **NOTE:** 
> 
> - The difference from the [onChange](#onchange)event is that this event is triggered earlier than the [onChange](#onchange)event. onEnterSelectedArea is triggered when an option enters the selected area during sliding, and is suitable for obtaining index value changes in real time, applicable to scenarios that require a quick response to user sliding. onChange is triggered after sliding ends and the selected item is settled, and is suitable for obtaining the finally confirmed selected value, applicable to scenarios that require obtaining the user's final selection.
> 
> - The difference from the [onScrollStop](#onscrollstop) event is that onEnterSelectedArea focuses on the logical state of an option entering the selected area, while onScrollStop focuses on the complete stop of the scrolling behavior. Use onEnterSelectedArea when an earlier response to index changes is required, and use [onScrollStop](#onscrollstop) when confirmation that scrolling has completely stopped is required.
> 
> - In multi-column linkage scenarios, using this callback is not recommended. This callback identifies the node at which an option enters the divider area during sliding. The options that change accordingly do not involve sliding, so in the callback return value, only the value of the currently sliding column changes normally, while the values of the other non-sliding columns remain unchanged.
> 
> - This API does not support being called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-onEnterSelectedArea(callback: TextPickerEnterSelectedAreaCallback): TextPickerAttribute--><!--Device-TextPickerAttribute-onEnterSelectedArea(callback: TextPickerEnterSelectedAreaCallback): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpicker-comp-textpickerenterselectedareacallback-t.md) | Yes | Callback invoked when an option enters the divider area during sliding of the TextPicker. Callback signature: (value: string &#124; string[], index: number &#124; number[]) =&gt; void, where value is the text of the currently selected item, and index is the index of the currently selected item (starting from 0). |

## onScrollStop

```TypeScript
onScrollStop(callback: TextPickerScrollStopCallback)
```

Triggered when the scrolling in the text picker stops.

If the scrolling is initiated by a gesture, this event is triggered when the finger is lifted from the screen and the scrolling stops.

> **NOTE:** 
> 
> - The difference from the [onEnterSelectedArea](#onenterselectedarea) event is that onScrollStop focuses on the complete stop of the scrolling behavior, while onEnterSelectedArea focuses on the logical state of an option entering the selected area. onEnterSelectedArea responds to index changes earlier and is suitable for real-time feedback scenarios. It is recommended to use [onEnterSelectedArea](#onenterselectedarea). If you need to confirm that the scrolling behavior has completely stopped, use onScrollStop.
> 
> - Since API version 20, this API supports being called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TextPickerAttribute-onScrollStop(callback: TextPickerScrollStopCallback): TextPickerAttribute--><!--Device-TextPickerAttribute-onScrollStop(callback: TextPickerScrollStopCallback): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [TextPickerScrollStopCallback](arkts-arkui-textpicker-comp-textpickerscrollstopcallback-t.md) | Yes | Triggered when the option column of the text picker stops scrolling. Callback signature: (value: string &#124; string[], index: number &#124; number[]) =&gt; void, where value is the text of the currently selected item, and index is the index of the currently selected item (starting from 0). |

<a id="onscrollstop-1"></a>

## onScrollStop

```TypeScript
onScrollStop(callback: Optional<TextPickerScrollStopCallback>)
```

Triggered when the scrolling in the text picker stops. Compared with [onScrollStop&lt;sup&gt;14+&lt;/sup&gt;](#onscrollstop), this API supports the **undefined** type for the **callback** parameter.

If the scrolling is initiated by a gesture, this event is triggered when the finger is lifted from the screen and the scrolling stops.

> **NOTE:** 
> 
> - The difference from the [onEnterSelectedArea](#onenterselectedarea) event is that onScrollStop focuses on the complete stop of the scrolling behavior, while onEnterSelectedArea focuses on the logical state of an option entering the selected area. onEnterSelectedArea responds to index changes earlier and is suitable for real-time feedback scenarios. It is recommended to use [onEnterSelectedArea](#onenterselectedarea). If you need to confirm that the scrolling behavior has completely stopped, use onScrollStop.
> 
> - Since API version 20, this API supports being called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-onScrollStop(callback: Optional<TextPickerScrollStopCallback>): TextPickerAttribute--><!--Device-TextPickerAttribute-onScrollStop(callback: Optional<TextPickerScrollStopCallback>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextPickerScrollStopCallback](arkts-arkui-textpicker-comp-textpickerscrollstopcallback-t.md)&gt; | Yes | Callback invoked when the option column of the text picker stops scrolling.<br>When the value of callback is undefined, the callback is not used. |

## selectedBackgroundStyle

```TypeScript
selectedBackgroundStyle(style: Optional<PickerBackgroundStyle>)
```

Sets the background style of selected items.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerAttribute-selectedBackgroundStyle(style: Optional<PickerBackgroundStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedBackgroundStyle(style: Optional<PickerBackgroundStyle>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerBackgroundStyle](arkts-arkui-textpicker-comp-pickerbackgroundstyle-i.md)&gt; | Yes | Color and border radius of the background of the selected item. In multi-column mode, the color and border radius of the background of the selected item are set for all columns at the same time.<br>Default value: <br>{<br>color: $r('sys.color.comp_background_tertiary'), <br>borderRadius: $r('sys.float.corner_radius_level12') <br>} |

## selectedIndex

```TypeScript
selectedIndex(value: number[])
```

Sets the index of the selected item or items in the data list. This setting takes precedence over the **value** property in [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md). Use the number type for single-column pickers. Use the number[] type for multi-column pickers.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerAttribute-selectedIndex(value: number | number[]): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedIndex(value: number | number[]): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number[] | Yes | Index of the selected item in the data selection list. The index starts from 0.<br>Default value: **0** <br>If the value is negative or exceeds the maximum index of the data selection list, the default value is used. <br> |

<a id="selectedindex-1"></a>

## selectedIndex

```TypeScript
selectedIndex(index: Optional<number[]>)
```

Sets the index of the selected item or items in the data list. This setting takes precedence over the **value** property in [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md). Use the number type for single-column pickers. Use the number[] type for multi-column pickers. Compared with [selectedIndex&lt;sup&gt;10+&lt;/sup&gt;](#selectedindex), this API supports the **undefined** type for the **index** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-selectedIndex(index: Optional<number | number[]>): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedIndex(index: Optional<number | number[]>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number[]&gt; | Yes | Index of the selected item in the data selection list. The index starts from 0. <br>Default value: **0** <br>If the value of **index** is **undefined**, the value of **selected** in [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md) is used. <br>If the value of **index** is a negative number or exceeds the maximum index value of the data selection list, the default value is used. <br> |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

Sets the text color, font size, and font weight of the selected item.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerAttribute-selectedTextStyle(value: PickerTextStyle): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedTextStyle(value: PickerTextStyle): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the selected item.<br>Default value: <br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>} <br>} <br>**Note:** If this method is not called to set the style, the default value is used. |

<a id="selectedtextstyle-1"></a>

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle>)
```

Sets the text color, font size, and font weight of the selected item. Compared with [selectedTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#selectedtextstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the selected item.<br>Default value: <br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>} <br>} <br>When the value of style is undefined, the default value is used. |

<a id="selectedtextstyle-2"></a>

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

Sets the text color, font size, font weight, maximum font size, minimum font size, and truncation mode of the selected item. Compared with [selectedTextStyle&lt;sup&gt;18+&lt;/sup&gt;](#selectedtextstyle-1), the style parameter adds support for the [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md) type.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) &#124; [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)&gt; | Yes | Text color, font size, font weight, maximum font size, minimum font size, and truncation mode of the selected item's overlong text.<br>Default value: <br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>}, <br>minFontSize: 0, <br>maxFontSize: 0, <br>overflow: TextOverflow.Clip <br>} <br>When the value of style is undefined, the default value is used. |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

Sets the text color, font size, and font weight of candidate items (the first item immediately above or below the selected item).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerAttribute-textStyle(value: PickerTextStyle): TextPickerAttribute--><!--Device-TextPickerAttribute-textStyle(value: PickerTextStyle): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the options.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} <br>**Note:** When this method is not called to set the style, the default value is used. |

<a id="textstyle-1"></a>

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

Sets the text color, font size, and font weight of candidate items (the first item immediately above or below the selected item). Compared with [textStyle&lt;sup&gt;10+&lt;/sup&gt;](#textstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerAttribute-textStyle(style: Optional<PickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-textStyle(style: Optional<PickerTextStyle>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the options to be selected.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} <br>When the value of style is undefined, the default value is used. |

<a id="textstyle-2"></a>

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>)
```

Sets the text color, font size, font weight, maximum font size, minimum font size, and truncation mode of candidate items (the first item immediately above or below the selected item). Compared with [textStyle&lt;sup&gt;18+&lt;/sup&gt;](#textstyle-1), the style parameter adds support for the [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md) type.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerAttribute-textStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute--><!--Device-TextPickerAttribute-textStyle(style: Optional<PickerTextStyle | TextPickerTextStyle>): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) &#124; [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)&gt; | Yes | Text color, font size, font weight, maximum font size, minimum font size, and truncation mode of the text to be selected.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>}, <br>minFontSize: 0, <br>maxFontSize: 0, <br>overflow: TextOverflow.Clip <br>} <br>When the value of style is undefined, the default value is used. |

## onAccept

```TypeScript
onAccept(callback: (value: string, index: number) => void)
```

Triggered when the OK button in the dialog box is clicked. This event can be triggered only in the [text picker dialog box](arkts-arkui-textpicker-comp.md).

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 10. This API has been completely
> removed, and there is no substitute API.

**Since:** 8

**Deprecated since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-TextPickerAttribute-onAccept(callback: (value: string, index: number) => void): TextPickerAttribute--><!--Device-TextPickerAttribute-onAccept(callback: (value: string, index: number) => void): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: string, index: number) =&gt; void | Yes |  |

## onCancel

```TypeScript
onCancel(callback: () => void)
```

Triggered when the cancel button in the dialog box is clicked. This event can be triggered only in the [text picker dialog box](arkts-arkui-textpicker-comp.md).

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 10. This API has been completely
> removed. There is no substitute API.

**Since:** 8

**Deprecated since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-TextPickerAttribute-onCancel(callback: () => void): TextPickerAttribute--><!--Device-TextPickerAttribute-onCancel(callback: () => void): TextPickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | () =&gt; void | Yes | Callback invoked when the cancel button in the dialog box is clicked. |
