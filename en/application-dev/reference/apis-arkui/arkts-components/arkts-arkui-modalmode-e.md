# ModalMode

Enumerates modal modes of the sub-window menu.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

Automatic mode, which is the default behavior of the menu component on the current device. In the current version, the effect on all devices is the same as that of **ModalMode.NONE**.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 1
```

Events can be passed through areas other than the menu itself, allowing underlying controls to respond to events.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TARGET_WINDOW

```TypeScript
TARGET_WINDOW = 2
```

Events cannot be passed through the application window where the menu is located and the menu area, but can be passed through other areas.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
