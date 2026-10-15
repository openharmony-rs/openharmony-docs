# SheetMode

```TypeScript
declare enum SheetMode
```

Define the display mode of the sheet.

**Since:** 12

<!--Device-unnamed-declare enum SheetMode--><!--Device-unnamed-declare enum SheetMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EMBEDDED

```TypeScript
EMBEDDED = 1
```

Sets the semi-modal panel to be displayed at the top level of the current page.

**Note:** 

Currently, the panel can be mounted only on a Page or NavDestination node. If a NavDestination exists, it is mounted on the NavDestination first. Top-level display is supported only in these two types of pages.

In this mode, a newly opened page can cover the semi-modal dialog box. After returning from the page, the semi-modal dialog box still exists and its content is not lost.

In this mode, ensure that the target page node (for example, the Page node) is mounted to the tree before the semi-modal dialog box is displayed. Otherwise, the semi-modal dialog box cannot be mounted to the corresponding page node.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetMode-EMBEDDED = 1--><!--Device-SheetMode-EMBEDDED = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OVERLAY

```TypeScript
OVERLAY = 0
```

The sheet is displayed at the top of the window corresponding to the current **UIContext** instance, above all pages. It is displayed at the same level as dialog boxes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetMode-OVERLAY = 0--><!--Device-SheetMode-OVERLAY = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
