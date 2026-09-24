# TextMenuShowMode

```TypeScript
declare enum TextMenuShowMode
```

Enumerates the text menu display modes.

**Since:** 16

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

The menu is displayed in the current window.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 16.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PREFER_WINDOW

```TypeScript
PREFER_WINDOW = 1
```

The menu is preferentially displayed in a separate window. If a separate window is not supported, the menu is displayed in the current window.

**NOTE:** 

Displaying the text selection menu in a separate window is not supported for window types other than the app main window, app sub-window, system modal window, and system desktop window.

Displaying the text selection menu in a separate window is not supported in the previewer.

Displaying the text selection menu in a separate window is not supported in [UIExtension](arkts-arkui-arkui-uiextension.md).

When a text component is displayed in a child window of [Popup](arkts-arkui-arkui-advanced-popup.md), [Dialog](arkts-arkui-arkui-advanced-dialog.md), [Toast](../../../ui/arkts-create-toast.md), or [Menu](../arkts-components/arkts-arkui-menu-comp.md#menu), the corresponding text selection menu cannot be displayed in a separate window.

When **autoFill** is available for **TextInput** or **TextArea**, the corresponding text selection menu cannot be displayed in a separate window.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 16.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
