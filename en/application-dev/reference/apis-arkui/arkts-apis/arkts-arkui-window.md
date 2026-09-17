# @ohos.window

The Window module provides basic window management capabilities, such as creating and destroying the current window,
 setting properties for the current window, and managing and scheduling windows.

This module provides the following common window-related functions:

- [Window](arkts-arkui-window-n.md): window instance, which is the basic unit managed by the window manager.
 - [WindowStage](arkts-arkui-window-windowstage-i.md): window manager that manages windows.

> **NOTE**
 >
 > - This topic describes only system APIs provided by the module. For details about its public APIs, see
 > [@ohos.window (Window)](arkts-arkui-window-n.md).
 >
 > - For the system capability SystemCapability.Window.SessionManager, use
 > canIUse() to check whether the device supports this system
 > capability and the corresponding APIs.



## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [window](arkts-arkui-window-n.md) | Window manager. |

### Interfaces

| Name | Description |
| --- | --- |
| [Callback](arkts-arkui-window-callback-i.md) | Defines the window callback. |

### Types

| Name | Description |
| --- | --- |
| [WindowAnimationCurveParam](arkts-arkui-windowanimationcurveparam-t.md) | Defines the window animation curve param. |
| [WindowEventListener](arkts-arkui-windoweventlistener-t.md) | Callback function for window event |
