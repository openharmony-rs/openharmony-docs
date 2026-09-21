# MenuItem properties/events

```TypeScript
declare class MenuItemAttribute extends CommonMethod<MenuItemAttribute>
```

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** MenuItemAttribute extends CommonMethod<MenuItemAttribute>

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentFont

```TypeScript
contentFont(value: Font)
```

Sets the font style of the menu item content.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Font style of the menu item content. |

## contentFontColor

```TypeScript
contentFontColor(value: ResourceColor)
```

Sets the font color of the menu item content.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the menu item content.<br>Default value: **'#E5000000'** |

## labelFont

```TypeScript
labelFont(value: Font)
```

Sets the font style of the menu item label.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Font style of the menu item label. |

## labelFontColor

```TypeScript
labelFontColor(value: ResourceColor)
```

Sets the font color of the menu item label.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the menu item label.<br>Default value: **'#99000000'** |

## onChange

```TypeScript
onChange(callback: (selected: boolean) => void)
```

Triggered when the selection status of the menu item is changed manually.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (selected: boolean) =&gt; void | Yes | Invoked when the selected status changes.<br>**true**: selected; **false**: unselected. |

## selected

```TypeScript
selected(value: boolean)
```

Sets whether the menu item is selected.

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the menu item is selected.<br>**true**: The menu item is selected. **false**: The menu item is not selected.<br>Default value: **false**. |

## selectIcon

```TypeScript
selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier)
```

Sets whether to display the selected icon when the menu item is selected.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md) | Yes | Whether to display the selected icon when the menu item is selected.<br>**true**: Display the default check mark icon. **false**: Hide the selected state icon.<br>**ResourceStr**: Display the specified custom icon resource.<br>**SymbolGlyphModifier**: Display the specified HMSymbol icon.<br>Default value: **false**.<br>**Since:** 12 |

## subMenuBuilder

```TypeScript
subMenuBuilder(builder: CustomBuilder)
```

Create the submenu for custom menu item.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Indicates the builder function for submenu. |
