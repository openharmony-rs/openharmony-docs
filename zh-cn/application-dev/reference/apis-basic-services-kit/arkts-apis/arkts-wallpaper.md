# @ohos.wallpaper(壁纸)

壁纸管理服务为OpenHarmony系统服务，提供壁纸切换功能。从API 9开始壁纸管理的接口调整为系统API，壁纸的切换只能通过系统应用来完成。壁纸管理提供壁纸切换通道，使用壁纸的应用（如：桌面）需订阅壁纸变化通知并刷新壁纸显示。

> **说明：**
> 
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.wallpaper (壁纸)](#ohoswallpaper壁纸)。

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Wallpaper

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getColors(壁纸)](arkts-basicservices-wallpaper-getcolors-f.md) | 获取指定类型壁纸的主要颜色信息。 |
| [getColors(壁纸)](arkts-basicservices-wallpaper-getcolors-f.md) | 获取指定类型壁纸的主要颜色信息。 |
| [getFile(壁纸)](arkts-basicservices-wallpaper-getfile-f.md) | 获取指定类型的壁纸文件。 |
| [getFile(壁纸)](arkts-basicservices-wallpaper-getfile-f.md) | 获取指定类型的壁纸文件。 |
| [getId(壁纸)](arkts-basicservices-wallpaper-getid-f.md) | 获取指定类型壁纸的ID。 |
| [getId(壁纸)](arkts-basicservices-wallpaper-getid-f.md) | 获取指定类型壁纸的ID。 |
| [getMinHeight(壁纸)](arkts-basicservices-wallpaper-getminheight-f.md) | 获取壁纸的最小高度值。 |
| [getMinHeight(壁纸)](arkts-basicservices-wallpaper-getminheight-f.md) | 获取壁纸的最小高度值。 |
| [getMinWidth(壁纸)](arkts-basicservices-wallpaper-getminwidth-f.md) | 获取壁纸的最小宽度值。 |
| [getMinWidth(壁纸)](arkts-basicservices-wallpaper-getminwidth-f.md) | 获取壁纸的最小宽度值。 |
| [isChangePermitted(壁纸)](arkts-basicservices-wallpaper-ischangepermitted-f.md) | 是否允许应用改变当前用户的壁纸。 |
| [isChangePermitted(壁纸)](arkts-basicservices-wallpaper-ischangepermitted-f.md) | 是否允许应用改变当前用户的壁纸。 |
| [isOperationAllowed(壁纸)](arkts-basicservices-wallpaper-isoperationallowed-f.md) | 是否允许用户设置壁纸。 |
| [isOperationAllowed(壁纸)](arkts-basicservices-wallpaper-isoperationallowed-f.md) | 是否允许用户设置壁纸。 |
| [off(壁纸)](arkts-basicservices-wallpaper-off-f.md#offcolorchange) | 取消订阅壁纸颜色变化结果上报事件。不支持多线程并发调用。 |
| [on(壁纸)](arkts-basicservices-wallpaper-on-f.md#oncolorchange) | 订阅壁纸颜色变化结果上报事件。不支持多线程并发调用。 |
| [reset(壁纸)](arkts-basicservices-wallpaper-reset-f.md) | 移除指定类型的壁纸，恢复为默认显示的壁纸。 |
| [reset(壁纸)](arkts-basicservices-wallpaper-reset-f.md) | 移除指定类型的壁纸，恢复为默认显示的壁纸。 |
| [setWallpaper(壁纸)](arkts-basicservices-wallpaper-setwallpaper-f.md) | 将指定资源设置为指定类型的壁纸。 |
| [setWallpaper(壁纸)](arkts-basicservices-wallpaper-setwallpaper-f.md) | 将指定资源设置为指定类型的壁纸。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getColorsSync(壁纸)](arkts-basicservices-wallpaper-getcolorssync-f-sys.md) | 获取指定类型壁纸的主要颜色信息。 |
| [getImage(壁纸)](arkts-basicservices-wallpaper-getimage-f-sys.md) | 获取壁纸图片的像素图，且只能获取使用setImage设置的静态壁纸。使用callback异步回调。 |
| [getImage(壁纸)](arkts-basicservices-wallpaper-getimage-f-sys.md) | 获取壁纸图片的像素图，且只能获取使用setImage设置的静态壁纸。使用promise异步回调。 |
| [getMinHeightSync(壁纸)](arkts-basicservices-wallpaper-getminheightsync-f-sys.md) | 获取壁纸的最小高度值。 |
| [getMinWidthSync(壁纸)](arkts-basicservices-wallpaper-getminwidthsync-f-sys.md) | 获取壁纸的最小宽度值。 |
| [getPixelMap(壁纸)](arkts-basicservices-wallpaper-getpixelmap-f-sys.md) | 获取壁纸图片的像素图。 |
| [getPixelMap(壁纸)](arkts-basicservices-wallpaper-getpixelmap-f-sys.md) | 获取壁纸图片的像素图。 |
| [getWallpaperByState(壁纸)](arkts-basicservices-wallpaper-getwallpaperbystate-f-sys.md) | 获取指定壁纸类型、折展态、横竖屏的壁纸图片的像素图，如果指定的壁纸不存在，会逐步降级匹配，unfolded-land - & gt; unfolded-port - & gt;normal-port。使用promise异步回调。 |
| off(壁纸) | 取消订阅壁纸变化通知事件。不支持多线程并发调用。 |
| on(壁纸) | 订阅壁纸变化通知事件。不支持多线程并发调用。 |
| [restore(壁纸)](arkts-basicservices-wallpaper-restore-f-sys.md) | 移除指定类型的壁纸，恢复为默认显示的壁纸。使用callback异步回调。 |
| [restore(壁纸)](arkts-basicservices-wallpaper-restore-f-sys.md) | 移除指定类型的壁纸，恢复为默认显示的壁纸。使用promise异步回调。 |
| [setAllWallpapers(壁纸)](arkts-basicservices-wallpaper-setallwallpapers-f-sys.md) | 设置设备所有形态的壁纸。使用promise异步回调。（包括折展状态、横竖屏状态、资源路径，其中NORMAL-PORT为必选） |
| [setCustomWallpaper(壁纸)](arkts-basicservices-wallpaper-setcustomwallpaper-f-sys.md) | 将指定的zip资源包设置为桌面或锁屏的壁纸资源，仅当com.ohos.sceneboard存在时，支持使用该接口。且具有ohos.permission.GET_WALLPAPER权限的应用可以访问/data/wallpaper/目 录获取设置的资源。使用callback异步回调。 |
| [setCustomWallpaper(壁纸)](arkts-basicservices-wallpaper-setcustomwallpaper-f-sys.md) | 将指定的zip资源包设置为桌面或锁屏的壁纸资源，仅当com.ohos.sceneboard存在时，支持使用该接口。且具有ohos.permission.GET_WALLPAPER权限的应用可以访问/data/wallpaper/目 录获取设置的资源。使用Promise异步回调。 |
| [setImage(壁纸)](arkts-basicservices-wallpaper-setimage-f-sys.md) | 将指定资源设置为指定类型的壁纸。使用callback异步回调。 |
| [setImage(壁纸)](arkts-basicservices-wallpaper-setimage-f-sys.md) | 将指定资源设置为指定类型的壁纸。使用promise异步回调。 |
| [setVideo(壁纸)](arkts-basicservices-wallpaper-setvideo-f-sys.md) | 将视频资源设置为桌面或锁屏的动态壁纸。使用callback异步回调。 |
| [setVideo(壁纸)](arkts-basicservices-wallpaper-setvideo-f-sys.md) | 将视频资源设置为桌面或锁屏的动态壁纸。使用promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [RgbaColor(壁纸)](arkts-basicservices-wallpaper-rgbacolor-i.md) | 定义壁纸颜色信息结构。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [WallpaperInfo(壁纸)](arkts-basicservices-wallpaper-wallpaperinfo-i-sys.md) | 定义壁纸的信息结构。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WallpaperType(壁纸)](arkts-basicservices-wallpaper-wallpapertype-e.md) | 定义壁纸的枚举类型。@enum { number } WallpaperType |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FoldState(壁纸)](arkts-basicservices-wallpaper-foldstate-e-sys.md) | 定义设备的折展状态枚举类型。 |
| [RotateState(壁纸)](arkts-basicservices-wallpaper-rotatestate-e-sys.md) | 定义设备的横竖屏状态枚举类型。 |
| [WallpaperResourceType(壁纸)](arkts-basicservices-wallpaper-wallpaperresourcetype-e-sys.md) | 定义壁纸资源的枚举类型。 |
<!--DelEnd-->
