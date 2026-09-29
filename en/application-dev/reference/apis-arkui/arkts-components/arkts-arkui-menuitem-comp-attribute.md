# MenuItem properties/events

```TypeScript
declare class MenuItemAttribute extends CommonMethod<MenuItemAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** MenuItemAttribute extends CommonMethod<MenuItemAttribute>

**Since:** 9

<!--Device-unnamed-declare class MenuItemAttribute extends CommonMethod<MenuItemAttribute>--><!--Device-unnamed-declare class MenuItemAttribute extends CommonMethod<MenuItemAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentFont

```TypeScript
contentFont(value: Font)
```

Sets the font style of the menu item content.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemAttribute-contentFont(value: Font): MenuItemAttribute--><!--Device-MenuItemAttribute-contentFont(value: Font): MenuItemAttribute-End-->

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

<!--Device-MenuItemAttribute-contentFontColor(value: ResourceColor): MenuItemAttribute--><!--Device-MenuItemAttribute-contentFontColor(value: ResourceColor): MenuItemAttribute-End-->

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

<!--Device-MenuItemAttribute-labelFont(value: Font): MenuItemAttribute--><!--Device-MenuItemAttribute-labelFont(value: Font): MenuItemAttribute-End-->

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

<!--Device-MenuItemAttribute-labelFontColor(value: ResourceColor): MenuItemAttribute--><!--Device-MenuItemAttribute-labelFontColor(value: ResourceColor): MenuItemAttribute-End-->

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

<!--Device-MenuItemAttribute-onChange(callback: (selected: boolean) => void): MenuItemAttribute--><!--Device-MenuItemAttribute-onChange(callback: (selected: boolean) => void): MenuItemAttribute-End-->

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

<!--Device-MenuItemAttribute-selected(value: boolean): MenuItemAttribute--><!--Device-MenuItemAttribute-selected(value: boolean): MenuItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the menu item is selected.<br>**true**: The menu item is selected. **false**: The menu item is not selected. <br>Default value: **false**. |

## selectIcon

```TypeScript
selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier)
```

Sets how the icon of a menu item is displayed when the menu item is selected.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemAttribute-selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier): MenuItemAttribute--><!--Device-MenuItemAttribute-selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier): MenuItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md) | Yes | How the icon is displayed when the menu item is selected.<br>**true**: display the default check mark icon. **false**: do not display the icon.<br> **ResourceStr**: display the specified icon.<br>**SymbolGlyphModifier**: display the specified HMSymbol icon.<br>Default value: **false**<br>**Since:** 12 |

## subMenuBuilder

```TypeScript
subMenuBuilder(builder: CustomBuilder)
```

Sets the submenu of a custom menu item.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MenuItemAttribute-subMenuBuilder(builder: CustomBuilder): MenuItemAttribute--><!--Device-MenuItemAttribute-subMenuBuilder(builder: CustomBuilder): MenuItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Custom content of the submenu.<br>When the input parameter type of the **MenuItem** component is [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md), this parameter can be used to access the custom submenu.<br>When the parent component is [Menu](arkts-arkui-menu-comp.md), the submenu can be triggered only when the [subMenuExpandingMode](arkts-arkui-menu-comp-attribute.md#submenuexpandingmode) attribute is set to **SubMenuExpandingMode.SIDE_EXPAND** or **SubMenuExpandingMode.STACK_EXPAND**. |
