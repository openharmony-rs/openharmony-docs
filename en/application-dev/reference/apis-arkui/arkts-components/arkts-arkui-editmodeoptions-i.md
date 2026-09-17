# EditModeOptions

Define edit mode options.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onGetPreviewBadge

```TypeScript
onGetPreviewBadge?: OnGetPreviewBadgeCallback
```

Called to return whether to display the number badge or the number displayed on the badge for the context menu preview. If not set, the number of selected items within the display range will be used. Returning false means not displaying the badge. Returning true means using the number of selected items within the display range. Returning a number to include selected items outside the display range.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableGatherSelectedItemsAnimation

```TypeScript
enableGatherSelectedItemsAnimation?: boolean
```

Define whether to gather selected items in grid or list when item is long pressed for context menu.

**Type:** boolean

**Default:** false

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableTwoFingerMultiSelect

```TypeScript
enableTwoFingerMultiSelect?: boolean
```

Enable two-finger swipe multi-selection. `true` indicates that two-finger swiping can enter edit mode and perform multi-selection. `false` indicates that two-finger swiping cannot perform multi-selection.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## useDefaultMultiSelectStyle

```TypeScript
useDefaultMultiSelectStyle?: boolean
```

Use default multi-select style. `true` indicates that the check box is displayed for GridItem or ListItem after entering the multi-select state. `false` indicates that there is no default style after entering the multi-select state.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
