# Window Rotation

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4; @jingbotao-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9b78e8a8d68d68a001cb6f06fd10a6c905fa0406 translatedAt=2026-11-03T02:57:40.445Z pushedAt=2026-11-03T03:03:05.829Z nl=1 -->

## Overview

The window rotation feature allows applications to automatically adjust their UI layout based on the device's physical orientation or user interaction, thereby improving the user experience in different usage scenarios.

Users can hold their mobile devices in various orientations. To ensure an optimal experience, applications sometimes need to adapt their layout to the device's orientation or lock the display to a specific one. For example, games operated with both hands are more suitable for landscape display, whereas video applications often need to switch freely between full-screen and Picture-in-Picture (PiP) playback.

The system provides screen rotation features, allowing you to define how your application responds to orientation changes.

A device has four display orientations. When a user holds the device upright, if the screen width is greater than its height, it is in **LANDSCAPE** mode, and the opposite orientation is **LANDSCAPE_INVERTED**. Conversely, if the screen height is greater than its width, it is in **PORTRAIT** mode, and the opposite is **PORTRAIT_INVERTED**.

The system determines the application's display orientation by comprehensively considering the rotation policy set by the application, the device's current holding orientation (gravity sensor angle), the system rotation lock switch state (which can be viewed/set by pulling down the Control Center), and the scenario the application is in (such as split screen, smart multi-window floating window, application background, etc.). For devices running OpenHarmony 7.0.0 or later, the system also determines the application's display orientation in combination with the system Smart Sense rotation switch state (on devices that support the smart sensing sensor, the Smart Sense rotation switch can be enabled via **Settings > System > Smart Sense rotation**).

Only the main window supports setting a rotation policy. Setting a rotation policy for a non-main window has no effect and does not report an error, and does not affect the display orientation.

The general principle of how the "application's scenario" affects the display orientation is as follows:

- If the application's main window is displayed in full screen, changes in rotation strategies take effect immediately.

- If the application's main window is not displayed in full screen, changes to the rotation strategy do not take effect immediately. The orientation change takes effect only when the application's main window enters full-screen display.

