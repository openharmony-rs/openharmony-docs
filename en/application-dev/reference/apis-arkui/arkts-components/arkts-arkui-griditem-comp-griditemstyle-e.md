# GridItemStyle

```TypeScript
declare enum GridItemStyle
```

Enumerates the **GridItem** styles, used to define the interaction state styles of **GridItem**.

> **NOTE:** 
> 
> To set the focused style for the grid item, the grid container must have paddings of greater than 4 vp for
> accommodating the focus frame of the grid item.

**Since:** 11

<!--Device-unnamed-declare enum GridItemStyle--><!--Device-unnamed-declare enum GridItemStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

No style. **Hover** and **Press** state styles are not displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridItemStyle-NONE = 0--><!--Device-GridItemStyle-NONE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PLAIN

```TypeScript
PLAIN = 1
```

Displays **Hover** and **Press** state styles. The **Hover** state is the style when the mouse hovers, and the **Press** state is the style when pressed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridItemStyle-PLAIN = 1--><!--Device-GridItemStyle-PLAIN = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
