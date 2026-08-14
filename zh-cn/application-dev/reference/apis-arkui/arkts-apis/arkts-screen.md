# @ohos.screen

本模块提供管理屏幕的一些基础能力，包括获取屏幕对象，监听屏幕变化，创建和销毁虚拟屏幕等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace screen--><!--Device-unnamed-declare namespace screen-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createVirtualScreen](arkts-arkui-screen-createvirtualscreen-f-sys.md#createVirtualScreen) | 创建虚拟屏幕，使用callback异步回调。 |
| [createVirtualScreen](arkts-arkui-screen-createvirtualscreen-f-sys.md#createVirtualScreen（系统接口）) | 创建虚拟屏幕，使用Promise异步回调。 |
| [destroyVirtualScreen](arkts-arkui-screen-destroyvirtualscreen-f-sys.md#destroyVirtualScreen) | 销毁虚拟屏幕，使用callback异步回调。 |
| [destroyVirtualScreen](arkts-arkui-screen-destroyvirtualscreen-f-sys.md#destroyVirtualScreen（系统接口）) | 销毁虚拟屏幕，使用Promise异步回调。 |
| [getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md#getAllScreens) | 获取所有的屏幕，使用callback异步回调。 |
| [getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md#getAllScreens（系统接口）) | 获取所有的屏幕，使用Promise异步回调。 |
| [isScreenRotationLocked](arkts-arkui-screen-isscreenrotationlocked-f-sys.md#isScreenRotationLocked) | 查询当前自动转屏是否锁定，使用callback异步回调。 |
| [isScreenRotationLocked](arkts-arkui-screen-isscreenrotationlocked-f-sys.md#isScreenRotationLocked（系统接口）) | 查询当前自动转屏是否锁定，使用Promise异步回调。 |
| [makeExpand](arkts-arkui-screen-makeexpand-f-sys.md#makeExpand) | 将屏幕设置为扩展模式，使用callback异步回调。 |
| [makeExpand](arkts-arkui-screen-makeexpand-f-sys.md#makeExpand（系统接口）) | 将屏幕设置为扩展模式，使用Promise异步回调。 |
| [makeMirror](arkts-arkui-screen-makemirror-f-sys.md#makeMirror) | 将屏幕设置为镜像模式，使用callback异步回调。 |
| [makeMirror](arkts-arkui-screen-makemirror-f-sys.md#makeMirror（系统接口）) | 将屏幕设置为镜像模式，使用Promise异步回调。 |
| [makeMirrorWithRegion](arkts-arkui-screen-makemirrorwithregion-f-sys.md#makeMirrorWithRegion) | 将屏幕的某一矩形区域设置为镜像模式，使用Promise异步回调。调用该接口后，不建议再进行屏幕的旋转/折叠，否则可能导致镜像内容异常。 |
| [makeUnique](arkts-arkui-screen-makeunique-f-sys.md#makeUnique) | 将屏幕设置为异源模式，使用Promise异步回调。 |
| [offChange](arkts-arkui-screen-offchange-f-sys.md#offChange) | Unregister the callback for screen changes. |
| [offConnect](arkts-arkui-screen-offconnect-f-sys.md#offConnect) | Unregister the callback for screen connection events. |
| [offDisconnect](arkts-arkui-screen-offdisconnect-f-sys.md#offDisconnect) | Unregister the callback for screen disconnection events. |
| off_change | 关闭屏幕状态变化的监听。 |
| off_connect | 关闭屏幕状态变化的监听。 |
| off_disconnect | 关闭屏幕状态变化的监听。 |
| [onChange](arkts-arkui-screen-onchange-f-sys.md#onChange) | Register the callback for screen change. |
| [onConnect](arkts-arkui-screen-onconnect-f-sys.md#onConnect) | Register the callback for screen connection events. |
| [onDisconnect](arkts-arkui-screen-ondisconnect-f-sys.md#onDisconnect) | Register the callback for screen disconnection events. |
| on_change | 开启屏幕状态变化的监听。 |
| on_connect | 开启屏幕状态变化的监听。 |
| on_disconnect | 开启屏幕状态变化的监听。 |
| [resizeVirtualScreen](arkts-arkui-screen-resizevirtualscreen-f-sys.md#resizeVirtualScreen) | 修改指定虚拟屏的尺寸，使用Promise异步回调。 |
| [setMultiScreenMode](arkts-arkui-screen-setmultiscreenmode-f-sys.md#setMultiScreenMode) | 设置扩展屏幕的显示模式（镜像/扩展），使用Promise异步回调。primaryScreenId和secondaryScreenId均为0时，仅在扩展屏显示。 |
| [setMultiScreenRelativePosition](arkts-arkui-screen-setmultiscreenrelativeposition-f-sys.md#setMultiScreenRelativePosition) | 仅在扩展模式下，设置主屏和扩展屏幕的位置信息，使用Promise异步回调。 |
| [setScreenPrivacyMaskImage](arkts-arkui-screen-setscreenprivacymaskimage-f-sys.md#setScreenPrivacyMaskImage) | 设置屏幕的隐私蒙版图片，使用Promise异步回调。 |
| [setScreenRotationLocked](arkts-arkui-screen-setscreenrotationlocked-f-sys.md#setScreenRotationLocked) | 设置自动转屏开关是否锁定，使用callback异步回调。 |
| [setScreenRotationLocked](arkts-arkui-screen-setscreenrotationlocked-f-sys.md#setScreenRotationLocked（系统接口）) | 设置自动转屏开关是否锁定，使用Promise异步回调。 |
| [setVirtualScreenSurface](arkts-arkui-screen-setvirtualscreensurface-f-sys.md#setVirtualScreenSurface) | 设置虚拟屏幕的surface，使用callback异步回调。 |
| [setVirtualScreenSurface](arkts-arkui-screen-setvirtualscreensurface-f-sys.md#setVirtualScreenSurface（系统接口）) | 设置虚拟屏幕的surface，使用Promise异步回调。 |
| [stopExpand](arkts-arkui-screen-stopexpand-f-sys.md#stopExpand) | 停止屏幕的扩展模式，使用callback异步回调。 |
| [stopExpand](arkts-arkui-screen-stopexpand-f-sys.md#stopExpand（系统接口）) | 停止屏幕的扩展模式，使用Promise异步回调。 |
| [stopMirror](arkts-arkui-screen-stopmirror-f-sys.md#stopMirror) | 停止屏幕的镜像模式，使用callback异步回调。 |
| [stopMirror](arkts-arkui-screen-stopmirror-f-sys.md#stopMirror（系统接口）) | 停止屏幕的镜像模式，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExpandOption](arkts-arkui-screen-expandoption-i-sys.md) | 扩展屏幕的参数。 |
| [MultiScreenPositionOptions](arkts-arkui-screen-multiscreenpositionoptions-i-sys.md) | 屏幕位置信息。 |
| [OrientationOptions](arkts-arkui-screen-orientationoptions-i-sys.md) | 设置旋转行为的参数 |
| [Rect](arkts-arkui-screen-rect-i-sys.md) | 矩形信息。 |
| [Screen](arkts-arkui-screen-screen-i-sys.md) | [物理屏](../../../displaymanager/display-terminology.md#物理屏)屏幕实例。 下列API示例中都需先使用[getAllScreens()](arkts-arkui-screen-getallscreens-f-sys.md#getAllScreens（系统接口）)、 [createVirtualScreen()](arkts-arkui-screen-createvirtualscreen-f-sys.md#createVirtualScreen（系统接口）) 中的任一方法获取到Screen实例，再通过此实例调用对应方法。 |
| [ScreenModeInfo](arkts-arkui-screen-screenmodeinfo-i-sys.md) | 屏幕显示模式信息。 |
| [VirtualScreenOption](arkts-arkui-screen-virtualscreenoption-i-sys.md) | 创建虚拟屏幕的参数。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MultiScreenMode](arkts-arkui-screen-multiscreenmode-e-sys.md) | 屏幕模式枚举。 |
| [Orientation](arkts-arkui-screen-orientation-e-sys.md) | 屏幕方向枚举。 |
| [ScreenSourceMode](arkts-arkui-screen-screensourcemode-e-sys.md) | 屏幕显示内容来源模式枚举。 |
| [ScreenType](arkts-arkui-screen-screentype-e-sys.md) | 屏幕类型枚举。 |
<!--DelEnd-->

