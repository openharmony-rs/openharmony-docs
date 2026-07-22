# @ohos.wallpaper

壁纸管理服务为OpenHarmony系统服务，提供壁纸切换功能。从API 9开始壁纸管理的接口调整为系统API，壁纸的切换只能通过系统应用来完成。壁纸管理提供壁纸切换通道，使用壁纸的应用（如：桌面）需订阅壁纸变化通知并刷新壁纸显示。
> **说明：**  
>  
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.wallpaper (壁纸)](arkts-wallpaper.md)。

**起始版本：** 7

<!--Device-unnamed-declare namespace wallpaper--><!--Device-unnamed-declare namespace wallpaper-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getColors](arkts-na-wallpaper-getcolors-f.md#getcolors) | 获取指定类型壁纸的主要颜色信息。 |
| [getColors](arkts-na-wallpaper-getcolors-f.md#getcolors-1) | 获取指定类型壁纸的主要颜色信息。 |
| [getFile](arkts-na-wallpaper-getfile-f.md#getfile) | 获取指定类型的壁纸文件。 |
| [getFile](arkts-na-wallpaper-getfile-f.md#getfile-1) | 获取指定类型的壁纸文件。 |
| [getId](arkts-na-wallpaper-getid-f.md#getid) | 获取指定类型壁纸的ID。 |
| [getId](arkts-na-wallpaper-getid-f.md#getid-1) | 获取指定类型壁纸的ID。 |
| [getMinHeight](arkts-na-wallpaper-getminheight-f.md#getminheight) | 获取壁纸的最小高度值。 |
| [getMinHeight](arkts-na-wallpaper-getminheight-f.md#getminheight-1) | 获取壁纸的最小高度值。 |
| [getMinWidth](arkts-na-wallpaper-getminwidth-f.md#getminwidth) | 获取壁纸的最小宽度值。 |
| [getMinWidth](arkts-na-wallpaper-getminwidth-f.md#getminwidth-1) | 获取壁纸的最小宽度值。 |
| [isChangePermitted](arkts-na-wallpaper-ischangepermitted-f.md#ischangepermitted) | 是否允许应用改变当前用户的壁纸。 |
| [isChangePermitted](arkts-na-wallpaper-ischangepermitted-f.md#ischangepermitted-1) | 是否允许应用改变当前用户的壁纸。 |
| [isOperationAllowed](arkts-na-wallpaper-isoperationallowed-f.md#isoperationallowed) | 是否允许用户设置壁纸。 |
| [isOperationAllowed](arkts-na-wallpaper-isoperationallowed-f.md#isoperationallowed-1) | 是否允许用户设置壁纸。 |
| [off](arkts-na-wallpaper-off-f.md#off) | 取消订阅壁纸颜色变化结果上报事件。不支持多线程并发调用。 |
| [on](arkts-na-wallpaper-on-f.md#on) | 订阅壁纸颜色变化结果上报事件。不支持多线程并发调用。 |
| [reset](arkts-na-wallpaper-reset-f.md#reset) | 移除指定类型的壁纸，恢复为默认显示的壁纸。 |
| [reset](arkts-na-wallpaper-reset-f.md#reset-1) | 移除指定类型的壁纸，恢复为默认显示的壁纸。 |
| [setWallpaper](arkts-na-wallpaper-setwallpaper-f.md#setwallpaper) | 将指定资源设置为指定类型的壁纸。 |
| [setWallpaper](arkts-na-wallpaper-setwallpaper-f.md#setwallpaper-1) | 将指定资源设置为指定类型的壁纸。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getColorsSync](arkts-na-wallpaper-getcolorssync-f-sys.md#getcolorssync) | 获取指定类型壁纸的主要颜色信息。 |
| [getImage](arkts-na-wallpaper-getimage-f-sys.md#getimage) | 获取壁纸图片的像素图，且只能获取使用setImage设置的静态壁纸。使用callback异步回调。 |
| [getImage](arkts-na-wallpaper-getimage-f-sys.md#getimage-1) | 获取壁纸图片的像素图，且只能获取使用setImage设置的静态壁纸。使用promise异步回调。 |
| [getMinHeightSync](arkts-na-wallpaper-getminheightsync-f-sys.md#getminheightsync) | 获取壁纸的最小高度值。 |
| [getMinWidthSync](arkts-na-wallpaper-getminwidthsync-f-sys.md#getminwidthsync) | 获取壁纸的最小宽度值。 |
| [getPixelMap](arkts-na-wallpaper-getpixelmap-f-sys.md#getpixelmap) | 获取壁纸图片的像素图。 |
| [getPixelMap](arkts-na-wallpaper-getpixelmap-f-sys.md#getpixelmap-1) | 获取壁纸图片的像素图。 |
| [getWallpaperByState](arkts-na-wallpaper-getwallpaperbystate-f-sys.md#getwallpaperbystate) | 获取指定壁纸类型、折展态、横竖屏的壁纸图片的像素图，如果指定的壁纸不存在，会逐步降级匹配，unfolded-land -> unfolded-port ->normal-port。使用promise异步回调。 |
| [off](arkts-na-wallpaper-off-f-sys.md#off-1) | 取消订阅壁纸变化通知事件。不支持多线程并发调用。 |
| [on](arkts-na-wallpaper-on-f-sys.md#on-1) | 订阅壁纸变化通知事件。不支持多线程并发调用。 |
| [restore](arkts-na-wallpaper-restore-f-sys.md#restore) | 移除指定类型的壁纸，恢复为默认显示的壁纸。使用callback异步回调。 |
| [restore](arkts-na-wallpaper-restore-f-sys.md#restore-1) | 移除指定类型的壁纸，恢复为默认显示的壁纸。使用promise异步回调。 |
| [setAllWallpapers](arkts-na-wallpaper-setallwallpapers-f-sys.md#setallwallpapers) | 设置设备所有形态的壁纸。使用promise异步回调。（包括折展状态、横竖屏状态、资源路径，其中NORMAL-PORT为必选） |
| [setCustomWallpaper](arkts-na-wallpaper-setcustomwallpaper-f-sys.md#setcustomwallpaper) | 将指定的zip资源包设置为桌面或锁屏的壁纸资源，仅当com.ohos.sceneboard存在时，支持使用该接口。且具有ohos.permission.GET_WALLPAPER权限的应用可以访问/data/wallpaper/目录获取设置的资源。使用callback异步回调。 |
| [setCustomWallpaper](arkts-na-wallpaper-setcustomwallpaper-f-sys.md#setcustomwallpaper-1) | 将指定的zip资源包设置为桌面或锁屏的壁纸资源，仅当com.ohos.sceneboard存在时，支持使用该接口。且具有ohos.permission.GET_WALLPAPER权限的应用可以访问/data/wallpaper/目录获取设置的资源。使用Promise异步回调。 |
| [setImage](arkts-na-wallpaper-setimage-f-sys.md#setimage) | 将指定资源设置为指定类型的壁纸。使用callback异步回调。 |
| [setImage](arkts-na-wallpaper-setimage-f-sys.md#setimage-1) | 将指定资源设置为指定类型的壁纸。使用promise异步回调。 |
| [setVideo](arkts-na-wallpaper-setvideo-f-sys.md#setvideo) | 将视频资源设置为桌面或锁屏的动态壁纸。使用callback异步回调。 |
| [setVideo](arkts-na-wallpaper-setvideo-f-sys.md#setvideo-1) | 将视频资源设置为桌面或锁屏的动态壁纸。使用promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [RgbaColor](arkts-na-wallpaper-rgbacolor-i.md) | 定义壁纸颜色信息结构。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [WallpaperInfo](arkts-na-wallpaper-wallpaperinfo-i-sys.md) | 定义壁纸的信息结构。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 定义壁纸的枚举类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FoldState](arkts-na-wallpaper-foldstate-e-sys.md) | 定义设备的折展状态枚举类型。 |
| [RotateState](arkts-na-wallpaper-rotatestate-e-sys.md) | 定义设备的横竖屏状态枚举类型。 |
| [WallpaperResourceType](arkts-na-wallpaper-wallpaperresourcetype-e-sys.md) | 定义壁纸资源的枚举类型。 |
<!--DelEnd-->

