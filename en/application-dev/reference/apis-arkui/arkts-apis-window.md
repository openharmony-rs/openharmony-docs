# Module Description
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b5bac46b123c8ef772e6a1f04f3d13c5b3c45368 translatedAt=2026-11-02T13:08:15.970Z pushedAt=2026-11-09T06:23:55.713Z nl=1 -->

The module provides basic window management capabilities, such as creating and destroying the current window, setting properties for the current window, and managing and scheduling windows.

This module provides the following common window-related functionalities:

- [Window](arkts-apis-window-Window.md): window instance, which is the basic unit managed by the window manager.
- [WindowStage](arkts-apis-window-WindowStage.md): window manager that manages windows.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - For the system capability SystemCapability.Window.SessionManager, use [canIUse()](../common/js-apis-syscap.md#caniuse) to check whether the device supports this system capability and the corresponding APIs.

## Modules to Import

```ts
import { window } from '@kit.ArkUI';
```