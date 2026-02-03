# MenuItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Armstrong15-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **MenuItem** component represents an item in a menu.

> **NOTE**
>
> This component is supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Child Components

Not supported

## APIs

MenuItem(value?: MenuItemOptions | CustomBuilder)

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                        |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------- |
| value  | [MenuItemOptions](#menuitemoptions)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | No  | Information about the menu item.|

## MenuItemOptions

Provides information about the menu item.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type                                       | Read-Only| Optional| Description                            |
| --------- | ------------------------------------------- | ---- | -------------------------------------- | -------------------------------------- |
| startIcon | [ResourceStr](ts-types.md#resourcestr)      | No  | Yes | Start icon of the menu item. Symbol icons are not supported. If a symbol icon is used, **symbolStartIcon** must be used.<br>**Atomic service API**: This API can be used in atomic services since API version 11.     |
| content   | [ResourceStr](ts-types.md#resourcestr)      | No  | Yes | Content of the menu item.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                       |
| endIcon   | [ResourceStr](ts-types.md#resourcestr)      | No  | Yes | End icon of the menu item. Symbol icons are not supported. If the symbol icon is used, **symbolEndIcon** must be used.<br>**Atomic service API**: This API can be used in atomic services since API version 11.       |
| labelInfo | [ResourceStr](ts-types.md#resourcestr)      | No  | Yes | Label information at the end of the menu item, such as shortcut keys like Ctrl+C.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| builder   | [CustomBuilder](ts-types.md#custombuilder8) | No  | Yes | Builder for a level-2 menu.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                     |
| symbolStartIcon<sup>12+</sup>   | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md)| No  | Yes | Symbol icon at the start of a menu item. When this parameter is set, the icon set through **startIcon** is not displayed.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| symbolEndIcon<sup>12+</sup>   | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md)| No  | Yes | Symbol icon at the end of a menu item. When this parameter is set, the icon set through **endIcon** is not displayed.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|


## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### selected

selected(value: boolean)

Sets whether the menu item is selected.

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes  | Whether the menu item is selected.<br>**true**: The menu item is selected. **false**: The menu item is not selected.<br>Default value: **false**.|

### selectIcon

selectIcon(value: boolean | ResourceStr | SymbolGlyphModifier)

Sets whether to display the selected icon when the menu item is selected.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | boolean&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)<sup>10+</sup>\|&nbsp;[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md)<sup>12+</sup> | Yes  | Whether to display the selected icon when the menu item is selected.<br>**true**: Display the default check mark icon. **false**: Hide the selected state icon.<br>**ResourceStr**: Display the specified custom icon resource.<br>**SymbolGlyphModifier**: Display the specified HMSymbol icon.<br>Default value: **false**.|
### contentFont<sup>10+</sup>

contentFont(value: Font)

Sets the font style of the menu item content.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                    | Mandatory| Description                        |
| ------ | ------------------------ | ---- | ---------------------------- |
| value  | [Font](ts-types.md#font) | Yes  | Font style of the menu item content.|

### contentFontColor<sup>10+</sup>

contentFontColor(value: ResourceColor)

Sets the font color of the menu item content.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Font color of the menu item content.<br>Default value: **'#E5000000'**|

### labelFont<sup>10+</sup>

labelFont(value: Font)

Sets the font style of the menu item label.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                    | Mandatory| Description                        |
| ------ | ------------------------ | ---- | ---------------------------- |
| value  | [Font](ts-types.md#font) | Yes  | Font style of the menu item label.|

### labelFontColor<sup>10+</sup>

labelFontColor(value: ResourceColor)

Sets the font color of the menu item label.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Font color of the menu item label.<br>Default value: **'#99000000'**|

## Events

### onChange

onChange(callback: (selected: boolean) => void)

Triggered when the selection status of the menu item is changed manually.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory| Description                                                        |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| selected | boolean | Yes  | Invoked when the selected status changes.<br>**true**: selected; **false**: unselected.|

## Example

See the example of [Menu](ts-basic-components-menu.md#example).
