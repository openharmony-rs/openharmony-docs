# KeyboardAvoidMode

```TypeScript
export const enum KeyboardAvoidMode
```

Enumerates the modes in which the layout responds when the keyboard is displayed.

**Since:** 11

<!--Device-unnamed-export const enum KeyboardAvoidMode--><!--Device-unnamed-export const enum KeyboardAvoidMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OFFSET

```TypeScript
OFFSET = 0
```

Offset Type, the layout moves up.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyboardAvoidMode-OFFSET = 0--><!--Device-KeyboardAvoidMode-OFFSET = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE

```TypeScript
RESIZE = 1
```

Resize Type, the layout is resized.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyboardAvoidMode-RESIZE = 1--><!--Device-KeyboardAvoidMode-RESIZE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OFFSET_WITH_CARET

```TypeScript
OFFSET_WITH_CARET = 2
```

Offset Type, the layout moves up, and this adjustment also occurs if the caret position in the text box changes.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-KeyboardAvoidMode-OFFSET_WITH_CARET = 2--><!--Device-KeyboardAvoidMode-OFFSET_WITH_CARET = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_WITH_CARET

```TypeScript
RESIZE_WITH_CARET = 3
```

Resize Type, the layout moves up, and this adjustment also occurs if the caret position in the text box changes.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-KeyboardAvoidMode-RESIZE_WITH_CARET = 3--><!--Device-KeyboardAvoidMode-RESIZE_WITH_CARET = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 4
```

None Type, the layout is not adjusted to avoid the keyboard.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-KeyboardAvoidMode-NONE = 4--><!--Device-KeyboardAvoidMode-NONE = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
