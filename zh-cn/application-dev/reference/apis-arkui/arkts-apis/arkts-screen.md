# @ohos.screen

本模块提供管理屏幕的一些基础能力，包括获取屏幕对象，监听屏幕变化，创建和销毁虚拟屏幕等。

**起始版本：** 9

<!--Device-unnamed-declare namespace screen--><!--Device-unnamed-declare namespace screen-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createVirtualScreen](arkts-arkui-screen-createvirtualscreen-f-sys.md#createvirtualscreen-1) | 创建虚拟屏幕，使用callback异步回调。 |
| [createVirtualScreen](arkts-arkui-screen-createvirtualscreen-f-sys.md#createvirtualscreen-2) | 创建虚拟屏幕，使用Promise异步回调。 |
| [destroyVirtualScreen](arkts-arkui-screen-destroyvirtualscreen-f-sys.md#destroyvirtualscreen-1) | 销毁虚拟屏幕，使用callback异步回调。 |
| [destroyVirtualScreen](arkts-arkui-screen-destroyvirtualscreen-f-sys.md#destroyvirtualscreen-2) | 销毁虚拟屏幕，使用Promise异步回调。 |
| [getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md#getallscreens-1) | 获取所有的屏幕，使用callback异步回调。 |
| [getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md#getallscreens-2) | 获取所有的屏幕，使用Promise异步回调。 |
| [isScreenRotationLocked](arkts-arkui-screen-isscreenrotationlocked-f-sys.md#isscreenrotationlocked-1) | 查询当前自动转屏是否锁定，使用callback异步回调。 |
| [isScreenRotationLocked](arkts-arkui-screen-isscreenrotationlocked-f-sys.md#isscreenrotationlocked-2) | 查询当前自动转屏是否锁定，使用Promise异步回调。 |
| [makeExpand](arkts-arkui-screen-makeexpand-f-sys.md#makeexpand-1) | 将屏幕设置为扩展模式，使用callback异步回调。 |
| [makeExpand](arkts-arkui-screen-makeexpand-f-sys.md#makeexpand-2) | 将屏幕设置为扩展模式，使用Promise异步回调。 |
| [makeMirror](arkts-arkui-screen-makemirror-f-sys.md#makemirror-1) | 将屏幕设置为镜像模式，使用callback异步回调。 |
| [makeMirror](arkts-arkui-screen-makemirror-f-sys.md#makemirror-2) | 将屏幕设置为镜像模式，使用Promise异步回调。 |
| [makeMirrorWithRegion](arkts-arkui-screen-makemirrorwithregion-f-sys.md#makemirrorwithregion-1) | 将屏幕的某一矩形区域设置为镜像模式，使用Promise异步回调。调用该接口后，不建议再进行屏幕的旋转/折叠，否则可能导致镜像内容异常。 |
| [makeUnique](arkts-arkui-screen-makeunique-f-sys.md#makeunique-1) | 将屏幕设置为异源模式，使用Promise异步回调。 |
| [off](arkts-arkui-screen-off-f-sys.md#off-1) | 关闭屏幕状态变化的监听。 |
| [off](arkts-arkui-screen-off-f-sys.md#off-2) | 关闭屏幕状态变化的监听。 |
| [off](arkts-arkui-screen-off-f-sys.md#off-3) | 关闭屏幕状态变化的监听。 |
| [on](arkts-arkui-screen-on-f-sys.md#on-1) | 开启屏幕状态变化的监听。 |
| [on](arkts-arkui-screen-on-f-sys.md#on-2) | 开启屏幕状态变化的监听。 |
| [on](arkts-arkui-screen-on-f-sys.md#on-3) | 开启屏幕状态变化的监听。 |
| [resizeVirtualScreen](arkts-arkui-screen-resizevirtualscreen-f-sys.md#resizevirtualscreen-1) | 修改指定虚拟屏的尺寸，使用Promise异步回调。 |
| [setMultiScreenMode](arkts-arkui-screen-setmultiscreenmode-f-sys.md#setmultiscreenmode-1) | 设置扩展屏幕的显示模式（镜像/扩展），使用Promise异步回调。primaryScreenId和secondaryScreenId均为0时，仅在扩展屏显示。 |
| [setMultiScreenRelativePosition](arkts-arkui-screen-setmultiscreenrelativeposition-f-sys.md#setmultiscreenrelativeposition-1) | 仅在扩展模式下，设置主屏和扩展屏幕的位置信息，使用Promise异步回调。 |
| [setScreenPrivacyMaskImage](arkts-arkui-screen-setscreenprivacymaskimage-f-sys.md#setscreenprivacymaskimage-1) | 设置屏幕的隐私蒙版图片，使用Promise异步回调。 |
| [setScreenRotationLocked](arkts-arkui-screen-setscreenrotationlocked-f-sys.md#setscreenrotationlocked-1) | 设置自动转屏开关是否锁定，使用callback异步回调。 |
| [setScreenRotationLocked](arkts-arkui-screen-setscreenrotationlocked-f-sys.md#setscreenrotationlocked-2) | 设置自动转屏开关是否锁定，使用Promise异步回调。 |
| [setVirtualScreenSurface](arkts-arkui-screen-setvirtualscreensurface-f-sys.md#setvirtualscreensurface-1) | 设置虚拟屏幕的surface，使用callback异步回调。 |
| [setVirtualScreenSurface](arkts-arkui-screen-setvirtualscreensurface-f-sys.md#setvirtualscreensurface-2) | 设置虚拟屏幕的surface，使用Promise异步回调。 |
| [stopExpand](arkts-arkui-screen-stopexpand-f-sys.md#stopexpand-1) | 停止屏幕的扩展模式，使用callback异步回调。 |
| [stopExpand](arkts-arkui-screen-stopexpand-f-sys.md#stopexpand-2) | 停止屏幕的扩展模式，使用Promise异步回调。 |
| [stopMirror](arkts-arkui-screen-stopmirror-f-sys.md#stopmirror-1) | 停止屏幕的镜像模式，使用callback异步回调。 |
| [stopMirror](arkts-arkui-screen-stopmirror-f-sys.md#stopmirror-2) | 停止屏幕的镜像模式，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExpandOption](arkts-arkui-screen-expandoption-i-sys.md) | 扩展屏幕的参数。 |
| [MultiScreenPositionOptions](arkts-arkui-screen-multiscreenpositionoptions-i-sys.md) | 屏幕位置信息。 |
| [OrientationOptions](arkts-arkui-screen-orientationoptions-i-sys.md) | 设置旋转行为的参数 |
| [Rect](arkts-arkui-screen-rect-i-sys.md) | 矩形信息。 |
| [Screen](arkts-arkui-screen-screen-i-sys.md) | [物理屏](../../../../displaymanager/display-terminology.md#物理屏)屏幕实例。下列API示例中都需先使用[getAllScreens()](arkts-arkui-screen-getallscreens-f-sys.md#getallscreens-1)、[createVirtualScreen()](arkts-arkui-screen-createvirtualscreen-f-sys.md#createvirtualscreen-1)中的任一方法获取到Screen实例，再通过此实例调用对应方法。 |
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
| [ScreenType](arkts-arkui-screen-screentype-e-sys.md) | 屏幕类型枚举 |
<!--DelEnd-->

