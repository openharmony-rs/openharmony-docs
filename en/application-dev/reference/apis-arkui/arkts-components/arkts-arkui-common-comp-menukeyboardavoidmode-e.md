# MenuKeyboardAvoidMode

```TypeScript
declare enum MenuKeyboardAvoidMode
```

Enumerates the modes in which the menu avoids the soft keyboard.

**Since:** 23

<!--Device-unnamed-declare enum MenuKeyboardAvoidMode--><!--Device-unnamed-declare enum MenuKeyboardAvoidMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

The menu does not avoid the soft keyboard.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-MenuKeyboardAvoidMode-NONE = 0--><!--Device-MenuKeyboardAvoidMode-NONE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE_AND_RESIZE

```TypeScript
TRANSLATE_AND_RESIZE = 1
```

The menu avoids the soft keyboard. If the space is insufficient, the menu will be translated or resized to avoid the soft keyboard.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-MenuKeyboardAvoidMode-TRANSLATE_AND_RESIZE = 1--><!--Device-MenuKeyboardAvoidMode-TRANSLATE_AND_RESIZE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
