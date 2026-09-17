# window

Window manager.

**Since:** 6

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createWindow](arkts-arkui-window-createwindow-f.md) | Creates a child window or system window. This API uses an asynchronous callback to return the result. |
| [createWindow](arkts-arkui-window-createwindow-f.md) | Creates a child window or system window. This API uses a promise to return the result. |
| [create](arkts-arkui-window-create-f.md) | Creates a child window. This API uses an asynchronous callback to return the result. |
| [create](arkts-arkui-window-create-f.md) | Creates a child window. This API uses a promise to return the result. |
| [create](arkts-arkui-window-create-f.md) | Creates a system window. This API uses a promise to return the result. |
| [create](arkts-arkui-window-create-f.md) | Creates a system window. This API uses an asynchronous callback to return the result. |
| [find](arkts-arkui-window-find-f.md) | Finds a window based on the ID. This API uses an asynchronous callback to return the result. |
| [find](arkts-arkui-window-find-f.md) | Finds a window based on the ID. This API uses a promise to return the result. |
| [findWindow](arkts-arkui-window-findwindow-f.md) | Finds a window based on the name. |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md) | Obtains the top window of the current application. This API uses an asynchronous callback to return the result. |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md) | Obtains the top window of the current application. This API uses a promise to return the result. |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md) | Obtains the top window of the current application. This API uses a promise to return the result. |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md) | Obtains the top window of the current application. This API uses an asynchronous callback to return the result. |
| [getLastWindow](arkts-arkui-window-getlastwindow-f.md) | Obtains the topmost layer child window of the current application. This API uses an asynchronous callback to return the result. |
| [getLastWindow](arkts-arkui-window-getlastwindow-f.md) | Obtains the topmost layer child window of the current application. This API uses a promise to return the result. |
| [shiftAppWindowFocus](arkts-arkui-window-shiftappwindowfocus-f.md) | Shifts the window focus from the source window to the target window in the same application. The window focus can be shifted within the main window and child windows. This API uses a promise to return the result. |
| [shiftAppWindowPointerEvent](arkts-arkui-window-shiftappwindowpointerevent-f.md) | Transfers a mouse input event from one window to another within the same application. This API takes effect only for the main window and its child windows. This API uses a promise to return the result. |
| [shiftAppWindowTouchEvent](arkts-arkui-window-shiftappwindowtouchevent-f.md) | Transfers a touchscreen input event from one window to another within the same application. This API takes effect only for the main window and its child windows. This API uses a promise to return the result. |
| [getVisibleWindowInfo](arkts-arkui-window-getvisiblewindowinfo-f.md) | Obtains information about visible main windows on the current screen. Visible main windows are main windows that are not returned to the background. This API uses a promise to return the result. |
| [getWindowsByCoordinate](arkts-arkui-window-getwindowsbycoordinate-f.md) | Obtains visible windows at the specified coordinates within the current application, sorted by their current layer order. The window at the topmost layer corresponds to index 0 of the array. This API uses a promise to return the result. |
| [getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md) | Obtains the layout information array of all windows visible on a display. The layout information is arranged based on the current window stacking order, and the topmost window in the hierarchy is at index 0 of the array. This API uses a promise to return the result. |
| [getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md) | Obtains the array of window layout info visible on a specified screen. The width and height of each rect are calculated after scaling. The array is sorted by the current window level. The index of the array corresponding to the highest level is 0. |
| [getGlobalWindowMode](arkts-arkui-window-getglobalwindowmode-f.md) | Obtains the window mode of the window that is in the foreground lifecycle on the specified screen. This API uses a promise to return the result. |
| [onApplicationFocusStateChange](arkts-arkui-window-onapplicationfocusstatechange-f.md) | Register the callback for application process focus state changes. |
| [offApplicationFocusStateChange](arkts-arkui-window-offapplicationfocusstatechange-f.md) | Unregister the callback for application process focus state changes. |
| [setStartWindowBackgroundColor](arkts-arkui-window-setstartwindowbackgroundcolor-f.md) | Sets the background color of the splash screen of the UIAbility based on the specified module name and ability name within the same bundle name. This API uses a promise to return the result. |
| [setWatermarkImageForAppWindows](arkts-arkui-window-setwatermarkimageforappwindows-f.md) | Sets a watermark image for windows in the current application process. This API uses a promise to return the result. This API must be called after [loadContent()](arkts-arkui-window-window-i.md#loadcontent) or [setUIContent()](arkts-arkui-window-window-i.md#setuicontent) takes effect. |
| [getAllMainWindowInfo](arkts-arkui-window-getallmainwindowinfo-f.md) | Obtains the information about all main windows. This API uses a promise to return the result. |
| [getMainWindowSnapshot](arkts-arkui-window-getmainwindowsnapshot-f.md) | Obtains the screenshots of one or more main windows specified by **windowId**. This API uses a promise to return the result. |
| [setWindowPosition](arkts-arkui-window-setwindowposition-f.md) | Adjusts the position of one or more main windows in the current application process. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createSubWindowAndBindParent](arkts-arkui-window-createsubwindowandbindparent-f-sys.md) | Create a subwindow with a specific name and bind parent. The parent window only supports main window. The subwindow follows the parent window to show/hide, but does not follow the parent window to destroy. The subwindow listens to the parent window lifecycle changes through the callback function. |
| [minimizeAll](arkts-arkui-window-minimizeall-f-sys.md) | Minimizes all main windows on a display. |
| [minimizeAll](arkts-arkui-window-minimizeall-f-sys.md) | Minimizes all main windows on a display. This API uses a promise to return the result. |
| [minimizeAllWithExclusion](arkts-arkui-window-minimizeallwithexclusion-f-sys.md) | Minimizes all main windows on a display while keeping one window open. This API uses a promise to return the result. |
| [toggleShownStateForAllAppWindows](arkts-arkui-window-toggleshownstateforallappwindows-f-sys.md) | Hides or restores the application's windows during quick multi-window switching. This API uses an asynchronous callback to return the result. |
| [toggleShownStateForAllAppWindows](arkts-arkui-window-toggleshownstateforallappwindows-f-sys.md) | Hides or restores the application's windows during quick multi-window switching. This API uses a promise to return the result. |
| [setWindowLayoutMode](arkts-arkui-window-setwindowlayoutmode-f-sys.md) | Sets the window layout mode. This API uses an asynchronous callback to return the result. |
| [setWindowLayoutMode](arkts-arkui-window-setwindowlayoutmode-f-sys.md) | Sets the window layout mode. This API uses a promise to return the result. |
| [setGestureNavigationEnabled](arkts-arkui-window-setgesturenavigationenabled-f-sys.md) | Enables or disables gesture navigation. This API uses an asynchronous callback to return the result. For security purposes, the system does not interfere with the disabling and enabling of gesture navigation. If an application exits abnormally after it disables gesture navigation and wants to restore gesture navigation, it must implement automatic launch and call this API again to enable gesture navigation. |
| [setGestureNavigationEnabled](arkts-arkui-window-setgesturenavigationenabled-f-sys.md) | Enables or disables gesture navigation. This API uses a promise to return the result. For security purposes, the system does not interfere with the disabling and enabling of gesture navigation. If an application exits abnormally after it disables gesture navigation and wants to restore gesture navigation, it must implement automatic launch and call this API again to enable gesture navigation. |
| [setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md) | Controls whether a watermark image is displayed on the screen. This API uses a promise to return the result. |
| [setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md) | Set watermark image. |
| [setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md) | Controls whether a watermark image is displayed on the screen. This API uses an asynchronous callback to return the result. |
| [setSpecificSystemWindowZIndex](arkts-arkui-window-setspecificsystemwindowzindex-f-sys.md) | Sets the z-level of a system window. This API uses a promise to return the result. |
| [getTopNavDestinationName](arkts-arkui-window-gettopnavdestinationname-f-sys.md) | Obtains the name of NavDestination in the current top-level Navigation component of the specified foreground window. This API uses a promise to return the result. |
| [getSnapshot](arkts-arkui-window-getsnapshot-f-sys.md) | Obtains a snapshot of the same size as the specified window. This API uses a promise to return the result. If privacy mode is enabled for the current window (using [setWindowPrivacyMode](arkts-arkui-window-window-i.md#setwindowprivacymode)), taking a screenshot will result in a blank screen. |
| [on](arkts-arkui-window-on-f-sys.md#onsystembartintchange) | Subscribes to the property change event of the status bar and navigation bar. |
| [off](arkts-arkui-window-off-f-sys.md#offsystembartintchange) | Unsubscribes from the property change event of the status bar and navigation bar. |
| [on](arkts-arkui-window-on-f-sys.md#ongesturenavigationenabledchange) | Subscribes to the gesture navigation status change event. |
| [off](arkts-arkui-window-off-f-sys.md#offgesturenavigationenabledchange) | Unsubscribes from the gesture navigation status change event. |
| [on](arkts-arkui-window-on-f-sys.md#onwatermarkflagchange) | Subscribes to the watermark status change event. |
| [off](arkts-arkui-window-off-f-sys.md#offwatermarkflagchange) | Unsubscribes from the watermark status change event. |
| [notifyScreenshotEvent](arkts-arkui-window-notifyscreenshotevent-f-sys.md) | Notifies a screenshot event. This API uses a promise to return the result. |
| [moveMainWindowToTargetDisplay](arkts-arkui-window-movemainwindowtotargetdisplay-f-sys.md) | Move a window to the target display. The window must be a main window. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [SystemBarProperties](arkts-arkui-window-systembarproperties-i.md) | Describes the properties of the status bar<!--Del--> and three-button navigation bar<!--DelEnd-->. |
| [StatusBarProperty](arkts-arkui-window-statusbarproperty-i.md) | Describes the properties of the status bar. These properties are returned when you query the status bar's configuration details. |
| [SystemBarStyle](arkts-arkui-window-systembarstyle-i.md) | Describes the properties of the status bar. These properties are valid for the page-level status bar. |
| [FrameMetrics](arkts-arkui-window-framemetrics-i.md) | Enumerates the metrics for frame performance. |
| [Rect](arkts-arkui-window-rect-i.md) | Describes the rectangular area of the window. |
| [RectInVP](arkts-arkui-window-rectinvp-i.md) | Describes the rectangular area of the window, in vp. |
| [Position](arkts-arkui-window-position-i.md) | Describes the position of the window or component. |
| [AvoidArea](arkts-arkui-window-avoidarea-i.md) | Describes the area to avoid for window content. |
| [UIEnvAvoidAreaVP](arkts-arkui-window-uienvavoidareavp-i.md) | Describes the information about the window avoidance area in units of vp, which requires careful attention during [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout) adaptation. |
| [Size](arkts-arkui-window-size-i.md) | Describes the window size, in px. |
| [SizeInVP](arkts-arkui-window-sizeinvp-i.md) | Describes the window size, in vp. |
| [WindowInfo](arkts-arkui-window-windowinfo-i.md) | Describes the window information. |
| [WindowFocusState](arkts-arkui-window-windowfocusstate-i.md) | Describes the focus state change information of the window. |
| [WindowDensityInfo](arkts-arkui-window-windowdensityinfo-i.md) | Describes the information about the display density of the screen where the window is located and the window's custom display density. It is a scale factor independent of pixel units, that is, a factor for scaling display size. |
| [WindowProperties](arkts-arkui-window-windowproperties-i.md) | Describes the window properties. |
| [DecorButtonStyle](arkts-arkui-window-decorbuttonstyle-i.md) | Describes the button style of the system decoration bar. |
| [Configuration](arkts-arkui-window-configuration-i.md) | Defines the parameters for creating a child window or system window. |
| [WindowLimits](arkts-arkui-window-windowlimits-i.md) | Describes the parameters for window size limits. Applications can obtain the current window size limits (in px) via [getWindowLimits](arkts-arkui-window-window-i.md#getwindowlimits). Starting from API version 22, they can also be obtained via [getWindowLimitsVP](arkts-arkui-window-window-i.md#getwindowlimitsvp) (in vp). |
| [TitleButtonRect](arkts-arkui-window-titlebuttonrect-i.md) | Describes the rectangle used to hold the minimize, maximize, and close buttons on the title bar. This rectangle is located in the top-right corner of the window. |
| [RectChangeOptions](arkts-arkui-window-rectchangeoptions-i.md) | Describes the value and reason returned upon a window rectangle (position and size) change. |
| [AvoidAreaOptions](arkts-arkui-window-avoidareaoptions-i.md) | Describes the new area where the window cannot be displayed. The new area is returned when the corresponding event is triggered. |
| [UIEnvWindowAvoidAreaInfoPX](arkts-arkui-window-uienvwindowavoidareainfopx-i.md) | Describes [environment variable](../../../ui/arkts-env-system-property.md) data types for window avoidance areas of different types. All types of window avoidance areas are measured in px. |
| [UIEnvWindowAvoidAreaInfoVP](arkts-arkui-window-uienvwindowavoidareainfovp-i.md) | Describes [environment variable](../../../ui/arkts-env-system-property.md) data types for window avoidance areas of different types. All types of window avoidance areas are measured in vp. |
| [MainWindowInfo](arkts-arkui-window-mainwindowinfo-i.md) | Describes the main window information. |
| [WindowSnapshotConfiguration](arkts-arkui-window-windowsnapshotconfiguration-i.md) | Describes the configuration of the main window screenshot. |
| [WindowPositionParams](arkts-arkui-window-windowpositionparams-i.md) | Describes the position of a main window to adjust its z-order. |
| [OrientationResult](arkts-arkui-window-orientationresult-i.md) | Result of setting preferred orientation |
| [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md) | Describes the window information obtained during window rotation changes. |
| [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) | Describes the information returned by the application during window rotation changes. The system uses the information to adjust the size of the current window rectangle. If the returned information is about the rotation change of the main window, the system does not change the size of the main window. |
| [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md) | Describes the configuration for window animation. |
| [TransitionAnimation](arkts-arkui-window-transitionanimation-i.md) | Describes the window transition animation. |
| [MaximizeOptions](arkts-arkui-window-maximizeoptions-i.md) | Optional configuration for maximizing. |
| [MoveConfiguration](arkts-arkui-window-moveconfiguration-i.md) | Describes the window movement configuration. |
| [StartAnimationParams](arkts-arkui-window-startanimationparams-i.md) | Describes the parameters for the startup animation. |
| [WindowCreateParams](arkts-arkui-window-windowcreateparams-i.md) | Describes the window parameters during application startup. |
| [WindowSnapshotAnimationConfig](arkts-arkui-window-windowsnapshotanimationconfig-i.md) | Configuration for window snapshot animation. |
| [KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md) | Describes the information about the soft keyboard window. |
| [KeyFramePolicy](arkts-arkui-window-keyframepolicy-i.md) | Describes the configuration for keyframe policies. |
| [Window](arkts-arkui-window-window-i.md) | Represents a window instance, which is the basic unit managed by the window manager. |
| [ShowWindowOptions](arkts-arkui-window-showwindowoptions-i.md) | Describes the parameters for displaying a child window or system window. |
| [SubWindowOptions](arkts-arkui-window-subwindowoptions-i.md) | Describes the parameters used for creating a child window. |
| [WindowStage](arkts-arkui-window-windowstage-i.md) | Implements a window manager, which manages each basic window unit, that is, [Window](arkts-arkui-window-n.md) instance. |
| [WindowLayoutInfo](arkts-arkui-window-windowlayoutinfo-i.md) | Describes the information about the window layout. |
| [WindowInfoOptions](arkts-arkui-window-windowinfooptions-i.md) | Filter criteria for window information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [SystemBarRegionTint](arkts-arkui-window-systembarregiontint-i-sys.md) | Describes the callback for a single system bar. |
| [SystemBarTintState](arkts-arkui-window-systembartintstate-i-sys.md) | Describes the callback for the current system bar. |
| [WindowAnchorInfo](arkts-arkui-window-windowanchorinfo-i-sys.md) | Describes the anchor point information used to maintain the relative position between the level-1 child window and the main window. |
| [SubWindowAttachOptions](arkts-arkui-window-subwindowattachoptions-i-sys.md) | Describes the parameters used to maintain the relative position between the child window and the main window. |
| [ScaleOptions](arkts-arkui-window-scaleoptions-i-sys.md) | Describes the scale parameters. |
| [RotateOptions](arkts-arkui-window-rotateoptions-i-sys.md) | Describes the rotation parameters. |
| [TranslateOptions](arkts-arkui-window-translateoptions-i-sys.md) | Describes the translation parameters. |
| [TransitionContext](arkts-arkui-window-transitioncontext-i-sys.md) | Provides the context for the transition animation. |
| [TransitionController](arkts-arkui-window-transitioncontroller-i-sys.md) | Implements the transition animation controller. Before calling any API, you must create a system window. For details, see the sample code. |
| [Configuration](arkts-arkui-window-configuration-i-sys.md) | Defines the parameters for creating a child window or system window. |
| [StartMovingOptions](arkts-arkui-window-startmovingoptions-i-sys.md) | Optional configuration for startMovingWithOptions. |
| [StartAnimationSystemParams](arkts-arkui-window-startanimationsystemparams-i-sys.md) | Describes the start animation configuration. This API works only for full-screen applications. |
| [WindowCreateParams](arkts-arkui-window-windowcreateparams-i-sys.md) | Describes the window parameters during application startup. |
| [Window](arkts-arkui-window-window-i-sys.md) | Represents a window instance, which is the basic unit managed by the window manager. |
| [SubWindowOptions](arkts-arkui-window-subwindowoptions-i-sys.md) | Describes the parameters used for creating a child window. |
| [WindowStage](arkts-arkui-window-windowstage-i-sys.md) | Implements a window manager, which manages each basic window unit, that is, [Window](arkts-arkui-window-n.md) instance. |
| [SystemWindowOptions](arkts-arkui-window-systemwindowoptions-i-sys.md) | Describes the parameters for creating a system window. |
| [ExtensionWindowConfig](arkts-arkui-window-extensionwindowconfig-i-sys.md) | Describes the parameters for creating a window for a UI ServiceExtensionAbility. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [RotationChangeCallback](arkts-arkui-window-rotationchangecallback-t.md) | Describes a generic callback function for rotation event notifications. |
| [SpecificSystemBar](arkts-arkui-window-specificsystembar-t.md) | Defines the type of system bar that can be displayed or hidden. |

### Enums

| Name | Description |
| --- | --- |
| [WindowType](arkts-arkui-window-windowtype-e.md) | Enumerates the window types. |
| [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) | Enumerates the types of areas to avoid for window content. |
| [SplitRatioPreference](arkts-arkui-window-splitratiopreference-e.md) | Describes the type of split ratio preference. |
| [WindowStatusType](arkts-arkui-window-windowstatustype-e.md) | Enumerates the window modes. |
| [PixelUnit](arkts-arkui-window-pixelunit-e.md) | Enumerates the pixel units. |
| [WindowAnimationCurve](arkts-arkui-window-windowanimationcurve-e.md) | Enumerates the types of window animation curves. |
| [WindowTransitionType](arkts-arkui-window-windowtransitiontype-e.md) | Enumerates the types of window transition animations. |
| [AnimationType](arkts-arkui-window-animationtype-e.md) | Enumerates the types of window animations. |
| [WindowAnchor](arkts-arkui-window-windowanchor-e.md) | Enumerates the window anchor points. |
| [FocusChangeReason](arkts-arkui-window-focuschangereason-e.md) | Enumerates the reasons for the window focus state change. |
| [ColorSpace](arkts-arkui-window-colorspace-e.md) | Enumerates the color spaces. |
| [RectChangeReason](arkts-arkui-window-rectchangereason-e.md) | Enumerates the reasons for window rectangle (position and size) changes. |
| [OcclusionState](arkts-arkui-window-occlusionstate-e.md) | Enumerates the window visibility states. |
| [WindowPosition](arkts-arkui-window-windowposition-e.md) | Enumerates the target z-order to which the z-order of a main window can be adjusted. |
| [Orientation](arkts-arkui-window-orientation-e.md) | Enumerates the window orientations. <!--Del-->For details of the differences between different enumerated values, see [What is the difference between orientation values 8 to 10 or 12 and values 13 to 16 (API version 9)](../../../faqs/faqs-window-manager.md#what-is-the-difference-between-orientation-values-8-to-10-or-12-and-values-13-to-16-api-version-9).<!--DelEnd--> |
| [OrientationExecutionResult](arkts-arkui-window-orientationexecutionresult-e.md) | Type of execution result of setting preferred orientation |
| [RotationChangeType](arkts-arkui-window-rotationchangetype-e.md) | Enumerates the types of window rotation events. |
| [RectType](arkts-arkui-window-recttype-e.md) | Enumerates the types of window rectangle coordinate systems. |
| [ScreenshotEventType](arkts-arkui-window-screenshoteventtype-e.md) | Enumerates the screenshot event types. |
| [RotationInfoType](arkts-arkui-window-rotationinfotype-e.md) | Enumerates the types of rotation information. |
| [WindowEventType](arkts-arkui-window-windoweventtype-e.md) | Enumerates the window lifecycle states. |
| [MaximizePresentation](arkts-arkui-window-maximizepresentation-e.md) | Enumerates the layout when the window is maximized. |
| [AcrossDisplayPresentation](arkts-arkui-window-acrossdisplaypresentation-e.md) | Enum for across-display policy used when maximizing in the half-folded state of a foldable 2-in-1 device. |
| [GlobalWindowMode](arkts-arkui-window-globalwindowmode-e.md) | Enumerates the window modes. |
| [WindowStageEventType](arkts-arkui-window-windowstageeventtype-e.md) | Enumerates the lifecycle event types of a WindowStage. |
| [WindowStageLifecycleEventType](arkts-arkui-window-windowstagelifecycleeventtype-e.md) | Enumerates the lifecycle state types of a WindowStage. |
| [ModalityType](arkts-arkui-window-modalitytype-e.md) | Enumerates the modality types of the child window. |
| [WindowPostureMode](arkts-arkui-window-windowposturemode-e.md) | Enumerates of window posture mode. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [WindowType](arkts-arkui-window-windowtype-e-sys.md) | Enumerates the window types. |
| [WindowMode](arkts-arkui-window-windowmode-e-sys.md) | Enumerates the window modes. |
| [WindowLayoutMode](arkts-arkui-window-windowlayoutmode-e-sys.md) | Enumerates the window layout modes. |
| [AnimationType](arkts-arkui-window-animationtype-e-sys.md) | Enumerates the types of window animations. |
| [BlurStyle](arkts-arkui-window-blurstyle-e-sys.md) | Enumerates the window blur styles. |
| [ExtensionWindowAttribute](arkts-arkui-window-extensionwindowattribute-e-sys.md) | Enumerates the attributes of a window for a UI ServiceExtensionAbility. |
<!--DelEnd-->
