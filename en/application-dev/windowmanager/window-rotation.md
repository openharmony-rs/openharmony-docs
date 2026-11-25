# Window Rotation

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4; @jingbotao-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=eccecdf8133db426ff20bd2d5a89d4d0bef35522 translatedAt=2026-11-05T10:55:52.948Z pushedAt=2026-11-06T01:56:16.703Z nl=1 -->

## Overview

The window rotation feature allows an application to automatically adjust its UI layout based on the physical orientation of the device or the user's interaction behavior, thereby improving the user experience in different usage scenarios.

Users can hold their mobile devices in various orientations. To ensure an optimal experience, applications sometimes need to adapt their layout to the device's orientation or lock the display to a specific one. For example, games operated with both hands are more suitable for landscape display, whereas video applications often need to switch freely between full-screen and Picture-in-Picture (PiP) playback.

The system provides screen rotation features, allowing you to define how your application responds to orientation changes.

A device has four display orientations. When a user holds the device upright, if the screen width is greater than its height, it is in **LANDSCAPE** mode, and the opposite orientation is **LANDSCAPE_INVERTED**. Conversely, if the screen height is greater than its width, it is in **PORTRAIT** mode, and the opposite is **PORTRAIT_INVERTED**.

The system determines the display orientation of an application by comprehensively considering the rotation policy set by the application, the current holding orientation of the device (gravity sensor angle), the system rotation lock switch state (which can be viewed or set by pulling down the Control Panel), and the scenario the application is in (such as split-screen mode, smart multi-window floating window, or running in the background). For devices running OpenHarmony 7.0.0 or later, the system also determines the display orientation of the application in combination with the system smart sensing rotation switch state (on devices that support the smart sensor, you can enable the smart sensing rotation switch by going to **Settings > System > Smart sensing rotation**).

Only the main window supports setting a rotation policy. Setting a rotation policy for a non-main window has no effect and does not report an error, and does not affect the display orientation.

The general principle of how the "application's scenario" affects the display orientation is as follows:

- If the application's main window is displayed in full screen, changes in rotation strategies take effect immediately.

- If the application's main window is not displayed in full screen, changes to the rotation strategy do not take effect immediately. The orientation change takes effect only when the application's main window enters full-screen display.

