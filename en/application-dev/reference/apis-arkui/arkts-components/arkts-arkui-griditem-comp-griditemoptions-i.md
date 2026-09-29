# GridItemOptions

```TypeScript
declare interface GridItemOptions
```

Defines the **GridItem** style object, used to configure the style options of **GridItem**.

**Since:** 11

<!--Device-unnamed-declare interface GridItemOptions--><!--Device-unnamed-declare interface GridItemOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: GridItemStyle
```

Style of **GridItem**.

Default value: **GridItemStyle.NONE**

When set to **GridItemStyle.NONE**, no style is applied.

When set to **GridItemStyle.PLAIN**, the **Hover** and **Press** state styles are displayed. The **Hover** state is the style when the mouse hovers over the item, and the **Press** state is the style when the item is pressed.

**Type:** [GridItemStyle](arkts-arkui-griditem-comp-griditemstyle-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridItemOptions-style?: GridItemStyle--><!--Device-GridItemOptions-style?: GridItemStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
