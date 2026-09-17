# @ohos.screen

The module implements basic screen management. You can use the APIs of this module to obtain a Screen object, listen for screen changes, and create and destroy virtual screens.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createVirtualScreen](arkts-arkui-screen-createvirtualscreen-f-sys.md) | Creates a virtual screen. This API uses an asynchronous callback to return the result. |
| [createVirtualScreen](arkts-arkui-screen-createvirtualscreen-f-sys.md) | Creates a virtual screen. This API uses a promise to return the result. |
| [destroyVirtualScreen](arkts-arkui-screen-destroyvirtualscreen-f-sys.md) | Destroys a virtual screen. This API uses an asynchronous callback to return the result. |
| [destroyVirtualScreen](arkts-arkui-screen-destroyvirtualscreen-f-sys.md) | Destroys a virtual screen. This API uses a promise to return the result. |
| [getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md) | Obtains all screens. This API uses an asynchronous callback to return the result. |
| [getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md) | Obtains all screens. This API uses an asynchronous callback to return the result. |
| [getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md) | Obtains all screens. This API uses a promise to return the result. |
| [getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md) | Obtains all screens. This API uses a promise to return the result. |
| [isScreenRotationLocked](arkts-arkui-screen-isscreenrotationlocked-f-sys.md) | Checks whether auto rotate is locked. This API uses an asynchronous callback to return the result. |
| [isScreenRotationLocked](arkts-arkui-screen-isscreenrotationlocked-f-sys.md) | Checks whether auto rotate is locked. This API uses a promise to return the result. |
| [makeExpand](arkts-arkui-screen-makeexpand-f-sys.md) | Sets the screen to extended mode. This API uses an asynchronous callback to return the result. |
| [makeExpand](arkts-arkui-screen-makeexpand-f-sys.md) | Sets the screen to extended mode. This API uses a promise to return the result. |
| [makeMirror](arkts-arkui-screen-makemirror-f-sys.md) | Sets the screen to mirror mode. This API uses an asynchronous callback to return the result. |
| [makeMirror](arkts-arkui-screen-makemirror-f-sys.md) | Sets the screen to mirror mode. This API uses a promise to return the result. |
| [makeMirrorWithRegion](arkts-arkui-screen-makemirrorwithregion-f-sys.md) | Sets a rectangle on the screen to mirror mode. This API uses a promise to return the result. After this API is called, you are advised not to rotate or fold the screen further. Otherwise, the mirrored content may be abnormal. |
| [makeUnique](arkts-arkui-screen-makeunique-f-sys.md) | Sets the screen to independent display mode. This API uses a promise to return the result. |
| [off](arkts-arkui-screen-off-f-sys.md) | Unsubscribes from events related to the screen state. |
| [off](arkts-arkui-screen-off-f-sys.md) | Unsubscribes from events related to the screen state. |
| [off](arkts-arkui-screen-off-f-sys.md) | Unsubscribes from events related to the screen state. |
| [on](arkts-arkui-screen-on-f-sys.md) | Subscribes to events related to the screen state. |
| [on](arkts-arkui-screen-on-f-sys.md) | Subscribes to events related to the screen state. |
| [on](arkts-arkui-screen-on-f-sys.md) | Subscribes to events related to the screen state. |
| [resizeVirtualScreen](arkts-arkui-screen-resizevirtualscreen-f-sys.md) | Resizes the virtual screen. This API uses a promise to return the result. |
| [setMultiScreenMode](arkts-arkui-screen-setmultiscreenmode-f-sys.md) | Sets the display mode (mirror or extend) of the secondary screen. This API uses a promise to return the result. If both **primaryScreenId** and **secondaryScreenId** are set to **0**, the content is displayed only on the secondary screen. |
| [setMultiScreenRelativePosition](arkts-arkui-screen-setmultiscreenrelativeposition-f-sys.md) | Sets the positions of the primary and secondary screens in extend mode. This API uses a promise to return the result. |
| [setScreenPrivacyMaskImage](arkts-arkui-screen-setscreenprivacymaskimage-f-sys.md) | Sets a privacy mask image for the screen. This API uses a promise to return the result. |
| [setScreenRotationLocked](arkts-arkui-screen-setscreenrotationlocked-f-sys.md) | Sets whether to lock auto rotate. This API uses an asynchronous callback to return the result. |
| [setScreenRotationLocked](arkts-arkui-screen-setscreenrotationlocked-f-sys.md) | Sets whether to lock auto rotate. This API uses a promise to return the result. |
| [setVirtualScreenSurface](arkts-arkui-screen-setvirtualscreensurface-f-sys.md) | Sets a surface for a virtual screen. This API uses an asynchronous callback to return the result. |
| [setVirtualScreenSurface](arkts-arkui-screen-setvirtualscreensurface-f-sys.md) | Sets a surface for a virtual screen. This API uses a promise to return the result. |
| [stopExpand](arkts-arkui-screen-stopexpand-f-sys.md) | Stops extended mode. This API uses an asynchronous callback to return the result. |
| [stopExpand](arkts-arkui-screen-stopexpand-f-sys.md) | Stops extended mode. This API uses a promise to return the result. |
| [stopMirror](arkts-arkui-screen-stopmirror-f-sys.md) | Stops mirror mode. This API uses an asynchronous callback to return the result. |
| [stopMirror](arkts-arkui-screen-stopmirror-f-sys.md) | Stops mirror mode. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ExpandOption](arkts-arkui-screen-expandoption-i-sys.md) | Defines the parameters for expanding a screen. |
| [MultiScreenPositionOptions](arkts-arkui-screen-multiscreenpositionoptions-i-sys.md) | Describes the screen position information. |
| [OrientationOptions](arkts-arkui-screen-orientationoptions-i-sys.md) | The parameters for setting orientation |
| [Rect](arkts-arkui-screen-rect-i-sys.md) | Describes the rectangle information. |
| [Screen](arkts-arkui-screen-screen-i-sys.md) | Defines the [physical screen](../../../displaymanager/display-terminology.md#physical-screen) instance. |
| [ScreenModeInfo](arkts-arkui-screen-screenmodeinfo-i-sys.md) | Defines the screen mode information. |
| [VirtualScreenOption](arkts-arkui-screen-virtualscreenoption-i-sys.md) | Defines virtual screen parameters. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [MultiScreenMode](arkts-arkui-screen-multiscreenmode-e-sys.md) | Enumerates the display modes of secondary screens. |
| [Orientation](arkts-arkui-screen-orientation-e-sys.md) | Enumerates the screen orientations. |
| [ScreenSourceMode](arkts-arkui-screen-screensourcemode-e-sys.md) | Enumerates the sources of the content displayed on the screen. |
| [ScreenType](arkts-arkui-screen-screentype-e-sys.md) | Enumerates the types of screens. |
<!--DelEnd-->
