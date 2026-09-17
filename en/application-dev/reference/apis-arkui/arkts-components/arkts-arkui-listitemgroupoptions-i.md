# ListItemGroupOptions

Describes the **ListItemGroup** component parameter.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: CustomBuilder
```

Footer of the list item group.

**Type:** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## footerStyle

```TypeScript
footerStyle?: ListItemGroupHeaderFooterStyle
```

Footer style of ListItemGroup. If this parameter is set to ListItemGroupHeaderFooterStyle.FLOATING, the footer component is displayed in floating mode during scrolling.

**Type:** [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroupheaderfooterstyle-e.md)

**Default:** ListItemGroupHeaderFooterStyle.NONE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## header

```TypeScript
header?: CustomBuilder
```

Header of the list item group.

**Type:** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## headerStyle

```TypeScript
headerStyle?: ListItemGroupHeaderFooterStyle
```

Header style of ListItemGroup. If this parameter is set to ListItemGroupHeaderFooterStyle.FLOATING, the header component is displayed in floating mode during scrolling.

**Type:** [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroupheaderfooterstyle-e.md)

**Default:** ListItemGroupHeaderFooterStyle.NONE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: number | string
```

Spacing between list items. This parameter only affects the spacing between list items, but not spacing between the header and list items or between the footer and list items. <br>Default value: **0**<br>Unit: vp

**Type:** number &#124; string

**Default:** 0

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ListItemGroupStyle
```

Style of the list item.

**Type:** [ListItemGroupStyle](arkts-arkui-listitemgroupstyle-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
