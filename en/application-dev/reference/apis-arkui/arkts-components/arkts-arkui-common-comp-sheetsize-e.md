# SheetSize

```TypeScript
declare enum SheetSize
```

Defines sheet size type.

**Since:** 10

<!--Device-unnamed-declare enum SheetSize--><!--Device-unnamed-declare enum SheetSize-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FIT_CONTENT

```TypeScript
FIT_CONTENT = 2
```

Specifies the half-modal height as the height that fits the content.

**Note:** 

1. FIT_CONTENT means that the half-modal container height adapts to the layout of the root node of the child
builder. In this scenario, the height of the root node of the builder cannot use a percentage, because the two cannot depend on each other's layout.
2. If the half-modal uses the SheetSize.FIT_CONTENT adaptive mode and its type is set to a centered dialog
box or a follow-hand dialog box, in API version 22 and earlier, the maximum height is displayed when the height is greater than the maximum height, and the minimum height is displayed when the height is less than the minimum height.

Starting from API version 23, the maximum height is displayed when the height is greater than the maximum height, and the actual adaptive height takes effect when the height is less than the minimum height.

For a centered dialog box and a follow-hand dialog box, the minimum height is 320 vp and the maximum height is 90% of the short side of the window.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetSize-FIT_CONTENT = 2--><!--Device-SheetSize-FIT_CONTENT = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LARGE

```TypeScript
LARGE = 1
```

Specifies the half-modal height as almost the height of the window where the half-modal is located.

On TV devices, the half-modal height is the height of the window where the half-modal is located.

**Note:** 

This value is invalid for a centered dialog box or a follow-hand dialog box, in which case the default height 560 vp is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SheetSize-LARGE = 1--><!--Device-SheetSize-LARGE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MEDIUM

```TypeScript
MEDIUM = 0
```

Specifies the half-modal height as 60% of the window where the half-modal is located.

On TV devices, the half-modal height is 50% of the window where the half-modal is located.

**Note:** 

This value is invalid for a centered dialog box or a follow-hand dialog box, in which case the default height 560 vp is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SheetSize-MEDIUM = 0--><!--Device-SheetSize-MEDIUM = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
