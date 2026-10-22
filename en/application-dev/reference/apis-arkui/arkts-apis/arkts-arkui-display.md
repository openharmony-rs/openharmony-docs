# @ohos.display

The **Display** module provides APIs for managing displays, such as obtaining information about the default display, obtaining information about all displays, and listening for the addition and removal of displays.

**Since:** 7

<!--Device-unnamed-declare namespace display--><!--Device-unnamed-declare namespace display-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [convertGlobalToRelativeCoordinate](arkts-arkui-display-convertglobaltorelativecoordinate-f.md#convertglobaltorelativecoordinate-1) | Converts global coordinates (based on the top-left corner of the primary screen) into relative coordinates (based on the top-left corner of the screen specified by **displayId**). This API supports only coordinate conversion between the primary screen and extended screen. If **displayId** is not passed, the coordinates are converted relative to the screen where the global coordinates are located. If the global coordinates are not on any screen, the coordinates are converted relative to the primary screen by default. |
| [convertRelativeToGlobalCoordinate](arkts-arkui-display-convertrelativetoglobalcoordinate-f.md#convertrelativetoglobalcoordinate-1) | Converts relative coordinates (based on the top-left corner of the screen) into global coordinates (based on the top-left corner of the primary screen). This API supports only coordinate conversion between the primary screen and extended screen. |
| [createVirtualScreen](arkts-arkui-display-createvirtualscreen-f.md#createvirtualscreen-1) | Creates a virtual screen. This API uses a promise to return the result. |
| [destroyVirtualScreen](arkts-arkui-display-destroyvirtualscreen-f.md#destroyvirtualscreen-1) | Destroys a virtual screen. This API uses a promise to return the result. |
| [getAllDisplayPhysicalResolution](arkts-arkui-display-getalldisplayphysicalresolution-f.md#getalldisplayphysicalresolution-1) | Obtains all the display modes supported by the current device, along with the physical screen resolutions for each mode. This API uses a promise to return the result. |
| [getAllDisplays](arkts-arkui-display-getalldisplays-f.md#getalldisplays-1) | Obtains all Display objects. This API uses an asynchronous callback to return the result. |
| [getAllDisplays](arkts-arkui-display-getalldisplays-f.md#getalldisplays-2) | Obtains all Display objects. This API uses a promise to return the result. |
| [getBrightnessInfo](arkts-arkui-display-getbrightnessinfo-f.md#getbrightnessinfo-1) | Obtains the screen brightness information of a display. If the screen does not support HDR, the **currentHeadroom** and **maxHeadroom** fields in the returned [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md) object use the default values. For virtual screens, the **sdrNits** field in the BrightnessInfo object uses the default value. |
| [getCurrentFoldCreaseRegion](arkts-arkui-display-getcurrentfoldcreaseregion-f.md#getcurrentfoldcreaseregion-1) | Obtains the crease region of the foldable device in the current display mode. |
| [getDefaultDisplaySync](arkts-arkui-display-getdefaultdisplaysync-f.md#getdefaultdisplaysync-1) | Obtains the **Display** object of the screen where the application is located. If multiple abilities of an application are on different screens, the **Display** object of the main screen is returned. If multiple abilities of an application are on the same screen, the **Display** object of the screen is returned. |
| [getDisplayByIdSync](arkts-arkui-display-getdisplaybyidsync-f.md#getdisplaybyidsync-1) | Obtains a Display object based on the display ID. |
| [getFoldDisplayMode](arkts-arkui-display-getfolddisplaymode-f.md#getfolddisplaymode-1) | Obtains the display mode of this foldable device. |
| [getFoldStatus](arkts-arkui-display-getfoldstatus-f.md#getfoldstatus-1) | Obtains the fold status of this foldable device. |
| [getPrimaryDisplaySync](arkts-arkui-display-getprimarydisplaysync-f.md#getprimarydisplaysync-1) | Obtains the information about the primary display. For devices other than 2-in-1 devices, the Display object obtained is the built-in screen. For 2-in-1 devices with an external screen, the Display object obtained is the primary screen. For 2-in-1 devices without an external screen, the Display object obtained is the built-in screen. |
| [isCaptured](arkts-arkui-display-iscaptured-f.md#iscaptured-1) | Checks whether the device's screen content is being captured. |
| [isCaptured](arkts-arkui-display-iscaptured-f.md#iscaptured-2) | Check whether the device is captured, projected, or recorded by any app in the bundle name list. |
| [isFoldable](arkts-arkui-display-isfoldable-f.md#isfoldable-1) | Checks whether this device is foldable. |
| [makeUnique](arkts-arkui-display-makeunique-f.md#makeunique-1) | Sets the screen to independent display mode. This API uses a promise to return the result. |
| [off('add' | 'remove' | 'change')](arkts-arkui-display-off-f.md#offadd-remove-change) | Unsubscribes from display changes. |
| [off('add' | 'remove' | 'change')](arkts-arkui-display-off-f.md#offadd-remove-change) | Unsubscribes from display changes. |
| [off('add' | 'remove' | 'change')](arkts-arkui-display-off-f.md#offadd-remove-change) | Unsubscribes from display changes. |
| [off('foldStatusChange')](arkts-arkui-display-off-f.md#offfoldstatuschange) | Unsubscribes from fold status change events of the foldable device. |
| [off('foldAngleChange')](arkts-arkui-display-off-f.md#offfoldanglechange) | Unsubscribes from folding angle change events of the foldable device. |
| [off('captureStatusChange')](arkts-arkui-display-off-f.md#offcapturestatuschange) | Unsubscribes from events indicating the status of the device's screen content is being captured. |
| [off('foldDisplayModeChange')](arkts-arkui-display-off-f.md#offfolddisplaymodechange) | Unsubscribes from display mode change events of the foldable device. |
| [off('brightnessInfoChange')](arkts-arkui-display-off-f.md#offbrightnessinfochange) | Unsubscribes from events related to screen brightness information changes. |
| [on('add' | 'remove' | 'change')](arkts-arkui-display-on-f.md#onadd-remove-change) | Subscribes to display changes. |
| [on('add' | 'remove' | 'change')](arkts-arkui-display-on-f.md#onadd-remove-change) | Subscribes to display changes. |
| [on('add' | 'remove' | 'change')](arkts-arkui-display-on-f.md#onadd-remove-change) | Subscribes to display changes. |
| [on('foldStatusChange')](arkts-arkui-display-on-f.md#onfoldstatuschange) | Subscribes to fold status change events of the foldable device. |
| [on('foldAngleChange')](arkts-arkui-display-on-f.md#onfoldanglechange) | Subscribes to folding angle change events of the foldable device. Note that there are two folding angles for dual- fold axis devices. When oriented with the charging port at the bottom, the hinges are identified from right to left as the first and second fold axes, respectively. |
| [on('captureStatusChange')](arkts-arkui-display-on-f.md#oncapturestatuschange) | Subscribes to events indicating the status of the device's screen content is being captured. |
| [on('foldDisplayModeChange')](arkts-arkui-display-on-f.md#onfolddisplaymodechange) | Subscribes to display mode change events of the foldable device. |
| [on('brightnessInfoChange')](arkts-arkui-display-on-f.md#onbrightnessinfochange) | Subscribes to events related to screen brightness information changes. If the screen does not support HDR, the **currentHeadroom** and **maxHeadroom** fields in the [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md) object use the default values. For virtual screens, the **sdrNits** field in the BrightnessInfo object uses the default value. |
| [onChangeWithAttribute](arkts-arkui-display-onchangewithattribute-f.md#onchangewithattribute-1) | Subscribes to changes of specified attributes of a display. |
| [setVirtualScreenSurface](arkts-arkui-display-setvirtualscreensurface-f.md#setvirtualscreensurface-1) | Sets a surface for a virtual screen. This API uses a promise to return the result. |
| [getAllDisplay](arkts-arkui-display-getalldisplay-f.md#getalldisplay-1) | Obtains all Display objects. This API uses an asynchronous callback to return the result. |
| [getAllDisplay](arkts-arkui-display-getalldisplay-f.md#getalldisplay-2) | Obtains all Display objects. This API uses a promise to return the result. |
| [getDefaultDisplay](arkts-arkui-display-getdefaultdisplay-f.md#getdefaultdisplay-1) | Obtains the default Display object. This API uses an asynchronous callback to return the result. |
| [getDefaultDisplay](arkts-arkui-display-getdefaultdisplay-f.md#getdefaultdisplay-2) | Obtains the default Display object. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addVirtualScreenBlocklist](arkts-arkui-display-addvirtualscreenblocklist-f-sys.md#addvirtualscreenblocklist-1) | Adds windows to the list of windows that are not allowed to be displayed during casting. This API takes effect only for the main window of an application or system windows. This API uses a promise to return the result. |
| [addVirtualScreenSurface](arkts-arkui-display-addvirtualscreensurface-f-sys.md#addvirtualscreensurface-1) | Add surface for the virtual screen. |
| [hasPrivateWindow](arkts-arkui-display-hasprivatewindow-f-sys.md#hasprivatewindow-1) | Checks whether there is a visible privacy window on a display. The window privacy mode can be set by calling setWindowPrivacyMode(). The content in the privacy window cannot be captured or recorded. |
| [off('privateModeChange')](arkts-arkui-display-off-f-sys.md#offprivatemodechange) | Unsubscribes from privacy mode changes of this display. |
| [on('privateModeChange')](arkts-arkui-display-on-f-sys.md#onprivatemodechange) | Subscribes to privacy mode changes of this display. When there is a privacy window in the foreground of the display, the display is in privacy mode, and the content in the privacy window cannot be captured or recorded. |
| [removeVirtualScreenBlocklist](arkts-arkui-display-removevirtualscreenblocklist-f-sys.md#removevirtualscreenblocklist-1) | Removes windows from the list of windows that are not allowed to be displayed during casting. This API takes effect only for the main window of an application or system windows. This API uses a promise to return the result. |
| [removeVirtualScreenSurface](arkts-arkui-display-removevirtualscreensurface-f-sys.md#removevirtualscreensurface-1) | Remove surface for the virtual screen. |
| [setFoldDisplayMode](arkts-arkui-display-setfolddisplaymode-f-sys.md#setfolddisplaymode-1) | Sets the display mode of the foldable device. |
| [setFoldDisplayMode](arkts-arkui-display-setfolddisplaymode-f-sys.md#setfolddisplaymode-2) | Sets the display mode of the foldable device, with the reason for the change specified. |
| [setFoldStatusLocked](arkts-arkui-display-setfoldstatuslocked-f-sys.md#setfoldstatuslocked-1) | Sets whether to lock the current fold status of the foldable device. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md) | Describes the screen brightness information. The information comes from the underlying screen data. |
| [CutoutInfo](arkts-arkui-display-cutoutinfo-i.md) | Describes the unusable area of a display, including punch hole, notch, and curved area of a waterfall display. |
| [Display](arkts-arkui-display-display-i.md) | Implements a Display instance, with attributes and APIs defined. |
| [DisplayPhysicalResolution](arkts-arkui-display-displayphysicalresolution-i.md) | Describes the display mode of a device and the corresponding physical screen resolution information. |
| [FoldCreaseRegion](arkts-arkui-display-foldcreaseregion-i.md) | Describes the crease region of a foldable device. |
| [Position](arkts-arkui-display-position-i.md) | Describes a coordinate position. In the global coordinate system, the origin is the top-left corner of the primary screen. In the relative coordinate system, the origin is the top-left corner of the specified screen. |
| [Rect](arkts-arkui-display-rect-i.md) | Describes a rectangle on the display. |
| [RelativePosition](arkts-arkui-display-relativeposition-i.md) | Describes a coordinate position in the relative coordinate system, with the origin in the top-left corner of the screen specified by **displayId**. |
| [RoundedCorner](arkts-arkui-display-roundedcorner-i.md) | Describes a single rounded corner on the screen. |
| [VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md) | Describes the virtual screen parameters. |
| [WaterfallDisplayAreaRects](arkts-arkui-display-waterfalldisplayarearects-i.md) | Describes the curved area on a waterfall display. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Display](arkts-arkui-display-display-i-sys.md) | Implements a Display instance, with attributes and APIs defined. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [BrightnessCallback](arkts-arkui-display-brightnesscallback-t.md) | Defines the callback function used to listen for screen brightness information. |

### Enums

| Name | Description |
| --- | --- |
| [CornerType](arkts-arkui-display-cornertype-e.md) | Enumerates the types of corners on the screen. |
| [DisplaySourceMode](arkts-arkui-display-displaysourcemode-e.md) | Enumerates the display modes for screen content. |
| [DisplayState](arkts-arkui-display-displaystate-e.md) | Enumerates the states of a display. |
| [FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md) | Enumerates the display modes of a foldable device. |
| [FoldStatus](arkts-arkui-display-foldstatus-e.md) | Enumerates the fold statuses of a foldable device. For dual-fold axis devices, when oriented with the charging port at the bottom, the hinges are identified from right to left as the first and second fold axes, respectively. |
| [Orientation](arkts-arkui-display-orientation-e.md) | Enumerates the orientations of a display. |
| [ScreenShape](arkts-arkui-display-screenshape-e.md) | Enumerates the screen shapes of a display. |
