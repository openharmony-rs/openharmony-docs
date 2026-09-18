# ShowWindowOptions

Describes the parameters for displaying a child window or system window.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## focusOnShow

```TypeScript
focusOnShow?: boolean
```

Whether the window automatically gains focus when [showWindow()](arkts-arkui-window-window-i.md#showwindow) is called. The default value is **true**. This parameter does not take effect for the main window, modal window, and dialog boxes.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager
