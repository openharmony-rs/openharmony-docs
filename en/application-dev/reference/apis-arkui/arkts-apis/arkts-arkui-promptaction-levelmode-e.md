# LevelMode

```TypeScript
export enum LevelMode
```

Enumerates the display level modes of the dialog box.

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OVERLAY

```TypeScript
OVERLAY = 0
```

The dialog box is displayed at the root node level of the application window and remains visible during navigation.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EMBEDDED

```TypeScript
EMBEDDED = 1
```

The dialog box is a child of the page's route/navigation and is hidden when the page is hidden. <br>**NOTE:** <br>1. Currently, the dialog box can only be mounted to a **Page** or [NavDestination](../arkui-ts/ts-basic-components-navdestination.md) node, with **Page** nodes taking precedence. The dialog box is displayed only on top of these two page types. <br>2. In this mode, new pages can be displayed over the dialog box. When users return to the previous page, the dialog box remains visible and its content is preserved. <br>3. In this mode, you must ensure that the target page node, such as the **Page** node, has been attached to the tree before bringing up the dialog box; otherwise, the dialog box will not be able to be attached to the corresponding page node.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
