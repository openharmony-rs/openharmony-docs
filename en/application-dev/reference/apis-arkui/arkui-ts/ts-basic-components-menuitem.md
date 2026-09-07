# MenuItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f4455d49fe81d569e83d83e0e0f1509f8b842b29 translatedAt=2026-09-03T04:14:53.359Z -->

The **MenuItem** component represents an item in a menu.

> **NOTE**
>
> - This component is supported since API version 9. Newly added content in later versions is marked with a superscript to indicate the version in which it was introduced.
>
> - This component supports [WithTheme](./ts-container-with-theme.md) since API version 26.0.0.

## Child Components

Not supported

## APIs

MenuItem(value?: MenuItemOptions | CustomBuilder)

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                        |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------- |
| value  | [MenuItemOptions](#menuitemoptions)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | No   | Contains the information for setting the MenuItem. Use MenuItemOptions when standard menu item configuration (such as the start icon, content, and label) is required; use CustomBuilder when the display content and layout of the menu item need to be customized. If this parameter is not passed, an empty MenuItem object is created. |

## MenuItemOptions

Information about a menu item in a menu.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type                                       | Read-Only| Optional| Description                            |
| --------- | ------------------------------------------- | ---- | -------------------------------------- | -------------------------------------- |
| startIcon | [ResourceStr](ts-types.md#resourcestr)      | No   | Yes  | Start icon of the MenuItem. Symbol icons are not supported. To use a Symbol icon, use symbolStartIcon instead. By default, no start icon is displayed. <br/>**Atomic service API:** This API is supported in atomic services since API version 11.      |
| content   | [ResourceStr](ts-types.md#resourcestr)      | No   | Yes  | Content of the MenuItem. The default value is an empty string.<br/>**Atomic service API:** This API is supported in atomic services since API version 11.                        |
| endIcon   | [ResourceStr](ts-types.md#resourcestr)      | No   | Yes  | End icon of the MenuItem. Symbol icons are not supported. To use a Symbol icon, use symbolEndIcon instead. By default, no end icon is displayed.<br/>**Atomic service API:** This API is supported in atomic services since API version 11.        |
| labelInfo | [ResourceStr](ts-types.md#resourcestr)      | No   | Yes  | Label information at the end of the MenuItem, for example, the shortcut key Ctrl+C. By default, no label information is displayed.<br/>**Atomic service API:** This API is supported in atomic services since API version 11.  |
| builder   | [CustomBuilder](ts-types.md#custombuilder8) | No   | Yes  | Used to build a secondary menu. By default, no secondary menu is displayed.<br/>**Atomic service API:** This API is supported in atomic services since API version 11.                      |
| symbolStartIcon<sup>12+</sup>   | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md)| No   | Yes  | Symbol icon at the start of the MenuItem. When this item is configured, the original startIcon is not displayed. By default, no Symbol start icon is displayed.<br/>**Atomic service API:** This API is supported in atomic services since API version 12.<br/>**Model constraint:** This API can be used only in the stage model.|
| symbolEndIcon<sup>12+</sup>   | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md)| No   | Yes  | Symbol icon at the end of the MenuItem. When this item is configured, the original endIcon is not displayed. By default, no Symbol end icon is displayed.<br/>**Atomic service API:** This API is supported in atomic services since API version 12.<br/>**Model constraint:** This API can be used only in the stage model.|


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

Sets how the icon of a menu item is displayed when the menu item is selected.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | boolean&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr)<sup>10+</sup>\|&nbsp;[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md)<sup>12+</sup> | Yes   | How the icon is displayed when the menu item is selected.<br/>true: displays the default checkmark icon; false: does not display the icon.<br/>ResourceStr: displays the specified icon.<br/>SymbolGlyphModifier: displays the specified HMSymbol icon.<br/>Default value: false |
### contentFont<sup>10+</sup>

contentFont(value: Font)

Sets the font style of the menu item content.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                    | Mandatory| Description                        |
| ------ | ------------------------ | ---- | ---------------------------- |
| value  | [Font](ts-types.md#font) | Yes  | Font style of the menu item content.|

### contentFontColor<sup>10+</sup>

contentFontColor(value: ResourceColor)

Sets the font color of the menu item content.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Font color of the menu item content.<br>Default value: **'#E5000000'**|

### labelFont<sup>10+</sup>

labelFont(value: Font)

Sets the font style of the menu item label.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                    | Mandatory| Description                        |
| ------ | ------------------------ | ---- | ---------------------------- |
| value  | [Font](ts-types.md#font) | Yes  | Font style of the menu item label.|

### labelFontColor<sup>10+</sup>

labelFontColor(value: ResourceColor)

Sets the font color of the menu item label.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Font color of the menu item label.<br>Default value: **'#99000000'**|

### subMenuBuilder

subMenuBuilder(builder: CustomBuilder)

Sets the submenu of a custom menu item.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters** 

| Name | Type                                                         | Mandatory | Description                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| builder  | [CustomBuilder](ts-types.md#custombuilder8) | Yes   | Sets the custom content of the submenu.<br/>When the input parameter type of the MenuItem component is [CustomBuilder](ts-types.md#custombuilder8), this attribute can be used to access the custom submenu.<br/>When the parent component is [Menu](ts-basic-components-menu.md), the submenu can be triggered only when the [subMenuExpandingMode](ts-basic-components-menu.md#submenuexpandingmode12) attribute is set to SubMenuExpandingMode.SIDE_EXPAND or SubMenuExpandingMode.STACK_EXPAND.|

## Events

### onChange

onChange(callback: (selected: boolean) => void)

Triggered when the selection status of the menu item is changed manually.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory| Description                                                        |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| selected | boolean | Yes | Whether the current menu item is selected.<br />true: the current menu item is selected; false: the current menu item is not selected. |

## Example

See the example of [Menu](ts-basic-components-menu.md#example).
