# TextSelectableMode

```TypeScript
declare enum TextSelectableMode
```

Sets whether text can be selected and focused on.

**Since:** 12

<!--Device-unnamed-declare enum TextSelectableMode--><!--Device-unnamed-declare enum TextSelectableMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELECTABLE_UNFOCUSABLE

```TypeScript
SELECTABLE_UNFOCUSABLE = 0
```

The text is selectable, but not focusable. Setting the **selection**, **bindSelectionMenu**, or **copyOption** attribute does not affect the behavior.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextSelectableMode-SELECTABLE_UNFOCUSABLE = 0--><!--Device-TextSelectableMode-SELECTABLE_UNFOCUSABLE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELECTABLE_FOCUSABLE

```TypeScript
SELECTABLE_FOCUSABLE = 1
```

The text is selectable and focusable. It obtains focus when touched.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextSelectableMode-SELECTABLE_FOCUSABLE = 1--><!--Device-TextSelectableMode-SELECTABLE_FOCUSABLE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## UNSELECTABLE

```TypeScript
UNSELECTABLE = 2
```

The text is not selectable nor focusable. The **selection**, **bindSelectionMenu**, and **copyOption** attributes do not work in this case.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextSelectableMode-UNSELECTABLE = 2--><!--Device-TextSelectableMode-UNSELECTABLE = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
