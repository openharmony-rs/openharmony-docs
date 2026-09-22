# GridItemAlignment

```TypeScript
declare enum GridItemAlignment
```

Enumerates the alignment modes of grid items.

> **NOTE:** 
> 
> 1. The **STRETCH** option only takes effect in scrollable grids.<br>
> 2. The **STRETCH** option takes effect only if each grid item in a row is of a regular size (occupying only one row and one column). It is not effective in scenarios where there are grid items spanning across rows or columns.<br>
> 3. When **STRETCH** is used, only grid items without a set height will adopt the height of the tallest grid item in the current row; the height of grid items with a set height will remain unchanged.<br>
> 4. When **STRETCH** is used, the grid undergoes an additional layout process, which may incur additional performance overhead.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Use the default alignment mode of the grid.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STRETCH

```TypeScript
STRETCH = 1
```

Use the height of the tallest grid item in a row as the height for all other grid items in that row.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
