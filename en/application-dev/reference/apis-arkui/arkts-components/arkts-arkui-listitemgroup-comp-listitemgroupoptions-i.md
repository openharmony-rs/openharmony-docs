# ListItemGroupOptions

```TypeScript
declare interface ListItemGroupOptions
```

Describes the **ListItemGroup** component parameter.

**Since:** 9

<!--Device-unnamed-declare interface ListItemGroupOptions--><!--Device-unnamed-declare interface ListItemGroupOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: CustomBuilder
```

Footer of the list item group.

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListItemGroupOptions-footer?: CustomBuilder--><!--Device-ListItemGroupOptions-footer?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footerComponent

```TypeScript
footerComponent?: ComponentContent
```

Footer of the list item group, in the type of ComponentContent. This parameter takes precedence over the footer parameter. This means that, if both footer and footerComponent are set, the value of footerComponent is used. To avoid display issues, do not assign the same footerComponent to different ListItemGroup components.

**Type:** ComponentContent

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ListItemGroupOptions-footerComponent?: ComponentContent--><!--Device-ListItemGroupOptions-footerComponent?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footerStyle

```TypeScript
footerStyle?: ListItemGroupHeaderFooterStyle
```

Footer style of ListItemGroup. If this parameter is set to ListItemGroupHeaderFooterStyle.FLOATING, the footer component is displayed in floating mode during scrolling.

**Type:** [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroup-comp-listitemgroupheaderfooterstyle-e.md)

**Default:** ListItemGroupHeaderFooterStyle.NONE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ListItemGroupOptions-footerStyle?: ListItemGroupHeaderFooterStyle--><!--Device-ListItemGroupOptions-footerStyle?: ListItemGroupHeaderFooterStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## header

```TypeScript
header?: CustomBuilder
```

Header component of the **ListItemGroup**. <p><strong>NOTE</strong> <br>It can contain a single child component or no child component. If it is not set, there is no header component. This parameter has a lower priority than **headerComponent**. That is, if both header and **headerComponent** are set, the value of **headerComponent** takes effect. </p>

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListItemGroupOptions-header?: CustomBuilder--><!--Device-ListItemGroupOptions-header?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## headerComponent

```TypeScript
headerComponent?: ComponentContent
```

Header of the list item group, in the type of ComponentContent. This parameter takes precedence over the header parameter. This means that, if both header and headerComponent are set, the value of headerComponent is used. To avoid display issues, do not assign the same headerComponent to different ListItemGroup components.

**Type:** ComponentContent

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ListItemGroupOptions-headerComponent?: ComponentContent--><!--Device-ListItemGroupOptions-headerComponent?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## headerStyle

```TypeScript
headerStyle?: ListItemGroupHeaderFooterStyle
```

Header style of ListItemGroup. If this parameter is set to ListItemGroupHeaderFooterStyle.FLOATING, the header component is displayed in floating mode during scrolling.

**Type:** [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroup-comp-listitemgroupheaderfooterstyle-e.md)

**Default:** ListItemGroupHeaderFooterStyle.NONE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ListItemGroupOptions-headerStyle?: ListItemGroupHeaderFooterStyle--><!--Device-ListItemGroupOptions-headerStyle?: ListItemGroupHeaderFooterStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: number | string
```

Spacing between list items. This parameter only affects the spacing between list items, but not spacing between the header and list items or between the footer and list items. <br>Default value: **0**<br>Unit: vp

**Type:** number &#124; string

**Default:** 0

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListItemGroupOptions-space?: number | string--><!--Device-ListItemGroupOptions-space?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spaceWidth

```TypeScript
spaceWidth?: Dimension
```

Spacing between list items. This parameter only affects the spacing between list items, but not spacing between the header and list items or between the footer and list items. <br>Default value: **0**<br>Unit: vp <br>**NOTE:** <br>If this parameter is set to a negative number or a value greater than or equal to the length of the list content area, the default value is used. If both **spaceWidth** and **space** are set, **spaceWidth** takes precedence. When **spaceWidth** is **undefined** or **null**, **space** takes effect.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ListItemGroupOptions-spaceWidth?: Dimension--><!--Device-ListItemGroupOptions-spaceWidth?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ListItemGroupStyle
```

Card style of the **ListItemGroup** component. <br>Default value: **ListItemGroupStyle.NONE** <br>When set to **ListItemGroupStyle.NONE**, no style is applied. <br>When set to **ListItemGroupStyle.CARD**, it is recommended to use it together with **ListItemStyle.CARD** of [ListItem](ts-container-listitem.md) to display the default card style. <br>In card style, the default specifications of **ListItemGroup** are as follows: left and right margins of 12 vp, and top, bottom, left, and right padding of 4 vp. <br>In card style, default **focused**, **hover**, **pressed**, **selected**, and **disabled** styles are provided for the list items in the card. <p><strong>NOTE</strong> <br>When set to **ListItemGroupStyle.CARD**, the **listDirection** attribute of List must be **Axis.Vertical**. If it is set to **Axis.Horizontal**, the display will be disordered. The [alignListItem](ts-container-list.md#alignlistitem9) attribute of **List** defaults to **ListItemAlign.Center**, which centers the items. </p>

**Type:** [ListItemGroupStyle](arkts-arkui-listitemgroup-comp-listitemgroupstyle-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListItemGroupOptions-style?: ListItemGroupStyle--><!--Device-ListItemGroupOptions-style?: ListItemGroupStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