For details about the differences between rotation strategies and device-related differences, see [Rotation Strategies and Device Differences](#rotation-strategies-and-device-differences). For details about the rotation strategies and restrictions in different scenarios, see [Behavior Restrictions of the Rotation API](#behavior-restrictions-of-the-rotation-api).

> **NOTE**
>
> The terms "bar-type form factor" and "tablet-type form factor" in this document mainly apply to foldable devices. On a foldable device, the screen aspect ratio and available size change in different forms, which affects how the system determines the rotation policy:
>
> - **Bar-type form factor**: The screen aspect ratio is close to that of a bar phone, and the system handles the rotation policy according to the bar phone specification. For example, the device is in the folded state using the external screen, or it is a small foldable (clamshell) device in the unfolded state. In this mode, the device can rotate only to three orientations: portrait, landscape, and reverse landscape. Reverse portrait is not supported. In addition, when rotation is locked, the device cannot be locked in the landscape state.
>
> - **Tablet-type form factor**: The screen aspect ratio is close to that of a tablet device, and the system handles the rotation policy according to the tablet specification. For example, when the device is in the unfolded state, it can rotate to four orientations: portrait, landscape, reverse portrait, and reverse landscape. When rotation is locked, the device can be locked in the landscape state.

## Relationship Between Window Rotation and Screen Orientation

Typically, "window rotation" refers to an application calling the [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API to set a rotation strategy, thereby changing the display orientation of the application on the screen. More precisely, this strategy influences the entire screen's orientation, which in turn affects the layout of all on-screen elements, including system components (such as home screen, status bar, pull-down control panel, and pull-down notification center) and other applications. The key point is that changing an application's rotation strategy affects not only the application itself but also all visible elements on the screen, including elements that are invisible in the background. These elements ultimately transition from one direction to another through a rotation animation.

The system provides the screen property [@ohos.display](../reference/apis-arkui/js-apis-display.md) to obtain basic screen information, where [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) represents the current display direction of the device screen. This value updates after a window rotation. It is important to note that [Orientation](../reference/apis-arkui/arkts-apis-window-e.md#orientation9) used in the rotation strategy is a different concept from [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) used in the screen property, though they share the same names for the four base directions. For details, see [Window Orientation](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-multi-device-window-direction).

The aspect ratio of an application window has no direct relationship with the screen property [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10). It is not recommended to adapt the window layout based on the screen property [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10). The screen property [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) is used only to assist in correcting the orientation of the sensor and camera.

## Behavior Restrictions of the Rotation API

When a foreground application calls [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) to set a rotation strategy, the system immediately checks whether the current screen display orientation meets the new strategy.

- If not, in most cases, the system immediately triggers a rotation animation to comply. For example:

  Scenario 1: An application switches from **PORTRAIT** to **LANDSCAPE** while the user holds the phone upright. The application immediately rotates to landscape.

  Scenario 2: An application switches from **PORTRAIT** to **AUTO_ROTATION** while the user holds the phone sideways. The application immediately rotates from portrait to landscape.

- In special cases, such as multi-window floating windows, split-screen, multitasking, application background, and free windows, the system ignores the rotation policy set by the app. The API can be called normally, but the application's display orientation does not change. The system readjusts the application's display layout based on the rotation policy only when the application exits these scenarios.

  Scenario 1: In special scenarios such as split-screen and multi-window floating windows, the system forces the application to display in portrait orientation to maintain the display effect. In this case, if the application changes its rotation strategy to **LANDSCAPE**, the display orientation does not change.

  Scenario 2: In free windows mode, all applications are forced to display in a small window, and rotation strategies are ignored.

In addition, the display orientation of an application is strongly related to sensors. On devices without sensors (such as TVs) or devices where sensor rotation is disabled (such as [PC mode](../windowmanager/window-terminology.md#desktop-mode)), setting a rotation policy does not take effect: you can still call the [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API normally, but the actual application orientation does not change.


## Rotation Strategies and Device Differences

You can set the display orientation through the "orientation" field in the [module.json5 configuration file](../quick-start/module-configuration-file.md), or by calling the [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API at runtime. For details, see [Setting the Window Rotation Policy](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-landscape-and-portrait-development#section58861731201715).

The system provides 18 orientation types to meet the needs of different scenarios. Depending on the usage scenario, these orientation types can be divided into fixed, automatic rotation, temporary, and others.

### Fixed Orientation Types

| Name| Value| Description |
| -------- | -------- | -------- |
| PORTRAIT | 1 | Portrait.|
| LANDSCAPE | 2 | Landscape.|
| PORTRAIT_INVERTED | 3 | Reverse portrait.|
| LANDSCAPE_INVERTED | 4 | Reverse landscape.|

These four types lock the application to a specific orientation, regardless of how the user holds the device. They are commonly used in games.

> **NOTE**
> 
> [Orientation](../reference/apis-arkui/arkts-apis-window-e.md#orientation9) used in the rotation strategy is a different concept from [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) used in the screen property, though they share the same names for the four base directions. For details, see [Window Orientation](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-multi-device-window-direction).

### Automatic Rotation Orientation Types

| Name| Value| Description |
| -------- | -------- | -------- |
| AUTO_ROTATION | 5 | Automatically rotates with the sensor. The orientation can be portrait, landscape, reverse portrait, or reverse landscape.|
| AUTO_ROTATION_PORTRAIT | 6 | Automatically rotates with the sensor in the vertical direction. The orientation can be portrait or reverse portrait.|
| AUTO_ROTATION_LANDSCAPE | 7 | Automatically rotates with the sensor in the horizontal direction. The orientation can be landscape or reverse landscape.|
| AUTO_ROTATION_RESTRICTED | 8 | Follows sensor auto-rotation, can rotate to portrait, landscape, reverse portrait, and reverse landscape (four orientations), and is controlled by the system rotation lock switch. |
| AUTO_ROTATION_PORTRAIT_RESTRICTED | 9 | Follows sensor auto-rotation in portrait orientation, can rotate to portrait and reverse portrait, cannot rotate to landscape or reverse landscape, and is controlled by the system rotation lock switch. |
| AUTO_ROTATION_LANDSCAPE_RESTRICTED | 10 | Follows sensor auto-rotation in landscape orientation, can rotate to landscape and reverse landscape, cannot rotate to portrait or reverse portrait, and is controlled by the system rotation lock switch. |
| AUTO_ROTATION_UNSPECIFIED | 12 | Follows sensor auto-rotation, is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system (for example, on a bar-type device, it can rotate to portrait, landscape, and reverse landscape, three orientations, but cannot rotate to reverse portrait). |

These seven orientation types are commonly used to set the app to adjust its orientation according to the gravity sensor so that the app always displays the page correctly when the user holds the device. For devices running OpenHarmony 7.0.0 or later, a new capability is added to set the app to adjust its orientation according to the smart sensor, and the final app orientation is determined by both the gravity sensor and the smart sensor together.

There are some differences in these seven types depending on the usage scenario. For example:

- The types with the "RESTRICTED" suffix, namely "AUTO_ROTATION_RESTRICTED", "AUTO_ROTATION_PORTRAIT_RESTRICTED", and "AUTO_ROTATION_LANDSCAPE_RESTRICTED", are controlled by the system rotation lock switch. When rotation lock is enabled, an application set to these types is fixed in the locked orientation and no longer adjusts its page according to the gravity sensor. For devices running OpenHarmony 7.0.0 or later, when rotation lock is enabled, an application set to these types is fixed in the locked orientation and, in addition to no longer adjusting its page according to the gravity sensor, also no longer adjusts its page according to the smart sensor.

- Types with **PORTRAIT** or **LANDSCAPE** restrict the application to rotate between portrait/inverted portrait and landscape/inverted landscape.

> **NOTE**
> 
> The two rotation policies, **AUTO_ROTATION_RESTRICTED** and **AUTO_ROTATION_UNSPECIFIED**, are very similar in functionality: both support auto-rotation controlled by the rotation lock switch. However, there are some differences between them on different products.
> 
> - **When the system rotation lock switch is off**
> 
>   The **AUTO_ROTATION_RESTRICTED** policy allows rotation to all four orientations of the device. In contrast, the orientations to which **AUTO_ROTATION_UNSPECIFIED** can rotate depend on the product form factor of the device. On a bar phone or when the device is in a bar-phone-like form, apps with this orientation type can rotate to three orientations—portrait, landscape, and reverse landscape—but not to reverse portrait. On a tablet or when the device is in a tablet-like form, apps can rotate to all four orientations of the device.
> 
> - **When the system rotation lock switch is on**
> 
>   On a bar phone or when the device is in a bar-phone-like form, neither **AUTO_ROTATION_RESTRICTED** nor **AUTO_ROTATION_UNSPECIFIED** supports locking to landscape. When an application is set to either of these two rotation policies and rotates to landscape, if the user then pulls down the control panel and enables rotation lock, the application is forced to rotate to portrait and remains in the rotation-locked state. On a tablet or when the device is in a tablet-like form, both rotation policies support locking to landscape. If an application needs to support auto-rotation on a bar phone while also being able to lock to the current orientation, it is recommended to prioritize using the **USER_ROTATION** rotation policy.

### Temporary Orientation Types

| Name| Value| Description |
| -------- | -------- | -------- |
| USER_ROTATION_PORTRAIT | 13 | Temporarily rotates to portrait when called, then follows sensor auto-rotation. It is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system. (For example, on a bar-type device, it can rotate to portrait, landscape, and reverse landscape, but not to reverse portrait.) |
| USER_ROTATION_LANDSCAPE | 14 | Temporarily rotates to landscape when called, then follows sensor auto-rotation. It is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system. (For example, on a bar-type device, it can rotate to portrait, landscape, and reverse landscape, but not to reverse portrait.) |
| USER_ROTATION_PORTRAIT_INVERTED | 15 | Temporarily rotates to reverse portrait when called, then follows sensor auto-rotation. It is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system. (For example, on a bar-type device, it can rotate to portrait, landscape, and reverse landscape, but not to reverse portrait.) |
| USER_ROTATION_LANDSCAPE_INVERTED | 16 | Temporarily rotates to reverse landscape when called, then follows sensor auto-rotation. It is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system. (For example, on a bar-type device, it can rotate to portrait, landscape, and reverse landscape, but not to reverse portrait.) |

These four orientation types are controlled by the system rotation lock switch and also support auto-rotation based on the gravity sensor. For devices running OpenHarmony 7.0.0 or later, a new capability is added to support auto-rotation based on the smart sensor (on devices that support the smart sensor, you can enable the smart sensing rotation switch by going to **Settings > System > Smart sensing rotation**). The difference between these four types and "AUTO_ROTATION_RESTRICTED" is that when an application sets these four types, the application is immediately and temporarily rotated to the specified orientation. For example, when the user holds the phone in portrait orientation and the application is displayed in portrait, if the application sets the rotation policy to "USER_ROTATION_LANDSCAPE", the application immediately rotates to landscape display. These four types are typically used by video applications when switching from small-window playback to full-screen playback.

> **NOTE**
> 
> **USER_ROTATION_PORTRAIT_INVERTED** is a special temporary orientation type with differences across devices.
> 
> - On a bar phone or when the device is in a bar-phone-like form, an application set to the **USER_ROTATION_PORTRAIT_INVERTED** rotation policy cannot temporarily rotate to reverse portrait. Instead, it still displays in portrait orientation, and during auto-rotation, it can only rotate to three orientations—portrait, landscape, and reverse landscape—but not to reverse portrait.
> 
> - On a tablet or when the device is in a tablet-like form, when the rotation lock switch is off, the application can auto-rotate to all four orientations: portrait, reverse portrait, landscape, and reverse landscape.

### Other Orientation Types

| Name| Value| Description |
| -------- | -------- | -------- |
| UNSPECIFIED | 0 | Unspecified. The orientation is determined by the system.|
| LOCKED | 11 | Locked.|
| FOLLOW_DESKTOP | 17 | Following the orientation of the home screen.|

These three types are used in the following specific scenarios:

- "UNSPECIFIED" is the undefined orientation type. That is, when an application neither sets the orientation in the module.json5 file nor calls [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) at runtime, the system uses this type for the application by default. In this case, the display orientation of the application is determined by the system. Typically, on a bar phone, the default is portrait display and rotation is not supported; on a tablet, rotation to four orientations is supported and is controlled by the system rotation lock switch.

- **LOCKED** is the locked mode, typically used in application-launching-application scenarios. An application set to this strategy maintains the same orientation as the previous application when launched by another app. When this strategy is in effect, the application's orientation may also change due to reasons such as application switching.

- "FOLLOW_DESKTOP" is the follow-desktop mode. Typically, the home screen of a bar phone is fixed in portrait display and cannot rotate, while the home screen of a tablet can rotate. Foldable devices such as dual-fold, tri-fold, and wide-fold devices are special: in the folded state, the home screen cannot rotate, just like a bar phone, but in the unfolded state, it can rotate, just like a tablet. For the actual home screen rotation effect, refer to the behavior on a real device.

## Constraints

- The [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API takes effect only on devices that support sensor-based rotation (such as phones and tablets). On devices without sensors (such as TVs) or devices where sensor-based rotation is disabled (such as in PC mode), the API can still be called normally, but the application display orientation will not change. For details, see [Behavior Restrictions of the Rotation API](#behavior-restrictions-of-the-rotation-api).

- The orientations to which the screen can rotate differ across device forms (bar phones/bar-phone-like forms, tablets/tablet-like forms, and foldable phones in folded/unfolded states). For details, see [Rotation Strategies and Device Differences](#rotation-strategies-and-device-differences).