For details about the differences between rotation strategies and device-related differences, see [Rotation Strategies and Device Differences](#rotation-strategies-and-device-differences). For details about the rotation strategies and restrictions in different scenarios, see [Behavior Restrictions of the Rotation API](#behavior-restrictions-of-the-rotation-api).

> **NOTE**
>
> The terms "candy-bar-like form" and "tablet-like form" used in this document mainly refer to foldable devices. On foldable devices, the screen aspect ratio and available size change in different forms, which affects the system's judgment of the rotation policy:
>
> - **Candy-bar-like form**: The screen aspect ratio is close to that of a bar phone, and the system processes the rotation policy according to the bar phone specification. For example, the device is in the folded state, uses the external screen, or is a small foldable (clamshell) device in the unfolded state. In this mode, rotation is supported only to three orientations: portrait, landscape, and reverse landscape; reverse portrait is not supported. In addition, when rotation is locked, the device cannot be locked in the landscape state.
>
> - **Tablet-like form**: The screen aspect ratio is close to that of a tablet device, and the system processes the rotation policy according to the tablet specification. For example, when the device is in the unfolded state, rotation is supported to four orientations: portrait, landscape, reverse portrait, and reverse landscape. When rotation is locked, the device can be locked in the landscape state.

## Relationship Between Window Rotation and Screen Orientation

Typically, "window rotation" refers to an application calling the [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API to set a rotation strategy, thereby changing the display orientation of the application on the screen. More precisely, this strategy influences the entire screen's orientation, which in turn affects the layout of all on-screen elements, including system components (such as home screen, status bar, pull-down control panel, and pull-down notification center) and other applications. The key point is that changing an application's rotation strategy affects not only the application itself but also all visible elements on the screen, including elements that are invisible in the background. These elements ultimately transition from one direction to another through a rotation animation.

The system provides the screen property [@ohos.display](../reference/apis-arkui/js-apis-display.md) to obtain basic screen information, where [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) represents the current display direction of the device screen. This value updates after a window rotation. It is important to note that [Orientation](../reference/apis-arkui/arkts-apis-window-e.md#orientation9) used in the rotation strategy is a different concept from [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) used in the screen property, though they share the same names for the four base directions. For details, see [Window Orientation](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-multi-device-window-direction).

The aspect ratio of an application window has no direct relationship with the screen property [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10), and it is not recommended to adapt the window layout based on the screen property [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10). The screen property [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) is only used to assist in orientation correction for sensors and cameras.

## Behavior Restrictions of the Rotation API

When a foreground application calls [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) to set a rotation strategy, the system immediately checks whether the current screen display orientation meets the new strategy.

- If not, in most cases, the system immediately triggers a rotation animation to comply. For example:

  Scenario 1: An application switches from **PORTRAIT** to **LANDSCAPE** while the user holds the phone upright. The application immediately rotates to landscape.

  Scenario 2: An application switches from **PORTRAIT** to **AUTO_ROTATION** while the user holds the phone sideways. The application immediately rotates from portrait to landscape.

- In special cases, such as multi-window floating windows, split-screen, multitasking, application background, and free windows, the system ignores the rotation policy set by the app. The API can be called normally, but the application's display orientation does not change. The system readjusts the application's display layout based on the rotation policy only when the application exits these scenarios.

  Scenario 1: In special scenarios such as split-screen and multi-window floating windows, the system forces the application to display in portrait orientation to maintain the display effect. In this case, if the application changes its rotation strategy to **LANDSCAPE**, the display orientation does not change.

  Scenario 2: In free windows mode, all applications are forced to display in a small window, and rotation strategies are ignored.

In addition, the application's display orientation is strongly related to sensors. On devices without sensors (such as TVs) or devices where sensor rotation is disabled (such as [PC mode](../windowmanager/window-terminology.md#desktop-mode)), setting a rotation policy does not take effect: the [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API can be called normally, but the actual application orientation does not change.


## Rotation Strategies and Device Differences

An application can set the display orientation through the "orientation" field in the [module.json5 configuration file](../quick-start/module-configuration-file.md), or by calling the [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) API at runtime. For details, see [Setting the Window Rotation Policy](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-landscape-and-portrait-development#section58861731201715).

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
| AUTO_ROTATION_RESTRICTED | 8 | Follows the sensor to auto-rotate, and can rotate to four orientations: portrait, landscape, reverse portrait, and reverse landscape. It is also controlled by the system rotation lock switch. |
| AUTO_ROTATION_PORTRAIT_RESTRICTED | 9 | Follows the sensor to auto-rotate vertically, and can rotate to portrait and reverse portrait, but cannot rotate to landscape or reverse landscape. It is also controlled by the system rotation lock switch. |
| AUTO_ROTATION_LANDSCAPE_RESTRICTED | 10 | Follows the sensor to auto-rotate horizontally, and can rotate to landscape and reverse landscape, but cannot rotate to portrait or reverse portrait. It is also controlled by the system rotation lock switch. |
| AUTO_ROTATION_UNSPECIFIED | 12 | Follows the sensor to auto-rotate, is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system (for example, on a bar phone, it can rotate to three orientations: portrait, landscape, and reverse landscape, but cannot rotate to reverse portrait). |

These seven orientation types are commonly used to set the app to adjust its orientation according to the gravity sensor so that the app always displays the page correctly when the user holds the device. For devices running OpenHarmony 7.0.0 or later, a new capability is added to set the app to adjust its orientation according to the smart sensor, and the final app orientation is determined by both the gravity sensor and the smart sensor together.

There are some differences in these seven types depending on the usage scenario. For example:

- The types with the "RESTRICTED" suffix, "AUTO_ROTATION_RESTRICTED", "AUTO_ROTATION_PORTRAIT_RESTRICTED", and "AUTO_ROTATION_LANDSCAPE_RESTRICTED", are controlled by the system rotation lock switch. When rotation lock is enabled, an application set to these types is fixed in the locked orientation and no longer follows the gravity sensor to adjust the page. For devices running OpenHarmony 7.0.0 or later, when rotation lock is enabled, an application set to these types is fixed in the locked orientation and, in addition to no longer following the gravity sensor to adjust the page, also no longer follows the smart sensing sensor to adjust the page.

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
| USER_ROTATION_PORTRAIT | 13 | Temporarily rotates to portrait when called, then follows the sensor to auto-rotate, is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system. (For example, on a bar phone, it can rotate to portrait, landscape, and reverse landscape, but cannot rotate to reverse portrait.) |
| USER_ROTATION_LANDSCAPE | 14 | Temporarily rotates to landscape when called, then follows the sensor to auto-rotate, is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system. (For example, on a bar phone, it can rotate to portrait, landscape, and reverse landscape, but cannot rotate to reverse portrait.) |
| USER_ROTATION_PORTRAIT_INVERTED | 15 | Temporarily rotates to reverse portrait when called, then follows the sensor to auto-rotate, is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system. (For example, on a bar phone, it can rotate to portrait, landscape, and reverse landscape, but cannot rotate to reverse portrait.) |
| USER_ROTATION_LANDSCAPE_INVERTED | 16 | Temporarily rotates to reverse landscape when called, then follows the sensor to auto-rotate, is controlled by the system rotation lock switch, and the rotatable orientations are determined by the system. (For example, on a bar phone, it can rotate to portrait, landscape, and reverse landscape, but cannot rotate to reverse portrait.) |

These four orientation types are controlled by the system rotation lock switch and also support auto-rotation based on the gravity sensor. For devices running OpenHarmony 7.0.0 or later, auto-rotation based on the smart sensing sensor is newly supported (on devices that support the smart sensing sensor, the Smart Sense rotation switch can be enabled via **Settings > System > Smart Sense rotation**). The difference between these four types and "AUTO_ROTATION_RESTRICTED" is that when an application sets these four orientation types, the application is immediately and temporarily rotated to the specified orientation. For example, when a user holds the phone in portrait orientation and the application is displayed in portrait, if the application sets the rotation policy to "USER_ROTATION_LANDSCAPE", the application immediately rotates to landscape display. These four types are typically used by video applications when transitioning from small-window playback to full-screen playback.

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

- "UNSPECIFIED" is the undefined orientation type, which means that when an application has neither set it in the module.json5 file nor called [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) at runtime, the system uses this type by default. In this case, the application's display orientation is determined by the system. Typically, on a bar phone, the default is portrait display and rotation is not supported; on a tablet, rotation to four orientations is supported and is controlled by the system rotation lock switch.

- **LOCKED** is the locked mode, typically used in application-launching-application scenarios. An application set to this strategy maintains the same orientation as the previous application when launched by another app. When this strategy is in effect, the application's orientation may also change due to reasons such as application switching.

- "FOLLOW_DESKTOP" is the follow-desktop mode. Typically, the desktop of a bar phone is fixed in portrait display and cannot rotate, while the desktop of a tablet can rotate. Foldable devices such as dual-fold, tri-fold, and wide-fold devices are special: in the folded state, the desktop cannot rotate, just like a bar phone, but in the unfolded state, it can rotate, just like a tablet. For the actual desktop rotation effect, refer to the behavior on a real device.

## Constraints

- The [setPreferredOrientation()](../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1) interface takes effect only on devices that support sensor-based rotation (such as phones and tablets). On devices without sensors (such as TVs) or devices where sensor-based rotation is disabled (such as PC mode), the interface can be called normally, but the application display orientation does not change. For details, see [Behavior Restrictions of the Rotation API](#behavior-restrictions-of-the-rotation-api).
- The rotatable orientations differ across device form factors (bar phone/candy-bar-like form, tablet/tablet-like form, and foldable device folded/unfolded states). For details, see [Rotation Strategies and Device Differences](#rotation-strategies-and-device-differences).
