# MenuItemGroup
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=85a246303a3306c0a0ebfe5d53b17f767869db93 translatedAt=2026-09-03T04:15:04.053Z -->

This component is used to display a group of menu items. It supports setting the header and footer information of a group, and is used to organize and manage the classification structure of menu items. It is applicable to scenarios where multiple menu items need to be organized by category in a menu. By grouping, it clearly presents the hierarchical structure of the menu, improving the readability of the menu and the user experience.

> **NOTE**
>
> - This component is supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This component supports [WithTheme](./ts-container-with-theme.md) since API version 26.0.0.

## Child Components

This component contains the [MenuItem](ts-basic-components-menuitem.md) child component.

## APIs

MenuItemGroup(value?: MenuItemGroupOptions)

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                 | Mandatory| Description                                       |
| ------ | ----------------------------------------------------- | ---- | ------------------------------------------- |
| value  | [MenuItemGroupOptions](#menuitemgroupoptions) | No   | Sets the title and footer information of MenuItemGroup.<br/> If this parameter is not set, the title and footer information are not displayed. |

## MenuItemGroupOptions

Header and footer information of a menu item group.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type                                                        | Read-Only| Optional| Description                         |
| ------ | ------------------------------------------------------------ | ---- | ---- | ----------------------------- |
| header | [ResourceStr](ts-types.md#resourcestr)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | No   | Yes   | Sets the title of the group, which is displayed at the top of all menu items in the group. <br/> If not set, no title is displayed. |
| footer | [ResourceStr](ts-types.md#resourcestr)&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | No   | Yes   | Sets the footer of the group, which is displayed at the bottom of all menu items in the group. <br/> If not set, no footer is displayed. |

## Sample

For details, see [Example in Menu](ts-basic-components-menu.md#example).
