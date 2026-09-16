# Display Management Overview
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1901db9be343b0a2f2f315e66f0588f9bda6dfc5 translatedAt=2026-09-14T09:13:41.796Z pushedAt=2026-09-15T13:10:15.549Z -->

Display management is responsible for managing various types of displays on a device, including physical, virtual, and foldable displays. It manages their properties and acts as a publisher, broadcasting display-related events and information to subscribed services that require display information.

Display management includes the following capabilities:

- Obtaining the display properties, such as resolution, physical pixel density, and dimensions.
- Listening for various display events, including rotation, resolution changes, refresh rate changes, and folding state changes.
- Creating and using virtual screens. This capability is available only for system applications.

For details about how to obtain display properties and listen for status changes, see [Using OH_DisplayManager to Obtain Basic Display Information and Listen for Status Changes (C/C++)](native-display-manager.md) and [Using Display to Obtain Display Properties and Listen for Status Changes (ArkTS)](screenProperty-guideline.md).<!--Del--> For details about how to use virtual screens, see [Creating and Using a Virtual Screen (ArkTS) (for System Applications Only)](virtualScreen-guideline-sys.md).<!--DelEnd-->

## Constraints

- The Display and Screen APIs must be used in the system that supports the SystemCapability.Window.SessionManager capability. For details, see <!--RP1-->[SystemCapability](../reference/syscap.md).<!--RP1End-->
- In multi-display implementation, the Screen API is available only for system applications, and certain APIs require the ohos.permission.CAPTURE_SCREEN permission.