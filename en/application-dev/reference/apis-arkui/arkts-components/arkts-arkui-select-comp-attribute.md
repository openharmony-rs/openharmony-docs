# Select properties/events

```TypeScript
declare class SelectAttribute extends CommonMethod<SelectAttribute>
```

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** SelectAttribute extends CommonMethod<SelectAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowModifier

```TypeScript
arrowModifier(modifier: Optional<SymbolGlyphModifier>)
```

Creates an arrow modifier to customize the drop-down arrow icon style of the **Select** button. After **arrowModifier** is applied, the drop-down arrow icon style of the **Select** button will be completely customized by the developer.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)&gt; | Yes | Arrow modifier to apply to the **Select** button for customizing the drop-down arrow icon style. |

## arrowPosition

```TypeScript
arrowPosition(value: ArrowPosition)
```

Sets the alignment between the text and arrow of an option.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ArrowPosition](arkts-arkui-select-comp-arrowposition-e.md) | Yes | Alignment between the text and arrow of an option.<br>Default value: **ArrowPosition.END** |

<a id="arrowposition-1"></a>

## arrowPosition

```TypeScript
arrowPosition(position: Optional<ArrowPosition>)
```

Sets the alignment between the text and arrow of an option. Compared with [arrowPosition](#arrowposition), this API supports the **undefined** type for the **position** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ArrowPosition](arkts-arkui-select-comp-arrowposition-e.md)&gt; | Yes | Alignment between the text and arrow of an option.<br>If **position** is set to **undefined**, the default value **ArrowPosition.END** is used. |

## avoidance

```TypeScript
avoidance(mode: AvoidanceMode)
```

Sets the avoidance mode for the drop-down menu.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AvoidanceMode](arkts-arkui-select-comp-avoidancemode-e.md) | Yes | Avoidance mode for the drop-down menu.<br>Default value: **AvoidanceMode.COVER_TARGET** |

## controlSize

```TypeScript
controlSize(value: ControlSize)
```

Sets the size of the **Select** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ControlSize](arkts-arkui-button-comp-controlsize-e.md) | Yes | Size of the **Select** component.<br>Default value: **ControlSize.NORMAL** |

<a id="controlsize-1"></a>

## controlSize

```TypeScript
controlSize(size: Optional<ControlSize>)
```

