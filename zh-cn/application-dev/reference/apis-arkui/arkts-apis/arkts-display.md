# @ohos.display

屏幕属性提供管理显示设备的一些基础能力，包括获取默认显示设备的信息，获取所有显示设备的信息以及监听显示设备的插拔行为。

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[addVirtualScreenBlocklist](arkts-arkui-display-addvirtualscreenblocklist-f-sys.md#addVirtualScreenBlocklist-1) | 将窗口添加到禁止投屏显示的名单中，被添加的窗口无法在投屏时显示。仅对应用主窗或系统窗口生效。使用Promise异步回调。<br/> |
| <!--DelRow-->[addVirtualScreenSurface](arkts-arkui-display-addvirtualscreensurface-f-sys.md#addVirtualScreenSurface-1) | 为虚拟屏幕添加surface。<br/> |
| [convertGlobalToRelativeCoordinate](arkts-arkui-display-convertglobaltorelativecoordinate-f.md#convertGlobalToRelativeCoordinate-1) | 将主屏左上角为原点的全局坐标转换成displayId指定屏幕左上角为原点的相对坐标。若未传入displayId，默认转换为全局坐标所在屏幕的相对坐标系。若全局坐标不在任何屏幕上，默认转换成主屏的相对坐标。<br/> |
| [convertRelativeToGlobalCoordinate](arkts-arkui-display-convertrelativetoglobalcoordinate-f.md#convertRelativeToGlobalCoordinate-1) | 将指定屏幕左上角为原点的相对坐标转换成主屏左上角为原点的全局坐标，仅支持主屏和扩展屏的坐标转换。<br/> |
| [createVirtualScreen](arkts-arkui-display-createvirtualscreen-f.md#createVirtualScreen-1) | 创建虚拟屏幕，使用Promise异步回调。<br/> |
| [destroyVirtualScreen](arkts-arkui-display-destroyvirtualscreen-f.md#destroyVirtualScreen-1) | 销毁虚拟屏幕，使用Promise异步回调。<br/> |
| [getAllDisplay](arkts-arkui-display-getalldisplay-f.md#getAllDisplay-1) | 获取当前所有的Display对象，使用callback异步回调。<br/> |
| [getAllDisplay](arkts-arkui-display-getalldisplay-f.md#getAllDisplay-2) | 获取当前所有的Display对象，使用Promise异步回调。<br/> |
| [getAllDisplayPhysicalResolution](arkts-arkui-display-getalldisplayphysicalresolution-f.md#getAllDisplayPhysicalResolution-1) | 获取当前设备支持的所有显示模式及其对应的物理屏幕分辨率信息对象。使用Promise异步回调。<br/> |
| [getAllDisplays](arkts-arkui-display-getalldisplays-f.md#getAllDisplays-1) | 获取当前所有的Display对象，使用callback异步回调。<br/> |
| [getAllDisplays](arkts-arkui-display-getalldisplays-f.md#getAllDisplays-2) | 获取当前所有的Display对象，使用Promise异步回调。<br/> |
| [getBrightnessInfo](arkts-arkui-display-getbrightnessinfo-f.md#getBrightnessInfo-1) | 获取指定displayId对应屏幕的亮度信息。如果屏幕不支持HDR，返回的[BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md#BrightnessInfo)对象中的currentHeadroom和maxHeadroom<br/>为默认值。虚拟屏的BrightnessInfo对象中sdrNits为默认值。<br/> |
| [getCurrentFoldCreaseRegion](arkts-arkui-display-getcurrentfoldcreaseregion-f.md#getCurrentFoldCreaseRegion-1) | 在当前显示模式下获取折叠折痕区域。<br/> |
| [getDefaultDisplay](arkts-arkui-display-getdefaultdisplay-f.md#getDefaultDisplay-1) | 获取当前默认的Display对象，使用callback异步回调。<br/> |
| [getDefaultDisplay](arkts-arkui-display-getdefaultdisplay-f.md#getDefaultDisplay-2) | 获取当前默认的Display对象，使用Promise异步回调。<br/> |
| [getDefaultDisplaySync](arkts-arkui-display-getdefaultdisplaysync-f.md#getDefaultDisplaySync-1) | 返回应用所在屏幕的Display对象。若应用内多个Ability在不同屏幕，返回主屏的Display对象，若应用内多个Ability在同一屏幕，返回所在屏幕的Display对象。<br/> |
| [getDisplayByIdSync](arkts-arkui-display-getdisplaybyidsync-f.md#getDisplayByIdSync-1) | 根据displayId获取对应的Display对象。<br/> |
| [getFoldDisplayMode](arkts-arkui-display-getfolddisplaymode-f.md#getFoldDisplayMode-1) | 获取可折叠设备当前的显示模式。<br/> |
| [getFoldStatus](arkts-arkui-display-getfoldstatus-f.md#getFoldStatus-1) | 获取可折叠设备当前的折叠状态。<br/> |
| [getPrimaryDisplaySync](arkts-arkui-display-getprimarydisplaysync-f.md#getPrimaryDisplaySync-1) | 获取主屏信息。除2in1之外的设备获取的是设备自带屏幕的Display对象；2in1设备外接屏幕时获取的是当前主屏幕的Display对象；2in1设备没有外接屏幕时获取的是自带屏幕的Display对象。<br/> |
| <!--DelRow-->[hasPrivateWindow](arkts-arkui-display-hasprivatewindow-f-sys.md#hasPrivateWindow-1) | 查询指定display对象上是否有可见的隐私窗口。可通过<br/>[setWindowPrivacyMode()](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9)接口设置隐私窗口。<br/>隐私窗口内容将无法被截屏或录屏。<br/> |
| [isCaptured](arkts-arkui-display-iscaptured-f.md#isCaptured-1) | 检查设备的屏幕显示信息是否被获取。<br/> |
| [isCaptured](arkts-arkui-display-iscaptured-f.md#isCaptured-2) | 检查该设备是否被bundle名称列表中的任何应用抓拍、投影或录制。<br/> |
| [isFoldable](arkts-arkui-display-isfoldable-f.md#isFoldable-1) | 判断设备是否可折叠。<br/> |
| [makeUnique](arkts-arkui-display-makeunique-f.md#makeUnique-1) | 将屏幕设置为异源模式，使用Promise异步回调。<br/> |
| [off](arkts-arkui-display-off-f.md#off-1) | 关闭显示设备变化的监听。<br/> |
| [off](arkts-arkui-display-off-f.md#off-2) | 关闭显示设备变化的监听。<br/> |
| [off](arkts-arkui-display-off-f.md#off-3) | 关闭显示设备变化的监听。<br/> |
| <!--DelRow-->[off](arkts-arkui-display-off-f-sys.md#off-4) | 关闭屏幕隐私模式变化的监听。当屏幕前台有隐私窗口，则屏幕处于隐私模式，屏幕中的隐私窗口内容无法被截屏或录屏。<br/> |
| [off](arkts-arkui-display-off-f.md#off-5) | 关闭折叠设备折叠状态变化的监听。<br/> |
| [off](arkts-arkui-display-off-f.md#off-6) | 关闭折叠设备折叠角度变化的监听。<br/> |
| [off](arkts-arkui-display-off-f.md#off-7) | 关闭设备的屏幕显示信息是否被获取的监听。<br/> |
| [off](arkts-arkui-display-off-f.md#off-8) | 关闭折叠设备屏幕显示模式变化的监听。<br/> |
| [off](arkts-arkui-display-off-f.md#off-9) | 关闭所有屏幕亮度信息状态变化的监听。<br/> |
| [on](arkts-arkui-display-on-f.md#on-1) | 开启显示设备变化的监听。<br/> |
| [on](arkts-arkui-display-on-f.md#on-2) | 开启显示设备变化的监听。<br/> |
| [on](arkts-arkui-display-on-f.md#on-3) | 开启显示设备变化的监听。<br/> |
| <!--DelRow-->[on](arkts-arkui-display-on-f-sys.md#on-4) | 开启屏幕隐私模式变化的监听。当屏幕前台有隐私窗口，则屏幕处于隐私模式，屏幕中的隐私窗口内容无法被截屏或录屏。<br/> |
| [on](arkts-arkui-display-on-f.md#on-5) | 开启折叠设备折叠状态变化的监听。<br/><br/>本接口监听设备物理折叠状态的变化，如果要监听屏幕显示模式的变化，需要使用<br/>[display.on('foldDisplayModeChange')](display.on(type: 'foldDisplayModeChange', callback: Callback&lt;FoldDisplayMode&gt;))<br/>接口。<br/><br/>两者存在差异，时序上物理折叠状态变化在前，底层会根据物理折叠状态匹配屏幕显示模式状态。<br/><br/>若需监听当前显示内容是显示在折叠设备的内屏还是外屏，请使用<br/>[display.on('foldDisplayModeChange')](display.on(type: 'foldDisplayModeChange', callback: Callback&lt;FoldDisplayMode&gt;))<br/>。<br/> |
| [on](arkts-arkui-display-on-f.md#on-6) | 开启折叠设备折叠角度变化的监听。如果是双折轴设备，则有两个角度值；在充电口朝下的状态下，从右到左分别是折轴一和折轴二。<br/> |
| [on](arkts-arkui-display-on-f.md#on-7) | 开启设备的屏幕显示信息是否被获取的监听。<br/> |
| [on](arkts-arkui-display-on-f.md#on-8) | 开启折叠设备屏幕显示模式变化的监听。<br/><br/>本接口监听设备屏幕显示模式的变化，如果要监听设备物理折叠状态的变化，需要使用<br/>[display.on('foldStatusChange')](display.on(type: 'foldStatusChange', callback: Callback&lt;FoldStatus&gt;))接口。<br/><br/>两者存在差异，时序上物理折叠状态变化在前，底层会根据物理折叠状态匹配屏幕显示模式状态。<br/> |
| [on](arkts-arkui-display-on-f.md#on-9) | 开启所有屏幕亮度信息变化的监听。如果屏幕不支持HDR，监听到的[BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md#BrightnessInfo)对象中的currentHeadroom和maxHeadroom为默认值。虚拟<br/>屏的BrightnessInfo对象中sdrNits为默认值。<br/> |
| [onChangeWithAttribute](arkts-arkui-display-onchangewithattribute-f.md#onChangeWithAttribute-1) | 开启显示设备指定属性变化的监听。<br/> |
| <!--DelRow-->[removeVirtualScreenBlocklist](arkts-arkui-display-removevirtualscreenblocklist-f-sys.md#removeVirtualScreenBlocklist-1) | 将窗口从禁止投屏显示的名单中移除，被移除的窗口可以在投屏时显示。仅对应用主窗或系统窗口生效。使用Promise异步回调。<br/> |
| <!--DelRow-->[removeVirtualScreenSurface](arkts-arkui-display-removevirtualscreensurface-f-sys.md#removeVirtualScreenSurface-1) | 删除虚拟屏的surface<br/> |
| <!--DelRow-->[setFoldDisplayMode](arkts-arkui-display-setfolddisplaymode-f-sys.md#setFoldDisplayMode-1) | 更改可折叠设备的显示模式。<br/> |
| <!--DelRow-->[setFoldDisplayMode](arkts-arkui-display-setfolddisplaymode-f-sys.md#setFoldDisplayMode-2) | 更改可折叠设备的显示模式，并指明更改原因。<br/> |
| <!--DelRow-->[setFoldStatusLocked](arkts-arkui-display-setfoldstatuslocked-f-sys.md#setFoldStatusLocked-1) | 设置可折叠设备当前折叠状态的锁定状态。<br/> |
| [setVirtualScreenSurface](arkts-arkui-display-setvirtualscreensurface-f.md#setVirtualScreenSurface-1) | 设置虚拟屏幕的surfaceId，surfaceId用于标识一个surface，表示当前虚拟屏用于显示对应surface中的内容。使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md) | 屏幕亮度信息。此类型中的信息均来自底层屏幕信息数据。<br/> |
| [CutoutInfo](arkts-arkui-display-cutoutinfo-i.md) | 挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。<br/> |
| [Display](arkts-arkui-display-display-i.md) | 屏幕实例。描述Display对象的属性和方法。<br/><br/>下列API示例中都需先使用[getAllDisplays()](display.getAllDisplays(callback: AsyncCallback&lt;Array&lt;Display&gt;&gt;))、<br/>[getDefaultDisplaySync()](arkts-arkui-display-getdefaultdisplaysync-f.md#getDefaultDisplaySync-1)中的任一方法获取到Display实例，再通过此实例调用对应方法。<br/> |
| <!--DelRow-->[Display](arkts-arkui-display-display-i-sys.md) | 屏幕实例。描述Display对象的属性和方法。<br/><br/>下列API示例中都需先使用[getAllDisplays()](display.getAllDisplays(callback: AsyncCallback&lt;Array&lt;Display&gt;&gt;))、<br/>[getDefaultDisplaySync()](arkts-arkui-display-getdefaultdisplaysync-f.md#getDefaultDisplaySync-1)中的任一方法获取到Display实例，再通过此实例调用对应方法。<br/> |
| [DisplayPhysicalResolution](arkts-arkui-display-displayphysicalresolution-i.md) | 设备的显示模式以及对应的物理屏幕分辨率信息。<br/> |
| [FoldCreaseRegion](arkts-arkui-display-foldcreaseregion-i.md) | 折叠折痕区域。<br/> |
| [Position](arkts-arkui-display-position-i.md) | 坐标位置：在全局坐标系中，以主屏左上角为原点。在相对坐标系中，以指定屏幕左上角为原点。<br/> |
| [Rect](arkts-arkui-display-rect-i.md) | 矩形区域。<br/> |
| [RelativePosition](arkts-arkui-display-relativeposition-i.md) | 相对坐标系下的坐标位置，以displayId对应的屏幕左上角为原点。<br/> |
| [RoundedCorner](arkts-arkui-display-roundedcorner-i.md) | 屏幕圆角定义。<br/> |
| [VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md) | 创建虚拟屏幕的参数。<br/> |
| [WaterfallDisplayAreaRects](arkts-arkui-display-waterfalldisplayarearects-i.md) | 瀑布屏曲面部分显示区域。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CornerType](arkts-arkui-display-cornertype-e.md) | 屏幕圆角类型枚举。<br/> |
| [DisplaySourceMode](arkts-arkui-display-displaysourcemode-e.md) | 屏幕显示内容的显示模式枚举。<br/> |
| [DisplayState](arkts-arkui-display-displaystate-e.md) | 显示设备的状态枚举。<br/> |
| [FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md) | 可折叠设备的显示模式枚举。<br/><br/>&gt; **说明：**<br/><br/>&gt; 对于内外屏均可作为主屏幕使用的折叠产品，例如大折叠、阔折叠，内屏显示状态为FOLD_DISPLAY_MODE_FULL，外屏显示状态为FOLD_DISPLAY_MODE_MAIN。<br/><br/>&gt; 对于外屏只有简单的辅助显示作用的折叠产品，例如小折叠，内屏显示状态为FOLD_DISPLAY_MODE_MAIN，外屏显示状态为FOLD_DISPLAY_MODE_SUB。<br/> |
| [FoldStatus](arkts-arkui-display-foldstatus-e.md) | 当前可折叠设备的折叠状态枚举。如果是双折轴设备，则在充电口朝下的状态下，从右到左分别是折轴一和折轴二。<br/><br/>&gt; **说明：**<br/><br/>&gt; 只有一个折轴的产品包含FOLD_STATUS_EXPANDED、FOLD_STATUS_FOLDED、FOLD_STATUS_HALF_FOLDED三种折叠状态。<br/><br/>&gt; 具有两个折轴的产品包含上表除FOLD_STATUS_UNKNOWN以外的九种折叠状态。<br/><br/>&gt; FOLD_STATUS_UNKNOWN是一种不可用的折叠状态。<br/> |
| [Orientation](arkts-arkui-display-orientation-e.md) | 显示设备当前显示的方向枚举。<br/> |
| [ScreenShape](arkts-arkui-display-screenshape-e.md) | 显示设备的屏幕形状枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BrightnessCallback](arkts-arkui-display-brightnesscallback-t.md) | 监听屏幕亮度信息时使用的回调函数类型。<br/> |

