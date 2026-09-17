# @ohos.window.floatView

A float view is a small window that floats on a desktop or an application screen, providing flexible window management capabilities.

This module provides capabilities about the float view, including determining whether a device supports a float view, and creating a float view controller to start, update, or stop a float view.

**Application scenarios**:

A float view is applicable to scenarios where application content needs to be continuously displayed in an independent small window or shortcut operations need to be provided. Examples:

- Application for stock market tracking: When browsing other applications, users can use a float view to view real-  
time stock market changes without frequently switching between applications.  
- Live streaming application on a mobile phone: During live streaming, hosts can use a float view to display a custom  
interaction panel or control UI, facilitating real-time operations and interactions.

**Linkage with the floating ball**:

This module can be used together with [@ohos.window.floatingBall](arkts-arkui-window-floatingball.md). After the float view controller is bound to the floating ball controller using the [floatView.bind](arkts-arkui-floatview-bind-f.md) API, users can tap the floating ball to expand it as a float view, and click the minimize button in the upper left corner of the float view to collapse it back as a floating ball. This allows for seamless switching between the two window forms.

**Comparison between the global floating window and float view**:

- Similarities: Both the global floating window and float view are special types of application auxiliary windows  
that can remain displayed on the foreground even after the application's main window and corresponding ability transition to the background. They can be used to continue displaying the UI after the application transitions to the background.  
- Differences:  
- The global floating window is managed and its UI is drawn by developers, without a unified UI or animation effect.  
- The float view is managed by the system and its UI is drawn in a unified manner, offering a more sophisticated and  
refined animation effect.  
- The float view can be bound to the [floating ball](arkts-arkui-window-floatingball.md) for joint use,  
enabling more complex scenarios.

**Start version**: 26.0.0

> **NOTE:** 
> 
> - Use [canIUse()](../../../reference/common/js-apis-syscap.md#caniuse) to check whether the device supports the system capability SystemCapability.Window.SessionManager and the corresponding APIs.
> 
> - The APIs of this module can be used only in the stage model.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [bind](arkts-arkui-floatview-bind-f.md) | Binds the float view and floating ball. You need to create the [float view controller](arkts-arkui-floatview-floatviewcontroller-i.md) and [floating ball controller](arkts-arkui-floatingball-floatingballcontroller-i.md) first, and neither of them has been started. This API uses a promise to return the result. |
| [create](arkts-arkui-floatview-create-f.md) | Creates a float view controller. This API uses a promise to return the result. |
| [getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md) | Obtains the limits of the float view based on the passed template type. The unit is px. |
| [isFloatViewEnabled](arkts-arkui-floatview-isfloatviewenabled-f.md) | Checks whether the device supports the float view. |
| [unbind](arkts-arkui-floatview-unbind-f.md) | Unbinds the float view and floating ball. The unbinding can be performed only after both the [float view controller](arkts-arkui-floatview-floatviewcontroller-i.md) and [floating ball controller](arkts-arkui-floatingball-floatingballcontroller-i.md) are stopped. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [FloatViewConfiguration](arkts-arkui-floatview-floatviewconfiguration-i.md) | Provides parameter configuration required for creating a float view controller. |
| [FloatViewController](arkts-arkui-floatview-floatviewcontroller-i.md) | Defines a float view controller instance, which is used to start and stop the float view and register callbacks. |
| [FloatViewLimits](arkts-arkui-floatview-floatviewlimits-i.md) | Provides the limits of the float view. |
| [FloatViewProperties](arkts-arkui-floatview-floatviewproperties-i.md) | Provides the properties of the float view. |
| [FloatViewRectChangeInfo](arkts-arkui-floatview-floatviewrectchangeinfo-i.md) | Provides the rectangle area change information of the float view. |
| [FloatViewStateChangeInfo](arkts-arkui-floatview-floatviewstatechangeinfo-i.md) | Provides the state change information of the float view. |
| [RatioLimit](arkts-arkui-floatview-ratiolimit-i.md) | Provides the aspect ratio range of the float view. The aspect ratio is obtained by dividing the width of the rectangular area of the window by its height. |
| [TemplateProperty](arkts-arkui-floatview-templateproperty-i.md) | Provides parameter configuration required for switching the float view template and modifying the size of the window. |

### Enums

| Name | Description |
| --- | --- |
| [FloatViewState](arkts-arkui-floatview-floatviewstate-e.md) | Enumerates the states of the float view. |
| [FloatViewTemplateType](arkts-arkui-floatview-floatviewtemplatetype-e.md) | Provides the template type of the float view. |
