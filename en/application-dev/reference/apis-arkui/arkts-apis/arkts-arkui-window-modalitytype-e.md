# ModalityType

Enumerates the modality types of the child window.

**Since:** 14

**System capability:** SystemCapability.Window.SessionManager

## WINDOW_MODALITY

```TypeScript
WINDOW_MODALITY = 0
```

Select this value when only the parent window should not respond to user operations.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

## APPLICATION_MODALITY

```TypeScript
APPLICATION_MODALITY = 1
```

Select this value when other instances of the application should also not respond to user operations.

This enumeration can be called properly on a device that supports [freeform windows](../../../windowmanager/window-terminology.md#freeform-window) and is in the freeform window state. If the device does not support freeform windows, or if the device supports freeform windows but is not in the freeform window state, error code 801 is returned.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager
