# @ohos.display

屏幕属性提供管理显示设备的一些基础能力，包括获取默认显示设备的信息，获取所有显示设备的信息以及监听显示设备的插拔行为。

**起始版本：** 7

<!--Device-unnamed-declare namespace display--><!--Device-unnamed-declare namespace display-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [convertGlobalToRelativeCoordinate](arkts-arkui-display-convertglobaltorelativecoordinate-f.md#convertglobaltorelativecoordinate-1) | 将主屏左上角为原点的全局坐标转换成displayId指定屏幕左上角为原点的相对坐标。若未传入displayId，默认转换为全局坐标所在屏幕的相对坐标系。若全局坐标不在任何屏幕上，默认转换成主屏的相对坐标。 |
| [convertRelativeToGlobalCoordinate](arkts-arkui-display-convertrelativetoglobalcoordinate-f.md#convertrelativetoglobalcoordinate-1) | 将指定屏幕左上角为原点的相对坐标转换成主屏左上角为原点的全局坐标，仅支持主屏和扩展屏的坐标转换。 |
| [createVirtualScreen](arkts-arkui-display-createvirtualscreen-f.md#createvirtualscreen-1) | 创建虚拟屏幕，使用Promise异步回调。 |
| [destroyVirtualScreen](arkts-arkui-display-destroyvirtualscreen-f.md#destroyvirtualscreen-1) | 销毁虚拟屏幕，使用Promise异步回调。 |
| [getAllDisplay](arkts-arkui-display-getalldisplay-f.md#getalldisplay-1) | 获取当前所有的Display对象，使用callback异步回调。 |
| [getAllDisplay](arkts-arkui-display-getalldisplay-f.md#getalldisplay-2) | 获取当前所有的Display对象，使用Promise异步回调。 |
| [getAllDisplayPhysicalResolution](arkts-arkui-display-getalldisplayphysicalresolution-f.md#getalldisplayphysicalresolution-1) | 获取当前设备支持的所有显示模式及其对应的物理屏幕分辨率信息对象。使用Promise异步回调。 |
| [getAllDisplays](arkts-arkui-display-getalldisplays-f.md#getalldisplays-1) | 获取当前所有的Display对象，使用callback异步回调。 |
| [getAllDisplays](arkts-arkui-display-getalldisplays-f.md#getalldisplays-2) | 获取当前所有的Display对象，使用Promise异步回调。 |
| [getBrightnessInfo](arkts-arkui-display-getbrightnessinfo-f.md#getbrightnessinfo-1) | 获取指定displayId对应屏幕的亮度信息。如果屏幕不支持HDR，返回的[BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md)对象中的currentHeadroom和maxHeadroom为默认值。虚拟屏的BrightnessInfo对象中sdrNits为默认值。 |
| [getCurrentFoldCreaseRegion](arkts-arkui-display-getcurrentfoldcreaseregion-f.md#getcurrentfoldcreaseregion-1) | 在当前显示模式下获取折叠折痕区域。 |
| [getDefaultDisplay](arkts-arkui-display-getdefaultdisplay-f.md#getdefaultdisplay-1) | 获取当前默认的Display对象，使用callback异步回调。 |
| [getDefaultDisplay](arkts-arkui-display-getdefaultdisplay-f.md#getdefaultdisplay-2) | 获取当前默认的Display对象，使用Promise异步回调。 |
| [getDefaultDisplaySync](arkts-arkui-display-getdefaultdisplaysync-f.md#getdefaultdisplaysync-1) | 返回应用所在屏幕的Display对象。若应用内多个Ability在不同屏幕，返回主屏的Display对象，若应用内多个Ability在同一屏幕，返回所在屏幕的Display对象。 |
| [getDisplayByIdSync](arkts-arkui-display-getdisplaybyidsync-f.md#getdisplaybyidsync-1) | 根据displayId获取对应的Display对象。 |
| [getFoldDisplayMode](arkts-arkui-display-getfolddisplaymode-f.md#getfolddisplaymode-1) | 获取可折叠设备当前的显示模式。 |
| [getFoldStatus](arkts-arkui-display-getfoldstatus-f.md#getfoldstatus-1) | 获取可折叠设备当前的折叠状态。 |
| [getPrimaryDisplaySync](arkts-arkui-display-getprimarydisplaysync-f.md#getprimarydisplaysync-1) | 获取主屏信息。除2in1之外的设备获取的是设备自带屏幕的Display对象；2in1设备外接屏幕时获取的是当前主屏幕的Display对象；2in1设备没有外接屏幕时获取的是自带屏幕的Display对象。 |
| [isCaptured](arkts-arkui-display-iscaptured-f.md#iscaptured-1) | 检查设备的屏幕显示信息是否被获取。 |
| [isCaptured](arkts-arkui-display-iscaptured-f.md#iscaptured-2) | 检查该设备是否被bundle名称列表中的任何应用抓拍、投影或录制。 |
| [isFoldable](arkts-arkui-display-isfoldable-f.md#isfoldable-1) | 判断设备是否可折叠。 |
| [makeUnique](arkts-arkui-display-makeunique-f.md#makeunique-1) | 将屏幕设置为异源模式，使用Promise异步回调。 |
| [off](arkts-arkui-display-off-f.md#off-1) | 关闭显示设备变化的监听。 |
| [off](arkts-arkui-display-off-f.md#off-2) | 关闭显示设备变化的监听。 |
| [off](arkts-arkui-display-off-f.md#off-3) | 关闭显示设备变化的监听。 |
| [off](arkts-arkui-display-off-f.md#off-5) | 关闭折叠设备折叠状态变化的监听。 |
| [off](arkts-arkui-display-off-f.md#off-6) | 关闭折叠设备折叠角度变化的监听。 |
| [off](arkts-arkui-display-off-f.md#off-7) | 关闭设备的屏幕显示信息是否被获取的监听。 |
| [off](arkts-arkui-display-off-f.md#off-8) | 关闭折叠设备屏幕显示模式变化的监听。 |
| [off](arkts-arkui-display-off-f.md#off-9) | 关闭所有屏幕亮度信息状态变化的监听。 |
| [on](arkts-arkui-display-on-f.md#on-1) | 开启显示设备变化的监听。 |
| [on](arkts-arkui-display-on-f.md#on-2) | 开启显示设备变化的监听。 |
| [on](arkts-arkui-display-on-f.md#on-3) | 开启显示设备变化的监听。 |
| [on](arkts-arkui-display-on-f.md#on-5) | 开启折叠设备折叠状态变化的监听。本接口监听设备物理折叠状态的变化，如果要监听屏幕显示模式的变化，需要使用[display.on('foldDisplayModeChange')](arkts-arkui-display-on-f.md#on-8)接口。两者存在差异，时序上物理折叠状态变化在前，底层会根据物理折叠状态匹配屏幕显示模式状态。若需监听当前显示内容是显示在折叠设备的内屏还是外屏，请使用[display.on('foldDisplayModeChange')](arkts-arkui-display-on-f.md#on-8)。 |
| [on](arkts-arkui-display-on-f.md#on-6) | 开启折叠设备折叠角度变化的监听。如果是双折轴设备，则有两个角度值；在充电口朝下的状态下，从右到左分别是折轴一和折轴二。 |
| [on](arkts-arkui-display-on-f.md#on-7) | 开启设备的屏幕显示信息是否被获取的监听。 |
| [on](arkts-arkui-display-on-f.md#on-8) | 开启折叠设备屏幕显示模式变化的监听。本接口监听设备屏幕显示模式的变化，如果要监听设备物理折叠状态的变化，需要使用[display.on('foldStatusChange')](arkts-arkui-display-on-f.md#on-5)接口。两者存在差异，时序上物理折叠状态变化在前，底层会根据物理折叠状态匹配屏幕显示模式状态。 |
| [on](arkts-arkui-display-on-f.md#on-9) | 开启所有屏幕亮度信息变化的监听。如果屏幕不支持HDR，监听到的[BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md)对象中的currentHeadroom和maxHeadroom为默认值。虚拟屏的BrightnessInfo对象中sdrNits为默认值。 |
| [onChangeWithAttribute](arkts-arkui-display-onchangewithattribute-f.md#onchangewithattribute-1) | 开启显示设备指定属性变化的监听。 |
| [setVirtualScreenSurface](arkts-arkui-display-setvirtualscreensurface-f.md#setvirtualscreensurface-1) | 设置虚拟屏幕的surfaceId。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addVirtualScreenBlocklist](arkts-arkui-display-addvirtualscreenblocklist-f-sys.md#addvirtualscreenblocklist-1) | 将窗口添加到禁止投屏显示的名单中，被添加的窗口无法在投屏时显示。仅对应用主窗或系统窗口生效。使用Promise异步回调。 |
| [addVirtualScreenSurface](arkts-arkui-display-addvirtualscreensurface-f-sys.md#addvirtualscreensurface-1) | 为虚拟屏幕添加surface。 |
| [hasPrivateWindow](arkts-arkui-display-hasprivatewindow-f-sys.md#hasprivatewindow-1) | 查询指定display对象上是否有可见的隐私窗口。可通过[setWindowPrivacyMode()](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9)接口设置隐私窗口。隐私窗口内容将无法被截屏或录屏。 |
| [off](arkts-arkui-display-off-f-sys.md#off-4) | 关闭屏幕隐私模式变化的监听。当屏幕前台有隐私窗口，则屏幕处于隐私模式，屏幕中的隐私窗口内容无法被截屏或录屏。 |
| [on](arkts-arkui-display-on-f-sys.md#on-4) | 开启屏幕隐私模式变化的监听。当屏幕前台有隐私窗口，则屏幕处于隐私模式，屏幕中的隐私窗口内容无法被截屏或录屏。 |
| [removeVirtualScreenBlocklist](arkts-arkui-display-removevirtualscreenblocklist-f-sys.md#removevirtualscreenblocklist-1) | 将窗口从禁止投屏显示的名单中移除，被移除的窗口可以在投屏时显示。仅对应用主窗或系统窗口生效。使用Promise异步回调。 |
| [removeVirtualScreenSurface](arkts-arkui-display-removevirtualscreensurface-f-sys.md#removevirtualscreensurface-1) | 删除虚拟屏的surface。 |
| [setFoldDisplayMode](arkts-arkui-display-setfolddisplaymode-f-sys.md#setfolddisplaymode-1) | 更改可折叠设备的显示模式。 |
| [setFoldDisplayMode](arkts-arkui-display-setfolddisplaymode-f-sys.md#setfolddisplaymode-2) | 更改可折叠设备的显示模式，并指明更改原因。 |
| [setFoldStatusLocked](arkts-arkui-display-setfoldstatuslocked-f-sys.md#setfoldstatuslocked-1) | 设置可折叠设备当前折叠状态的锁定状态。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md) | 屏幕亮度信息。此类型中的信息均来自底层屏幕信息数据。 |
| [CutoutInfo](arkts-arkui-display-cutoutinfo-i.md) | 挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。 |
| [Display](arkts-arkui-display-display-i.md) | 屏幕实例。描述Display对象的属性和方法。下列API示例中都需先使用[getAllDisplays()](arkts-arkui-display-getalldisplays-f.md#getalldisplays-1)、[getDefaultDisplaySync()](arkts-arkui-display-getdefaultdisplaysync-f.md#getdefaultdisplaysync-1)中的任一方法获取到Display实例，再通过此实例调用对应方法。 |
| [DisplayPhysicalResolution](arkts-arkui-display-displayphysicalresolution-i.md) | 设备的显示模式以及对应的物理屏幕分辨率信息。 |
| [FoldCreaseRegion](arkts-arkui-display-foldcreaseregion-i.md) | 折叠折痕区域。 |
| [Position](arkts-arkui-display-position-i.md) | 坐标位置：在全局坐标系中，以主屏左上角为原点。在相对坐标系中，以指定屏幕左上角为原点。 |
| [Rect](arkts-arkui-display-rect-i.md) | 矩形区域。 |
| [RelativePosition](arkts-arkui-display-relativeposition-i.md) | 相对坐标系下的坐标位置，以displayId对应的屏幕左上角为原点。 |
| [RoundedCorner](arkts-arkui-display-roundedcorner-i.md) | 屏幕圆角定义。 |
| [VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md) | 创建虚拟屏幕的参数。 |
| [WaterfallDisplayAreaRects](arkts-arkui-display-waterfalldisplayarearects-i.md) | 瀑布屏曲面部分显示区域。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Display](arkts-arkui-display-display-i-sys.md) | 屏幕实例。描述Display对象的属性和方法。下列API示例中都需先使用[getAllDisplays()](arkts-arkui-display-getalldisplays-f.md#getalldisplays-1)、[getDefaultDisplaySync()](arkts-arkui-display-getdefaultdisplaysync-f.md#getdefaultdisplaysync-1)中的任一方法获取到Display实例，再通过此实例调用对应方法。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CornerType](arkts-arkui-display-cornertype-e.md) | 屏幕圆角类型枚举。 |
| [DisplaySourceMode](arkts-arkui-display-displaysourcemode-e.md) | 屏幕显示内容的显示模式枚举。 |
| [DisplayState](arkts-arkui-display-displaystate-e.md) | 显示设备的状态枚举。 |
| [FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md) | 可折叠设备的显示模式枚举。 |
| [FoldStatus](arkts-arkui-display-foldstatus-e.md) | 当前可折叠设备的折叠状态枚举。如果是双折轴设备，则在充电口朝下的状态下，从右到左分别是折轴一和折轴二。 |
| [Orientation](arkts-arkui-display-orientation-e.md) | 显示设备当前显示的方向枚举。 |
| [ScreenShape](arkts-arkui-display-screenshape-e.md) | 显示设备的屏幕形状枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BrightnessCallback](arkts-arkui-display-brightnesscallback-t.md) | 监听屏幕亮度信息时使用的回调函数类型。 |

