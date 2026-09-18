# @ohos.wallpaper(Wallpaper)

System wallpaper

@namespace wallpaper

**Since:** 7

**System capability:** SystemCapability.MiscServices.Wallpaper

## Modules to Import

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getColors](arkts-basicservices-wallpaper-getcolors-f.md) | Obtains the wallpaper colors for the wallpaper of the specified type. Returns rgbaColor type of array callback function. |
| [getColors](arkts-basicservices-wallpaper-getcolors-f.md) | Obtains the wallpaper colors for the wallpaper of the specified type. Returns rgbaColor type of array callback function. |
| [getFile](arkts-basicservices-wallpaper-getfile-f.md) | Obtains a file of the wallpaper of the specified type. Returns the file descriptor. When usage is complete, the caller needs to close the file descriptor in time. |
| [getFile](arkts-basicservices-wallpaper-getfile-f.md) | Obtains a file of the wallpaper of the specified type. Returns the file descriptor. When usage is complete, the caller needs to close the file descriptor in time. |
| [getId](arkts-basicservices-wallpaper-getid-f.md) | Obtains the ID of the wallpaper of the specified type. Returns an integer greater than or equal to `0` representing the wallpaper ID. if the specified type of wallpaper has been set; returns `-1` otherwise. The return value is an integer ranging from -1 to 2^31 - 1. |
| [getId](arkts-basicservices-wallpaper-getid-f.md) | Obtains the ID of the wallpaper of the specified type. Returns an integer greater than or equal to `0` representing the wallpaper ID. if the specified type of wallpaper has been set; returns `-1` otherwise. The return value is an integer ranging from -1 to 2^31 - 1. |
| [getMinHeight](arkts-basicservices-wallpaper-getminheight-f.md) | Obtains the minimum height of the wallpaper. in pixels. returns 0 if no wallpaper has been set. |
| [getMinHeight](arkts-basicservices-wallpaper-getminheight-f.md) | Obtains the minimum height of the wallpaper. in pixels. returns 0 if no wallpaper has been set. |
| [getMinWidth](arkts-basicservices-wallpaper-getminwidth-f.md) | Obtains the minimum width of the wallpaper. in pixels. returns 0 if no wallpaper has been set. |
| [getMinWidth](arkts-basicservices-wallpaper-getminwidth-f.md) | Obtains the minimum width of the wallpaper. in pixels. returns 0 if no wallpaper has been set. |
| [isChangePermitted](arkts-basicservices-wallpaper-ischangepermitted-f.md) | Checks whether to allow the application to change the wallpaper for the current user. Returns true if the application is allowed to set a wallpaper for the current user. returns false otherwise. |
| [isChangePermitted](arkts-basicservices-wallpaper-ischangepermitted-f.md) | Checks whether to allow the application to change the wallpaper for the current user. Returns true if the application is allowed to set a wallpaper for the current user. returns false otherwise. |
| [isOperationAllowed](arkts-basicservices-wallpaper-isoperationallowed-f.md) | Checks whether a user is allowed to set wallpapers. Returns true if a user is allowed to set wallpapers. returns false otherwise. |
| [isOperationAllowed](arkts-basicservices-wallpaper-isoperationallowed-f.md) | Checks whether a user is allowed to set wallpapers. Returns true if a user is allowed to set wallpapers. returns false otherwise. |
| [off](arkts-basicservices-wallpaper-off-f.md#offcolorchange) | Unregisters a listener for wallpaper color changes. |
| [on](arkts-basicservices-wallpaper-on-f.md#oncolorchange) | Registers a listener for wallpaper color changes to receive notifications about the changes. |
| [reset](arkts-basicservices-wallpaper-reset-f.md) | Removes a wallpaper of the specified type and restores the default one. |
| [reset](arkts-basicservices-wallpaper-reset-f.md) | Removes a wallpaper of the specified type and restores the default one. |
| [setWallpaper](arkts-basicservices-wallpaper-setwallpaper-f.md) | Sets a wallpaper of the specified type based on the uri path from a JPEG or PNG file or the pixel map of a PNG file. |
| [setWallpaper](arkts-basicservices-wallpaper-setwallpaper-f.md) | Sets a wallpaper of the specified type based on the uri path from a JPEG or PNG file or the pixel map of a PNG file. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getColorsSync](arkts-basicservices-wallpaper-getcolorssync-f-sys.md) | Obtains the wallpaper colors for the wallpaper of the specified type. Returns rgbaColor type of array callback function. |
| [getImage](arkts-basicservices-wallpaper-getimage-f-sys.md) | Obtains the default pixel map of a wallpaper of the specified type. Returns the default pixel map. Only the static wallpaper set by using setImage can be obtained. |
| [getImage](arkts-basicservices-wallpaper-getimage-f-sys.md) | Obtains the default pixel map of a wallpaper of the specified type. Returns the default pixel map. Only the static wallpaper set by using setImage can be obtained. |
| [getMinHeightSync](arkts-basicservices-wallpaper-getminheightsync-f-sys.md) | Obtains the minimum height of the wallpaper. in pixels. returns 0 if no wallpaper has been set. |
| [getMinWidthSync](arkts-basicservices-wallpaper-getminwidthsync-f-sys.md) | Obtains the minimum width of the wallpaper. in pixels. returns 0 if no wallpaper has been set. |
| [getPixelMap](arkts-basicservices-wallpaper-getpixelmap-f-sys.md) | Obtains the default pixel map of a wallpaper of the specified type. Returns the default pixel map. |
| [getPixelMap](arkts-basicservices-wallpaper-getpixelmap-f-sys.md) | Obtains the default pixel map of a wallpaper of the specified type. Returns the default pixel map. |
| [getWallpaperByState](arkts-basicservices-wallpaper-getwallpaperbystate-f-sys.md) | Obtains the default pixel map of a wallpaper of the specified device type. Returns the default pixel map. Only the static wallpaper set by using setAllWallpapers can be obtained. |
| [off](arkts-basicservices-wallpaper-off-f-sys.md#offwallpaperchange) | Unregisters a listener for wallpaper changes. |
| [on](arkts-basicservices-wallpaper-on-f-sys.md#onwallpaperchange) | Registers a listener for wallpaper changes to receive notifications about the changes. |
| [restore](arkts-basicservices-wallpaper-restore-f-sys.md) | Removes a wallpaper of the specified type and restores the default one. |
| [restore](arkts-basicservices-wallpaper-restore-f-sys.md) | Removes a wallpaper of the specified type and restores the default one. |
| [setAllWallpapers](arkts-basicservices-wallpaper-setallwallpapers-f-sys.md) | Set wallpapers for all forms of devices. |
| [setCustomWallpaper](arkts-basicservices-wallpaper-setcustomwallpaper-f-sys.md) | Sets wallpaper of the specified type based on the uri path of the custom wallpaper. |
| [setCustomWallpaper](arkts-basicservices-wallpaper-setcustomwallpaper-f-sys.md) | Sets wallpaper of the specified type based on the uri path of the custom wallpaper. |
| [setImage](arkts-basicservices-wallpaper-setimage-f-sys.md) | Sets a wallpaper of the specified type based on the uri path from a JPEG or PNG file or the pixel map of a PNG file. |
| [setImage](arkts-basicservices-wallpaper-setimage-f-sys.md) | Sets a wallpaper of the specified type based on the uri path from a JPEG or PNG file or the pixel map of a PNG file. |
| [setVideo](arkts-basicservices-wallpaper-setvideo-f-sys.md) | Sets live wallpaper of the specified type based on the uri path of the MP4 file. |
| [setVideo](arkts-basicservices-wallpaper-setvideo-f-sys.md) | Sets live wallpaper of the specified type based on the uri path of the MP4 file. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [RgbaColor](arkts-basicservices-wallpaper-rgbacolor-i.md) | RgbaColor definition |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [WallpaperInfo](arkts-basicservices-wallpaper-wallpaperinfo-i-sys.md) | WallpaperInfo definition including folding status, rotation status, and resource path. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | Indicates wallpaper type. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [FoldState](arkts-basicservices-wallpaper-foldstate-e-sys.md) | Define the folding state of wallpaper |
| [RotateState](arkts-basicservices-wallpaper-rotatestate-e-sys.md) | Define the rotation state of wallpaper |
| [WallpaperResourceType](arkts-basicservices-wallpaper-wallpaperresourcetype-e-sys.md) | Indicates the resource type of the wallpaper. |
<!--DelEnd-->