Sets the size of the **Select** component. Compared with [controlSize](#controlsize)&lt;sup&gt;12+&lt;/sup&gt;, this API supports the **undefined** type for **size** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ControlSize](arkts-arkui-button-comp-controlsize-e.md)&gt; | Yes | Size of the **Select** component.<br>If **size** is set to **undefined**, the default value **ControlSize.NORMAL** is used. |

## divider

```TypeScript
divider(options: Optional<DividerOptions> | null)
```

Sets the divider style. If this attribute is not set, the divider is displayed based on the default value.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[DividerOptions](arkts-arkui-textpicker-comp-divideroptions-i.md)&gt; &#124; null | Yes | Divider options.<br>1. If **DividerOptions** is set, the divider is displayed in the configured style.<br>Default value:<br>{<br>strokeWidth: '1px' , <br>color: '#33182431'<br>}<br>2. If this parameter is set to **null**, the divider is not displayed.<br>3. If the value of**strokeWidth** is too larger, the divider may overlap the text. The divider extends both upwards and downwards from the bottom of each item.<br>4. The default values for **startMargin** and **endMargin** are consistent with the style of the divider when the **divider** attribute is not set. If the sum of **startMargin** and **endMargin** is equal to the value of **optionWidth**, the divider is not displayed. If the sum of **startMargin** and **endMargin** exceeds the value of **optionWidth**, the divider line is displayed in the default style. |

## dividerStyle

```TypeScript
dividerStyle(style: Optional<DividerStyleOptions>)
```

Sets the divider style. If this attribute is not set, the divider is displayed based on the default value. This attribute cannot be used together with the **divider** attribute. The last one called will take effect.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[DividerStyleOptions](../arkts-apis/arkts-arkui-dividerstyleoptions-i.md)&gt; | Yes | Divider options.<br>1. If **DividerOptions** is set, the divider is displayed in the configured style.<br>Default value:<br>{<br>strokeWidth: '1px' , <br>color: '#33182431'<br>}<br>2. If this parameter is set to **null** or **undefined**, the default divider is displayed.<br>3. When **mode** is set to **FLOAT_ABOVE_MENU**, be careful with the **strokeWidth** settings to avoid covering text. The divider extends both upwards and downwards from the bottom of each item. When **mode** is **EMBEDDED_IN_MENU**, the divider expands to fill its own space within the menu.<br>4. The default values for **startMargin** and **endMargin** are consistent with the style of the divider when the **divider** attribute is not set. If the sum of **startMargin** and **endMargin** is equal to the value of **optionWidth**, the divider is not displayed. If the sum of **startMargin** and **endMargin** exceeds the value of **optionWidth**, the divider line is displayed in the default style. |

## font

```TypeScript
font(value: Font)
```

Sets the text style of the drop-down button. When **size** is set to **0**, the text is not displayed. When **size** is set to a negative value, the text is displayed at its default size.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text style of the drop-down list button.<br>For API versions 11 and earlier, the default value is as follows:<br>{<br>size: `$r('sys.float.ohos_id_text_size_button1')`,<br>weight: FontWeight.Medium<br>} <br>Since API version 12: The default value of **size** is **$r('sys.float.ohos_id_text_size_button2')** in the case of **controlSize.SMALL** and **$r('sys.float.ohos_id_text_size_button1')** in other cases. |

<a id="font-1"></a>

## font

```TypeScript
font(selectFont: Optional<Font>)
```

Sets the text style of the drop-down button. When **size** is set to **0**, the text is not displayed. When **size** is set to a negative value, the text is displayed at its default size. Compared with [font](#font), this API supports the **undefined** type for the **selectFont** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | Yes | Text style of the drop-down list button.<br>If **controlSize** is set to **controlSize.SMALL**, the default value of **size** is **$r('sys.float.ohos_id_text_size_button2')**. Otherwise, the default value is **$r('sys.float.ohos_id_text_size_button1')**.<br>If **selectFont** is set to **undefined**, the default font style is used. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color of the drop-down button.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the drop-down button.<br>Default value: **$r('sys.color.ohos_id_color_text_primary')** with the opacity of **$r('sys.color.ohos_id_alpha_content_primary')** |

<a id="fontcolor-1"></a>

## fontColor

```TypeScript
fontColor(resColor: Optional<ResourceColor>)
```

Sets the font color of the drop-down button. Compared with [fontColor](#fontcolor), this API supports the **undefined** type for the **resColor** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Font color of the drop-down button.<br>When **resColor** is set to **undefined**, the default value is a blend of **$r('sys.color.ohos_id_color_text_primary')** with the opacity of **$r('sys.color.ohos_id_alpha_content_primary')**.<br>If **value** is set to **undefined**, the previous value is retained. |

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode(mode: Optional<MenuKeyboardAvoidMode>)
```

Sets whether the drop-down menu avoids the soft keyboard. If this API is not used, the drop-down menu avoids the soft keyboard by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[MenuKeyboardAvoidMode](arkts-arkui-common-comp-menukeyboardavoidmode-e.md)&gt; | Yes | Whether the drop-down menu avoids the soft keyboard. If the value is **undefined**, it is treated as **MenuKeyboardAvoidMode.NONE**. |

## menuAlign

```TypeScript
menuAlign(alignType: MenuAlignType, offset?: Offset)
```

Sets the alignment between the drop-down button and the drop-down menu.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignType | [MenuAlignType](arkts-arkui-select-comp-menualigntype-e.md) | Yes | Alignment type.<br>Default value: **MenuAlignType.START** |
| offset | Offset | No | Offset of the drop-down menu relative to the drop-down button after alignment based on the alignment type.<br> Default value: **{dx: 0, dy: 0}** |

<a id="menualign-1"></a>

## menuAlign

```TypeScript
menuAlign(alignType: Optional<MenuAlignType>, offset?: Offset)
```

Sets the alignment between the drop-down button and the drop-down menu. Compared with [menuAlign](#menualign)&lt;sup&gt;10+&lt;/sup&gt;, this API supports the **undefined** type for the **alignType** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[MenuAlignType](arkts-arkui-select-comp-menualigntype-e.md)&gt; | Yes | Alignment type.<br>If **alignType** is set to **undefined**, the default value **MenuAlignType.START** is used. |
| offset | Offset | No | Offset of the drop-down menu relative to the drop-down button after alignment based on the alignment type.<br> Default value: **{dx: 0, dy: 0}** |

## menuBackgroundBlurStyle

```TypeScript
menuBackgroundBlurStyle(value: BlurStyle)
```

Sets the background blur style of the drop-down menu.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md) | Yes | Background blur style of the drop-down menu.<br>Default value: **BlurStyle.COMPONENT_ULTRA_THICK** |

<a id="menubackgroundblurstyle-1"></a>

## menuBackgroundBlurStyle

```TypeScript
menuBackgroundBlurStyle(style: Optional<BlurStyle>)
```

Sets the background blur style of the drop-down menu. Compared with [menuBackgroundBlurStyle](#menubackgroundblurstyle)&lt;sup&gt;11+&lt;/sup&gt;, this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)&gt; | Yes | Background blur style of the drop-down menu.<br>If **style** is set to **undefined**, the default value **BlurStyle.COMPONENT_ULTRA_THICK** is used. |

## menuBackgroundBlurStyleOptions

```TypeScript
menuBackgroundBlurStyleOptions(blurStyle: Optional<BackgroundBlurStyleOptions>)
```

Defines the select menu's background blur style with options

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurStyle | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)&gt; | Yes | The background blur style of menu. |

## menuBackgroundColor

```TypeScript
menuBackgroundColor(value: ResourceColor)
```

Sets the background color of the drop-down menu.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the drop-down menu.<br>Default value:<br>Versions earlier than API version 11: **$r('sys.color.ohos_id_color_card_bg')**<br>Since API version 11: **Color.Transparent** |

<a id="menubackgroundcolor-1"></a>

## menuBackgroundColor

```TypeScript
menuBackgroundColor(resColor: Optional<ResourceColor>)
```

Sets the background color of the drop-down menu. Compared with [menuBackgroundColor](#menubackgroundcolor)&lt;sup&gt;11+&lt;/sup&gt;, this API supports the **undefined** type for the **resColor** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Background color of the drop-down menu.<br>If **resColor** is set to **undefined**, the default value **Color.Transparent** is used. |

## menuBackgroundEffect

```TypeScript
menuBackgroundEffect(effect: Optional<BackgroundEffectOptions>)
```

Defines the select menu's background effect with options

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)&gt; | Yes | Background effect, including saturation, brightness, and color.<br>The configuration does not take effect when it is undefined. |

## menuItemContentModifier

```TypeScript
menuItemContentModifier(modifier: ContentModifier<MenuItemConfiguration>)
```

Creates a content modifier for the drop-down menu. After **menuItemContentModifier** is applied, the drop-down menu content will be completely customized by the developer, and the **Select** component's attributes, including the divider, option color, and drop-down menu font color, will not take effect.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[MenuItemConfiguration](arkts-arkui-select-comp-menuitemconfiguration-i.md)&gt; | Yes | Content modifier to apply to the drop-down menu.<br> **modifier**: content modifier. You need a custom class to implement the **ContentModifier** API. |

<a id="menuitemcontentmodifier-1"></a>

## menuItemContentModifier

```TypeScript
menuItemContentModifier(modifier: Optional<ContentModifier<MenuItemConfiguration>>)
```

Creates a content modifier for the drop-down menu. Compared with [menuItemContentModifier](#menuitemcontentmodifier) &lt;sup&gt;12+&lt;/sup&gt;, this API supports the **undefined** type for **modifier** parameter. After **menuItemContentModifier** is applied, the drop-down menu content will be completely customized by the developer, and the **Select** component's attributes, including the divider, option color, and drop-down menu font color, will not take effect.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[MenuItemConfiguration](arkts-arkui-select-comp-menuitemconfiguration-i.md)&gt;&gt; | Yes | Content modifier to apply to the drop-down menu.<br>**modifier**: content modifier. You need a custom class to implement the **ContentModifier** API.<br> If **modifier** is set to **undefined**, no content modifier is used. |

## menuOutline

```TypeScript
menuOutline(outline: MenuOutlineOptions)
```

Sets the outline style for the drop-down menu.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outline | [MenuOutlineOptions](arkts-arkui-select-comp-menuoutlineoptions-i.md) | Yes | Outline style of the drop-down menu. |

## menuSystemMaterial

```TypeScript
menuSystemMaterial(material: Optional<SystemUiMaterial>)
```

Set system-styled materials for select's menu. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of select's menu.

Device Behavior Differences:The effect of the same material may vary across different devices depending on their computing power.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| material | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)&gt; | Yes | The select's menu material, undefined means retaining the original visual style of the select's menu. |

## minKeyboardAvoidDistance

```TypeScript
minKeyboardAvoidDistance(distance: Optional<LengthMetrics>)
```

Sets the minimum distance for the **Select** component to avoid the soft keyboard. If this API is not used, the minimum distance is 8 vp by default. This API is valid only when [keyboardAvoidMode](#keyboardavoidmode) is set to avoid the soft keyboard.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| distance | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Sets the minimum distance for the drop-down menu to avoid the soft keyboard. If the value is set to a negative number or **undefined**, the value 8 vp will be used. |

## onSelect

```TypeScript
onSelect(callback: (index: number, value: string) => void)
```

Triggered when a drop-down menu option is selected.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (index: number, value: string) =&gt; void | Yes |  |

<a id="onselect-1"></a>

## onSelect

```TypeScript
onSelect(callback: Optional<OnSelectCallback>)
```

Triggered when a drop-down menu option is selected. Compared with [onSelect](#onselect), this API supports the **undefined** type for the **callback** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnSelectCallback](arkts-arkui-select-comp-onselectcallback-t.md)&gt; | Yes | Callback invoked when a drop-down menu option is selected.<br>If **callback** is set to **undefined**, the callback function is not used. |

## optionBgColor

```TypeScript
optionBgColor(value: ResourceColor)
```

Sets the background color of options in the drop-down menu.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of options in the drop-down menu.<br>Default value:<br>Versions earlier than API version 11: **Color.White**<br>Since API version 11: **Color.Transparent** |

<a id="optionbgcolor-1"></a>

## optionBgColor

```TypeScript
optionBgColor(resColor: Optional<ResourceColor>)
```

Sets the background color of options in the drop-down menu. Compared with [optionBgColor](#optionbgcolor), this API supports the **undefined** type for the **resColor** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Background color of options in the drop-down menu.<br>When the value of resColor is undefined, the background color of the drop-down menu item is Color.White. |

## optionFont

```TypeScript
optionFont(value: Font)
```

Sets the text font of options in the drop-down menu. When **size** is set to **0**, the text is not displayed. When **size** is set to a negative value, the text is displayed at its default size.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text font of options in the drop-down menu.<br>Default value:<br>{<br>size: $r('sys.float.ohos_id_text_size_body1'),<br>weight: FontWeight.Regular<br>} |

<a id="optionfont-1"></a>

## optionFont

```TypeScript
optionFont(selectFont: Optional<Font>)
```

Sets the text font of options in the drop-down menu. When **size** is set to **0**, the text is not displayed. When **size** is set to a negative value, the text is displayed at its default size.

Compared with [optionFont](#optionfont), this API supports the **undefined** type for the **selectFont** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | Yes | Text font of options in the drop-down menu.<br>If **selectFont** is set to **undefined**, the default value is used:<br>{<br>size: $r('sys.float.ohos_id_text_size_body1'),<br>weight: FontWeight.Regular<br>} |

## optionFontColor

```TypeScript
optionFontColor(value: ResourceColor)
```

Sets the font color of options in the drop-down menu.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of options in the drop-down menu.<br>Default value: **$r('sys.color.ohos_id_color_text_primary')** |

<a id="optionfontcolor-1"></a>

## optionFontColor

```TypeScript
optionFontColor(resColor: Optional<ResourceColor>)
```

Sets the font color of options in the drop-down menu. Compared with [optionFontColor](#optionfontcolor), this API supports the **undefined** type for the **resColor** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Font color of options in the drop-down menu.<br>If **resColor** is set to **undefined**, the default value **$r('sys.color.ohos_id_color_text_primary')** is used. |

## optionHeight

```TypeScript
optionHeight(value: Dimension)
```

Sets the maximum height for the drop-down menu. Percentage values are not supported. The default maximum height is 80% of the available screen height, and any custom maximum height setting must not exceed this limit.

This attribute has no effect when set to abnormal values or zero.

If the actual height of all drop-down menu options is less than the set height, the menu will automatically adjust to the actual content height.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Maximum height of the drop-down menu. |

<a id="optionheight-1"></a>

## optionHeight

```TypeScript
optionHeight(height: Optional<Dimension>)
```

Sets the maximum height for the drop-down menu. Percentage values are not supported. The default maximum height is 80% of the available screen height, and any custom maximum height setting must not exceed this limit. Compared with [optionHeight](#optionheight)&lt;sup&gt;11+&lt;/sup&gt;, this API supports the **undefined** type for the **height** parameter.

This attribute has no effect when set to abnormal values or zero.

If the actual height of all drop-down menu options is less than the set height, the menu will automatically adjust to the actual content height.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt; | Yes | Maximum height of the drop-down menu.<br>If **height** is set to **undefined**, the default value, which is 80% of the available screen height, is used. |

## optionTextModifier

```TypeScript
optionTextModifier(modifier: Optional<TextModifier>)
```

Creates an option text modifier to customize the text style of unselected options in the drop-down menu. After **optionTextModifier** is applied, the unselected option text style will be completely customized by the developer.

If both [optionFont](#optionfont) and **Font** of **optionTextModifier** are set, [optionFont](#optionfont) takes precedence. Any unspecified attributes in **optionFont** will use default values.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;TextModifier&gt; | Yes | Option text modifier to apply to the **Select** component for customizing the text style of unselected options in the drop-down menu. |

## optionWidth

```TypeScript
optionWidth(value: Dimension | OptionWidthMode)
```

Sets the width for the drop-down menu option. Percentage values are not supported. **OptionWidthMode** specifies whether to inherit the width of the drop-down button.

If an invalid value or a value less than the minimum width of 56 vp is set, the attribute has no effect. In this case, the option width uses the default value, which is the width of two columns.

The **Select** component maintains 16 vp spacing from both left and right screen edges by default. This creates a 32 vp total horizontal margin (16 vp × 2). To prevent horizontal shifting when the drop-down menu is displayed, set the width of the component itself and its menu options to a value less than or equal to **calc(100% - 32 vp)**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [OptionWidthMode](../arkts-apis/arkts-arkui-optionwidthmode-e.md) | Yes | Width of the drop-down menu option. |

<a id="optionwidth-1"></a>

## optionWidth

```TypeScript
optionWidth(width: Optional<Dimension | OptionWidthMode> )
```

Sets the width for the drop-down menu option. Percentage values are not supported. **OptionWidthMode** specifies whether to inherit the width of the drop-down button. Compared with [optionWidth](#optionwidth)&lt;sup&gt;11+&lt;/sup&gt;, this API supports the **undefined** type for the **width** parameter.

If an invalid value or a value less than the minimum width of 56 vp is set, the attribute has no effect. In this case, the option width uses the default value, which is the width of two columns.

The **Select** component maintains 16 vp spacing from both left and right screen edges by default. This creates a 32 vp total horizontal margin (16 vp × 2). To prevent horizontal shifting when the drop-down menu is displayed, set the width of the component itself and its menu options to a value less than or equal to **calc(100% - 32 vp)**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [OptionWidthMode](../arkts-apis/arkts-arkui-optionwidthmode-e.md)&gt; | Yes | Width of the drop-down menu option.<br>If **width** is set to **undefined**, it has no effect. In this case, the option width uses the default value, which is the width of two columns. |

## selected

```TypeScript
selected(value: number | Resource)
```

Sets the index of the initially selected option in the drop-down menu, where the first option has an index of 0. When **selected** is set to an invalid value or is not set, the default default **-1** is used, which indicates no selection. When **selected** is set to **undefined** or **null**, the first option is selected.

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Index of the initially selected option. The index is zero-based.<br>**Since:** 11 |

<a id="selected-1"></a>

## selected

```TypeScript
selected(numCount: Optional<number | Resource>)
```

Sets the index of the initially selected option in the drop-down menu, where the first option has an index of 0. When **selected** is set to an invalid value or is not set, the default default **-1** is used, which indicates no selection. When **selected** is set to **undefined** or **null**, the first option is selected.

This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md) and [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| numCount | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Index of the initially selected option.<br>When **numCount** is set to **undefined**, the first option is selected. |

## selectedOptionBgColor

```TypeScript
selectedOptionBgColor(value: ResourceColor)
```

Sets the background color of the selected option in the drop-down menu.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the selected option in the drop-down menu.<br>Default value: **$r('sys.color.ohos_id_color_component_activated')** with the opacity of **$r('sys.color.ohos_id_alpha_highlight_bg')** |

<a id="selectedoptionbgcolor-1"></a>

## selectedOptionBgColor

```TypeScript
selectedOptionBgColor(resColor: Optional<ResourceColor>)
```

Sets the background color of the selected option in the drop-down menu. Compared with [selectedOptionBgColor](#selectedoptionbgcolor), this API supports the **undefined** type for the **resColor** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Background color of the selected option in the drop-down menu.<br> When **resColor** is set to **undefined**, the default value is a blend of **$r('sys.color.ohos_id_color_component_activated')** with the opacity of **$r('sys.color.ohos_id_alpha_highlight_bg')**. |

## selectedOptionFont

```TypeScript
selectedOptionFont(value: Font)
```

Sets the text font of the selected option in the drop-down menu. When **size** is set to **0**, the text is not displayed. When **size** is set to a negative value, the text is displayed at its default size.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text font of the selected option in the drop-down menu.<br>Default value:<br>{<br>size: $r('sys.float.ohos_id_text_size_body1'),<br>weight: FontWeight.Regular<br>} |

<a id="selectedoptionfont-1"></a>

## selectedOptionFont

```TypeScript
selectedOptionFont(selectFont: Optional<Font>)
```

Sets the text font of the selected option in the drop-down menu. When **size** is set to **0**, the text is not displayed. When **size** is set to a negative value, the text is displayed at its default size. Compared with [selectedOptionFont](#selectedoptionfont), this API supports the **undefined** type for the **selectFont** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectFont | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | Yes | Text font of the selected option in the drop-down menu.<br>If **selectFont** is set to **undefined**, the default value is used:<br>{<br>size: $r('sys.float.ohos_id_text_size_body1'),<br> weight: FontWeight.Regular<br>} |

## selectedOptionFontColor

```TypeScript
selectedOptionFontColor(value: ResourceColor)
```

Sets the font color of the selected option in the drop-down menu.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the selected option in the drop-down menu.<br>Default value: **$r('sys.color.ohos_id_color_text_primary_activated')** |

<a id="selectedoptionfontcolor-1"></a>

## selectedOptionFontColor

```TypeScript
selectedOptionFontColor(resColor: Optional<ResourceColor>)
```

Sets the font color of the selected option in the drop-down menu. Compared with [selectedOptionFontColor](#selectedoptionfontcolor), this API supports the **undefined** type for the **resColor** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Font color of the selected option in the drop-down menu.<br>If **resColor** is set to **undefined**, the default value **$r('sys.color.ohos_id_color_text_primary_activated')** is used. |

## selectedOptionTextModifier

```TypeScript
selectedOptionTextModifier(modifier: Optional<TextModifier>)
```

Creates a selected-option text modifier to customize the text style of selected options in the drop-down menu. After **selectedOptionTextModifier** is applied, the selected-option text style will be completely customized by the developer.

If both [selectedOptionFont](#selectedoptionfont) and **Font** of **selectedOptionTextModifier** are set, [selectedOptionFont](#selectedoptionfont) takes precedence. If **selectedOptionFont** is not set, [optionFont](#optionfont) settings are applied. Any unspecified attributes in **selectedOptionFont** or **optionFont** will use default values.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;TextModifier&gt; | Yes | Selected-option text modifier to apply to the **Select** component for customizing the text style of selected options in the drop-down menu.<br>You can manage and maintain the text style as needed. |

## showDefaultSelectedIcon

```TypeScript
showDefaultSelectedIcon(show: boolean)
```

Sets whether to display the default selection icon.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| show | boolean | Yes | Whether to display the default selection icon.<br>**true**: The default icon is displayed. **false**: The default icon is not displayed. The background color is highlighted to indicate that the icon is selected.<br>Default value: **false**<br>When **show** is set to **true** and the background color of the selected option is set, both the background color of the selected option and the icon selected by default are displayed. If the background color of the selected item is not set via **selectedOptionBgColor**, the background color is not highlighted and only the icon selected by default is displayed. |

## showInSubWindow

```TypeScript
showInSubWindow(showInSubWindow: Optional<boolean>)
```

Sets whether the drop-down menu is displayed in the subwindow. If this API is not used, the drop-down menu is not displayed in the subwindow by default.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| showInSubWindow | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the drop-down menu is displayed in the subwindow.<br> **true**: The drop-down menu is displayed in the subwindow.<br>**false**: The drop-down menu is not displayed in the subwindow. |

## space

```TypeScript
space(value: Length)
```

Sets the spacing between the text and arrow of a drop-down menu option. This attribute cannot be set in percentage. If the value specified is **null**, **undefined**, or less than or equal to 8, the default value is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Spacing between the text and arrow of a drop-down menu option.<br>Default value: **8**<br>Note: For the string type, percentage values are not supported. |

<a id="space-1"></a>

## space

```TypeScript
space(spaceLength: Optional<Length>)
```

Sets the spacing between the text and arrow of a drop-down menu option. This attribute cannot be set in percentage. If the value specified is **null**, **undefined**, or less than or equal to 8, the default value is used.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spaceLength | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Length](../arkts-apis/arkts-arkui-length-t.md)&gt; | Yes | Spacing between the text and arrow of an option.<br>If **spaceLength** is set to **undefined**, the default value **8** is used. |

## textModifier

```TypeScript
textModifier(modifier: Optional<TextModifier>)
```

Creates a text modifier to customize the text style of the **Select** button. After **textModifier** is applied, the text style of the **Select** button will be completely customized by the developer.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;TextModifier&gt; | Yes | Text modifier to apply to the **Select** button for customizing the text style. |

## value

```TypeScript
value(value: ResourceStr)
```

Sets the text content of drop-down button. After a menu option is selected, the button text will automatically update to display the selected option's text.

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text of the drop-down button.<br>Note: If the text exceeds the column width, it will be truncated.<br>**Since:** 11 |

<a id="value-1"></a>

## value

```TypeScript
value(resStr: Optional<ResourceStr>)
```

Sets the text content of drop-down button. After a menu option is selected, the button text will automatically update to display the selected option's text. Compared with [value](#value), this API supports the **undefined** type for the **resStr** parameter.

This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md) and [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resStr | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)&gt; | Yes | Text of the drop-down button.<br>If **resStr** is set to **undefined**, the previous value is retained. |
