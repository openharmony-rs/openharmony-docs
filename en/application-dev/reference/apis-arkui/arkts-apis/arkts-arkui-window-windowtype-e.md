# WindowType

```TypeScript
enum WindowType
```

Enumerates the window types.

**Since:** 7

<!--Device-window-enum WindowType--><!--Device-window-enum WindowType-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_APP

```TypeScript
TYPE_APP = 0
```

Child window of an application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WindowType-TYPE_APP = 0--><!--Device-WindowType-TYPE_APP = 0-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_SYSTEM_ALERT

```TypeScript
TYPE_SYSTEM_ALERT = 1
```

System alert window.

**Since:** 7

**Deprecated since:** 11

<!--Device-WindowType-TYPE_SYSTEM_ALERT = 1--><!--Device-WindowType-TYPE_SYSTEM_ALERT = 1-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_FLOAT

```TypeScript
TYPE_FLOAT = 8
```

Global floating window.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WindowType-TYPE_FLOAT = 8--><!--Device-WindowType-TYPE_FLOAT = 8-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_DIALOG

```TypeScript
TYPE_DIALOG = 16
```

Modal window.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WindowType-TYPE_DIALOG = 16--><!--Device-WindowType-TYPE_DIALOG = 16-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## TYPE_MAIN

```TypeScript
TYPE_MAIN = 32
```

Main window of an application.

This window type cannot be used during window creation.

**Since:** 18

<!--Device-WindowType-TYPE_MAIN = 32--><!--Device-WindowType-TYPE_MAIN = 32-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core
