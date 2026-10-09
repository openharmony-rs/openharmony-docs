# Window Type Development Overview

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4; @qinliwen0417-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=ec7630a78aacf2433fa2a5ddf9c98995fe35f1df translatedAt=2026-10-08T09:06:59.931Z pushedAt=2026-10-09T00:53:19.349Z -->

Windows are divided into two types: system windows and app windows.

## System Window

A system window is a window that performs system-specific functions, such as the volume bar, wallpaper, notification panel, status bar, and navigation bar. <!--Del-->For details, see [WindowType](../reference/apis-arkui/js-apis-window-sys.md#windowtype7).<!--DelEnd-->

## App Window

Different from system windows, app windows refer to windows related to app display and are used to show app content. Based on management methods and purposes, app windows can be further divided into main windows and auxiliary windows.

### Main Window

A main window is created by default when a UIAbility is created. It is displayed as an independent task card in the task management UI and is used to show the main UIAbility UI of the app.

### Auxiliary Window

Auxiliary windows are created and destroyed by the app itself. They are not displayed as an independent task card in the task management UI and can be used to show auxiliary content of the app, such as dialogs.

Auxiliary windows include:

- Subwindow  

  In the stage model, created using the [createSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindow9-1) or [createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindowwithoptions11) API. For details, see [Subwindow Development Guide](subwindow-guide.md).

  When the [createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindowwithoptions11) API is used with the **zLevelAboveParentLoosened** attribute set to **true**, the created subwindow is called an independent subwindow.

- Global floating window (that is, **WindowType.TYPE_FLOAT**). For details, see [Global Floating Window Development](global-floating-window-guide.md).

- Dialog window (that is, **WindowType.TYPE_DIALOG**). For details, see [Dialog Window Development](dialog-window-guide.md).

- [Picture-in-picture](../reference/apis-arkui/js-apis-pipWindow.md)

- [Floating ball](../reference/apis-arkui/js-apis-floatingBall.md)

- [Float view](../reference/apis-arkui/js-apis-floatView.md)

## Comparison Between Floating Ball and Float View

- Commonalities: Both the float view and the [floating ball](../reference/apis-arkui/js-apis-floatingBall.md) are special application auxiliary windows. They can remain displayed in the foreground after the application main window and the corresponding UIAbility (application component) move to the background. They can be used to keep displaying the UI through the float view or floating ball after the application moves to the background.

- Differences:

  - They differ in display form. The floating ball is displayed as a small ball and is suitable for showing key information. The float view is displayed as a small window with a larger display area, which can continuously display application content or provide quick operations.

  - The floating ball can only be displayed docked to the screen edge, while the float view has no such restriction.

  - The floating ball has a fixed template, and applications cannot customize its UI. The float view also has a template, and its UI is managed and drawn uniformly by the system, but it provides a drawable area where applications can load specified page content.

- Applicable scenarios:

  - The floating ball is suitable for cross-application scenarios such as question search, bill recording, product price comparison, order grabbing, and translation, as well as real-time market tracking in financial applications.

  - The float view is suitable for scenarios where application content needs to be continuously displayed in an independent small window or quick operations need to be provided, such as stock tracking applications and live streaming applications.

- Linkage: The float view and the floating ball can be used together. After the float view controller is bound to the floating ball controller through the [floatView.bind](../reference/apis-arkui/js-apis-floatView.md#floatviewbind) API, tapping the floating ball expands it into the float view, and tapping the minimize button in the upper left corner of the float view collapses it back into the floating ball, enabling switching between the two window forms. 

## Comparison Between Global Floating Windows and Float View

- Commonalities: Both global floating windows and float views are a special type of application auxiliary window. They can remain displayed in the foreground even after the application main window and the corresponding UIAbility move to the background. They can be used to keep displaying UI through a global floating window or a float view after the application moves to the background.

- Differences:

  - You need to manage the global floating windows and implement UI rendering, with no unified UI or animation effects.

  - The float view is managed by the system, which renders a unified UI with more sophisticated and refined animation effects.

  - A float view supports binding and joint use with a [floating ball](../reference/apis-arkui/js-apis-floatingBall.md) to implement more complex scenarios.

  - The global floating window is only supported on PC/2-in-1 devices.

  - The float view is supported on phones, tablets, and PC/2-in-1 devices.

- Applicable scenarios:

  - The global floating window is suitable for multi-person video calls and screen sharing scenarios.

  - The float view is suitable for scenarios where application content needs to be continuously displayed in an independent small window or quick operations need to be provided, such as stock tracking applications and mobile live streaming applications.

  - For other non-specified scenarios, such as video playback, video conferencing, and video calls, you are advised to use [picture-in-picture](../reference/apis-arkui/js-apis-pipWindow.md) to present video content in a small window.