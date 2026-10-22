# window

```TypeScript
declare namespace window
```

**起始版本：** 6

<!--Device-unnamed-declare namespace window--><!--Device-unnamed-declare namespace window-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createWindow](arkts-arkui-window-createwindow-f.md#createwindow-1) | 创建子窗口或者系统窗口，使用callback异步回调。 |
| [createWindow](arkts-arkui-window-createwindow-f.md#createwindow-2) | 创建子窗口或者系统窗口，使用Promise异步回调。 |
| [findWindow](arkts-arkui-window-findwindow-f.md#findwindow-1) | 查找指定名称对应的窗口。 |
| [getAllMainWindowInfo](arkts-arkui-window-getallmainwindowinfo-f.md#getallmainwindowinfo-1) | 获取全部主窗口信息，使用Promise异步回调。 |
| [getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md#getallwindowlayoutinfo-1) | 获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。 |
| [getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md#getallwindowlayoutinfo-2) | 根据option指定的过滤条件获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。当未传入option或其中的字段都为默认值时，当前接口与[getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md)等价。 |
| [getGlobalWindowMode](arkts-arkui-window-getglobalwindowmode-f.md#getglobalwindowmode-1) | 获取指定屏幕上生命周期位于前台的窗口对应的窗口模式，使用Promise异步回调。 |
| [getLastWindow](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1) | 获取当前应用内层级最高的子窗口，使用callback异步回调。 |
| [getLastWindow](arkts-arkui-window-getlastwindow-f.md#getlastwindow-2) | 获取当前应用内层级最高的子窗口，使用Promise异步回调。 |
| [getMainWindowSnapshot](arkts-arkui-window-getmainwindowsnapshot-f.md#getmainwindowsnapshot-1) | 获取一个或多个指定windowId的主窗口截图，使用Promise异步回调。 |
| [getVisibleWindowInfo](arkts-arkui-window-getvisiblewindowinfo-f.md#getvisiblewindowinfo-1) | 获取当前屏幕的可见主窗口（未退至后台的主窗口）信息。使用Promise异步回调。 |
| [getWindowsByCoordinate](arkts-arkui-window-getwindowsbycoordinate-f.md#getwindowsbycoordinate-1) | 查询本应用指定坐标下的可见窗口数组，按当前窗口层级排列，层级最高的窗口对应数组下标为0，使用Promise异步回调。 |
| [offApplicationFocusStateChange](arkts-arkui-window-offapplicationfocusstatechange-f.md#offapplicationfocusstatechange-1) | 关闭应用进程获焦状态变化的监听。 |
| [onApplicationFocusStateChange](arkts-arkui-window-onapplicationfocusstatechange-f.md#onapplicationfocusstatechange-1) | 开启应用进程获焦状态变化的监听。此监听针对应用间的获焦状态变化，若同应用内窗口间的获焦状态发生变化，则不会触发回调函数。 |
| [setStartWindowBackgroundColor](arkts-arkui-window-setstartwindowbackgroundcolor-f.md#setstartwindowbackgroundcolor-1) | 设置同一应用包名下指定moduleName、abilityName对应UIAbility的启动页背景色，使用Promise异步回调。 |
| [setWatermarkImageForAppWindows](arkts-arkui-window-setwatermarkimageforappwindows-f.md#setwatermarkimageforappwindows-1) | 设置或取消本应用进程下窗口的水印图片，使用Promise异步回调。该接口需要在[loadContent()](arkts-arkui-window-window-i.md#loadcontent-1)或[setUIContent()](arkts-arkui-window-window-i.md#setuicontent-1)调用生效后使用。 |
| [setWindowPosition](arkts-arkui-window-setwindowposition-f.md#setwindowposition-1) | 调整当前应用进程中一个或多个主窗口的z序。使用Promise异步回调。 |
| [shiftAppWindowFocus](arkts-arkui-window-shiftappwindowfocus-f.md#shiftappwindowfocus-1) | 在同应用内将窗口焦点从源窗口转移到目标窗口，仅支持应用主窗、子窗范围内的焦点转移。使用Promise异步回调。 |
| [shiftAppWindowPointerEvent](arkts-arkui-window-shiftappwindowpointerevent-f.md#shiftappwindowpointerevent-1) | 主窗口和子窗口可正常调用，用于将鼠标输入事件从源窗口转移到目标窗口。使用Promise异步回调。 |
| [shiftAppWindowTouchEvent](arkts-arkui-window-shiftappwindowtouchevent-f.md#shiftappwindowtouchevent-1) | 主窗口和子窗口可正常调用，用于将触屏输入事件从源窗口转移到目标窗口。使用Promise异步回调。 |
| [create](arkts-arkui-window-create-f.md#create-1) | 创建子窗口，使用callback异步回调。 |
| [create](arkts-arkui-window-create-f.md#create-2) | 创建子窗口，使用Promise异步回调。 |
| [create](arkts-arkui-window-create-f.md#create-3) | 创建系统窗口，使用Promise异步回调。 |
| [create](arkts-arkui-window-create-f.md#create-4) | 创建系统窗口，使用callback异步回调。 |
| [find](arkts-arkui-window-find-f.md#find-1) | 查找id所对应的窗口，使用callback异步回调。 |
| [find](arkts-arkui-window-find-f.md#find-2) | 查找id所对应的窗口，使用Promise异步回调。 |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md#gettopwindow-1) | 获取当前应用内最后显示的窗口，使用callback异步回调。 |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md#gettopwindow-2) | 获取当前应用内最后显示的窗口，使用Promise异步回调。 |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md#gettopwindow-3) | 获取当前应用内最后显示的窗口，使用Promise异步回调。 |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md#gettopwindow-4) | 获取当前应用内最后显示的窗口，使用callback异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createSubWindowAndBindParent](arkts-arkui-window-createsubwindowandbindparent-f-sys.md#createsubwindowandbindparent-1) | 创建一个子窗，并绑定父窗。使用Promise异步回调。 |
| [getSnapshot](arkts-arkui-window-getsnapshot-f-sys.md#getsnapshot-1) | 获取指定窗口相同尺寸截图，使用Promise异步回调。若当前窗口设置为隐私模式（可通过[setWindowPrivacyMode](arkts-arkui-window-window-i.md#setwindowprivacymode-2)接口设置），截图结果为白屏。 |
| [getTopNavDestinationName](arkts-arkui-window-gettopnavdestinationname-f-sys.md#gettopnavdestinationname-1) | 获取指定的前台窗口当前栈顶[Navigation](../arkts-components/arkts-arkui-navigation-comp.md)中的[NavDestination](../arkts-components/arkts-arkui-navdestination-comp.md)名称，使用Promise异步回调。 |
| [minimizeAll](arkts-arkui-window-minimizeall-f-sys.md#minimizeall-1) | 最小化指定ID的屏幕中的所有主窗口。 |
| [minimizeAll](arkts-arkui-window-minimizeall-f-sys.md#minimizeall-2) | 最小化指定ID的屏幕中的所有主窗口，使用Promise异步回调。 |
| [minimizeAllWithExclusion](arkts-arkui-window-minimizeallwithexclusion-f-sys.md#minimizeallwithexclusion-1) | 最小化指定ID的屏幕中除指定窗口之外的所有主窗口，使用Promise异步回调。 |
| [moveMainWindowToTargetDisplay](arkts-arkui-window-movemainwindowtotargetdisplay-f-sys.md#movemainwindowtotargetdisplay-1) | 将指定的主窗口迁移到指定的屏幕上。使用Promise异步回调。 |
| [notifyScreenshotEvent](arkts-arkui-window-notifyscreenshotevent-f-sys.md#notifyscreenshotevent-1) | 通知屏幕截屏的事件类型，使用Promise异步回调。 |
| [off('systemBarTintChange')](arkts-arkui-window-off-f-sys.md#offsystembartintchange) | 关闭状态栏、导航栏属性变化的监听。 |
| [off('gestureNavigationEnabledChange')](arkts-arkui-window-off-f-sys.md#offgesturenavigationenabledchange) | 移除手势导航启用状态变化的监听。 |
| [off('waterMarkFlagChange')](arkts-arkui-window-off-f-sys.md#offwatermarkflagchange) | 移除水印启用状态变化的监听。 |
| [on('systemBarTintChange')](arkts-arkui-window-on-f-sys.md#onsystembartintchange) | 开启状态栏、导航栏属性变化的监听。 |
| [on('gestureNavigationEnabledChange')](arkts-arkui-window-on-f-sys.md#ongesturenavigationenabledchange) | 添加手势导航启用状态变化的监听。 |
| [on('waterMarkFlagChange')](arkts-arkui-window-on-f-sys.md#onwatermarkflagchange) | 添加水印启用状态变化的监听。 |
| [setGestureNavigationEnabled](arkts-arkui-window-setgesturenavigationenabled-f-sys.md#setgesturenavigationenabled-1) | 设置手势导航启用状态。使用callback异步回调。系统出于安全的考虑，不会干预手势的禁用和恢复。应用调用本接口禁用手势后异常退出的情况下，如果想要恢复手势，需自行实现自动拉起机制并再次调用本接口恢复手势。 |
| [setGestureNavigationEnabled](arkts-arkui-window-setgesturenavigationenabled-f-sys.md#setgesturenavigationenabled-2) | 设置手势导航启用状态。使用Promise异步回调。系统出于安全的考虑，不会干预手势的禁用和恢复。应用调用本接口禁用手势后异常退出的情况下，如果想要恢复手势，需自行实现自动拉起机制并再次调用本接口恢复手势。 |
| [setSpecificSystemWindowZIndex](arkts-arkui-window-setspecificsystemwindowzindex-f-sys.md#setspecificsystemwindowzindex-1) | 设置系统窗口的窗口层级。使用Promise异步回调。 |
| [setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md#setwatermarkimage-1) | 设置屏幕水印图片显示状态。使用Promise异步回调。 |
| [setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md#setwatermarkimage-2) | 设置屏幕水印图片的显示状态，并设定水印的优先级。使用Promise异步回调。当priority等于0时，当前接口与[setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md#setwatermarkimage-3)等价。 |
| [setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md#setwatermarkimage-3) | 设置屏幕水印图片显示状态。使用callback异步回调。 |
| [toggleShownStateForAllAppWindows](arkts-arkui-window-toggleshownstateforallappwindows-f-sys.md#toggleshownstateforallappwindows-1) | 多窗口快速切换时隐藏或者恢复应用窗口。 |
| [toggleShownStateForAllAppWindows](arkts-arkui-window-toggleshownstateforallappwindows-f-sys.md#toggleshownstateforallappwindows-2) | 多窗口快速切换时隐藏或者恢复应用窗口，使用Promise异步回调。 |
| [setWindowLayoutMode](arkts-arkui-window-setwindowlayoutmode-f-sys.md#setwindowlayoutmode-1) | 设置窗口布局模式，使用callback异步回调。 |
| [setWindowLayoutMode](arkts-arkui-window-setwindowlayoutmode-f-sys.md#setwindowlayoutmode-2) | 设置窗口布局模式，使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AvoidArea](arkts-arkui-window-avoidarea-i.md) | 窗口内容的避让区域。 |
| [AvoidAreaOptions](arkts-arkui-window-avoidareaoptions-i.md) | 系统避让区变化后返回当前避让区域以及避让区域类型。 |
| [Configuration](arkts-arkui-window-configuration-i.md) | 创建子窗口或系统窗口时的参数。 |
| [DecorButtonStyle](arkts-arkui-window-decorbuttonstyle-i.md) | 系统装饰栏按钮样式。 |
| [FrameMetrics](arkts-arkui-window-framemetrics-i.md) | 帧率指标。 |
| [KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md) | 软键盘窗口信息。 |
| [KeyFramePolicy](arkts-arkui-window-keyframepolicy-i.md) | 关键帧的策略配置。 |
| [MainWindowInfo](arkts-arkui-window-mainwindowinfo-i.md) | 主窗口信息。 |
| [MaximizeOptions](arkts-arkui-window-maximizeoptions-i.md) | 最大化窗口时的可选配置。 |
| [MoveConfiguration](arkts-arkui-window-moveconfiguration-i.md) | 窗口移动选项。 |
| [OrientationResult](arkts-arkui-window-orientationresult-i.md) | 设置窗口显示方向的执行结果。 |
| [Position](arkts-arkui-window-position-i.md) | 窗口或组件的位置。 |
| [Rect](arkts-arkui-window-rect-i.md) | 窗口矩形区域。 |
| [RectChangeOptions](arkts-arkui-window-rectchangeoptions-i.md) | 窗口矩形（窗口位置及窗口大小）变化返回的值及变化原因。 |
| [RectInVP](arkts-arkui-window-rectinvp-i.md) | 窗口矩形区域，单位为vp。 |
| [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md) | 窗口旋转变化时的窗口信息。 |
| [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) | 应用在窗口旋转变化时返回的信息，系统会根据此信息改变当前窗口矩形区域大小。当返回主窗口旋转变化的信息时，系统不改变主窗口的大小。 |
| [ShowWindowOptions](arkts-arkui-window-showwindowoptions-i.md) | 显示子窗口或系统窗口时的参数。 |
| [Size](arkts-arkui-window-size-i.md) | 窗口大小，单位为px。 |
| [SizeInVP](arkts-arkui-window-sizeinvp-i.md) | 窗口大小，单位为vp。 |
| [StartAnimationParams](arkts-arkui-window-startanimationparams-i.md) | 启动动画配置。 |
| [StatusBarProperty](arkts-arkui-window-statusbarproperty-i.md) | 状态栏的属性。在获取状态栏属性信息时返回。 |
| [SubWindowOptions](arkts-arkui-window-subwindowoptions-i.md) | 子窗口创建参数。 |
| [SystemBarProperties](arkts-arkui-window-systembarproperties-i.md) | 状态栏<!--Del-->、三键导航栏的<!--DelEnd-->属性。 |
| [SystemBarStyle](arkts-arkui-window-systembarstyle-i.md) | 状态栏的属性。在设置页面级状态栏属性时使用。 |
| [TitleButtonRect](arkts-arkui-window-titlebuttonrect-i.md) | 标题栏上的最小化、最大化、关闭按钮矩形区域，该区域位置坐标相对窗口右上角。 |
| [TransitionAnimation](arkts-arkui-window-transitionanimation-i.md) | 窗口转场动画配置。 |
| [UIEnvAvoidAreaVP](arkts-arkui-window-uienvavoidareavp-i.md) | 以vp为单位表示的窗口避让区域信息，在进行[沉浸式布局](../../../windowmanager/window-terminology.md#immersive-layout沉浸式布局)适配时需关注。 |
| [UIEnvWindowAvoidAreaInfoPX](arkts-arkui-window-uienvwindowavoidareainfopx-i.md) | 窗口不同类型避让区域信息组成的[环境变量](../../../ui/arkts-env-system-property.md)数据类型，每种类型避让区域单位为px。 |
| [UIEnvWindowAvoidAreaInfoVP](arkts-arkui-window-uienvwindowavoidareainfovp-i.md) | 窗口不同类型避让区域信息组成的[环境变量](../../../ui/arkts-env-system-property.md)数据类型，每种类型避让区域单位为vp。 |
| [Window](arkts-arkui-window-window-i.md) | 当前窗口实例，窗口管理器管理的基本单元。 |
| [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md) | 窗口动画参数配置。 |
| [WindowCreateParams](arkts-arkui-window-windowcreateparams-i.md) | 应用启动时的窗口参数配置。 |
| [WindowDensityInfo](arkts-arkui-window-windowdensityinfo-i.md) | 窗口所在显示设备和窗口自定义的显示密度信息，是与像素单位无关的缩放系数，即显示大小缩放系数。 |
| [WindowFocusState](arkts-arkui-window-windowfocusstate-i.md) | 描述窗口的焦点状态变化信息。 |
| [WindowInfo](arkts-arkui-window-windowinfo-i.md) | 当前窗口的详细信息。 |
| [WindowInfoOptions](arkts-arkui-window-windowinfooptions-i.md) | 窗口布局信息过滤选项。 |
| [WindowLayoutInfo](arkts-arkui-window-windowlayoutinfo-i.md) | 窗口布局信息。 |
| [WindowLimits](arkts-arkui-window-windowlimits-i.md) | 窗口尺寸限制参数，应用可以通过[getWindowLimits](arkts-arkui-window-window-i.md#getwindowlimits)获得当前窗口的尺寸限制（单位为px）；从API version 22开始，还可以通过[getWindowLimitsVP](arkts-arkui-window-window-i.md#getwindowlimitsvp)获取窗口尺寸限制（单位为vp）。 |
| [WindowPositionParams](arkts-arkui-window-windowpositionparams-i.md) | 描述待调整z序的主窗口的位置。 |
| [WindowProperties](arkts-arkui-window-windowproperties-i.md) | 窗口属性。 |
| [WindowSnapshotAnimationConfig](arkts-arkui-window-windowsnapshotanimationconfig-i.md) | 窗口截图动效的配置。 |
| [WindowSnapshotConfiguration](arkts-arkui-window-windowsnapshotconfiguration-i.md) | 主窗口截图的配置项。 |
| [WindowStage](arkts-arkui-window-windowstage-i.md) | 窗口管理器。管理各个基本窗口单元，即[Window](arkts-arkui-window-n.md)实例。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Configuration](arkts-arkui-window-configuration-i-sys.md) | 创建子窗口或系统窗口时的参数。 |
| [ExtensionWindowConfig](arkts-arkui-window-extensionwindowconfig-i-sys.md) | 创建扩展窗口时需要配置的参数。 |
| [RotateOptions](arkts-arkui-window-rotateoptions-i-sys.md) | 旋转参数。 |
| [ScaleOptions](arkts-arkui-window-scaleoptions-i-sys.md) | 缩放参数。 |
| [StartAnimationSystemParams](arkts-arkui-window-startanimationsystemparams-i-sys.md) | 启动动画配置，仅对全屏应用生效。 |
| [StartMovingOptions](arkts-arkui-window-startmovingoptions-i-sys.md) | `startMovingWithOptions` 的可选配置。 |
| [SubWindowAttachOptions](arkts-arkui-window-subwindowattachoptions-i-sys.md) | 子窗与主窗保持相对位置不变时的参数。 |
| [SubWindowOptions](arkts-arkui-window-subwindowoptions-i-sys.md) | 子窗口创建参数。 |
| [SystemBarRegionTint](arkts-arkui-window-systembarregiontint-i-sys.md) | 单个导航栏或状态栏回调信息。 |
| [SystemBarTintState](arkts-arkui-window-systembartintstate-i-sys.md) | 当前系统栏回调信息集合。 |
| [SystemWindowOptions](arkts-arkui-window-systemwindowoptions-i-sys.md) | 系统窗口的创建参数。 |
| [TransitionContext](arkts-arkui-window-transitioncontext-i-sys.md) | 属性转换的上下文信息。 |
| [TransitionController](arkts-arkui-window-transitioncontroller-i-sys.md) | 属性转换控制器。使用其子接口之前得先创建系统窗口，参照示例代码。 |
| [TranslateOptions](arkts-arkui-window-translateoptions-i-sys.md) | 平移参数。 |
| [Window](arkts-arkui-window-window-i-sys.md) | 当前窗口实例，窗口管理器管理的基本单元。 |
| [WindowAnchorInfo](arkts-arkui-window-windowanchorinfo-i-sys.md) | 一级子窗与主窗保持相对位置的窗口锚点参数信息。 |
| [WindowCreateParams](arkts-arkui-window-windowcreateparams-i-sys.md) | 应用启动时的窗口参数配置。 |
| [WindowStage](arkts-arkui-window-windowstage-i-sys.md) | 窗口管理器。管理各个基本窗口单元，即[Window](arkts-arkui-window-n.md)实例。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [RotationChangeCallback](arkts-arkui-window-rotationchangecallback-t.md) | 旋转事件通知通用回调函数。 |
| [SpecificSystemBar](arkts-arkui-window-specificsystembar-t.md) | 当前支持显示或隐藏的系统栏类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AcrossDisplayPresentation](arkts-arkui-window-acrossdisplaypresentation-e.md) | 在可折叠的2in1设备的半折叠状态下，最大化窗口时用于控制瀑布流模式切换策略的枚举。 |
| [AnimationType](arkts-arkui-window-animationtype-e.md) | 窗口动画类型枚举。 |
| [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) | 窗口内容的避让区域的类型枚举。 |
| [ColorSpace](arkts-arkui-window-colorspace-e.md) | 色域模式。 |
| [FocusChangeReason](arkts-arkui-window-focuschangereason-e.md) | 窗口焦点状态变化原因枚举。 |
| [GlobalWindowMode](arkts-arkui-window-globalwindowmode-e.md) | 窗口模式。 |
| [MaximizePresentation](arkts-arkui-window-maximizepresentation-e.md) | 窗口最大化时的布局枚举。 |
| [ModalityType](arkts-arkui-window-modalitytype-e.md) | 子窗口模态类型枚举。 |
| [OcclusionState](arkts-arkui-window-occlusionstate-e.md) | 窗口可见性状态枚举。 |
| [Orientation](arkts-arkui-window-orientation-e.md) | 窗口显示方向类型枚举。<!--Del-->不同枚举值之间的区别可查询[窗口Orientation枚举值8\~10或12和枚举值13\~16的区别(API9)](../../../faqs/faqs-window-manager.md#窗口orientation枚举值810或12和枚举值1316的区别api9)。<!--DelEnd--> |
| [OrientationExecutionResult](arkts-arkui-window-orientationexecutionresult-e.md) | 窗口显示方向的执行结果枚举。 |
| [PixelUnit](arkts-arkui-window-pixelunit-e.md) | 像素单位枚举。 |
| [RectChangeReason](arkts-arkui-window-rectchangereason-e.md) | 窗口矩形（窗口位置及窗口大小）变化的原因。 |
| [RectType](arkts-arkui-window-recttype-e.md) | 窗口矩形区域坐标系类型。 |
| [RotationChangeType](arkts-arkui-window-rotationchangetype-e.md) | 窗口旋转事件类型。 |
| [RotationInfoType](arkts-arkui-window-rotationinfotype-e.md) | 旋转信息类型枚举。 |
| [ScreenshotEventType](arkts-arkui-window-screenshoteventtype-e.md) | 截屏事件类型枚举。 |
| [SplitRatioPreference](arkts-arkui-window-splitratiopreference-e.md) | 描述分屏窗口分屏比例 |
| [WindowAnchor](arkts-arkui-window-windowanchor-e.md) | 窗口锚点枚举。 |
| [WindowAnimationCurve](arkts-arkui-window-windowanimationcurve-e.md) | 窗口动画曲线类型。 |
| [WindowEventType](arkts-arkui-window-windoweventtype-e.md) | 窗口生命周期。 |
| [WindowPosition](arkts-arkui-window-windowposition-e.md) | 主窗口z序调整的目标位置枚举。 |
| [WindowPostureMode](arkts-arkui-window-windowposturemode-e.md) | 窗口姿态模式枚举。 |
| [WindowStageEventType](arkts-arkui-window-windowstageeventtype-e.md) | WindowStage生命周期状态枚举。 |
| [WindowStageLifecycleEventType](arkts-arkui-window-windowstagelifecycleeventtype-e.md) | WindowStage生命周期的状态类型枚举。 |
| [WindowStatusType](arkts-arkui-window-windowstatustype-e.md) | 窗口模式枚举。 |
| [WindowTransitionType](arkts-arkui-window-windowtransitiontype-e.md) | 窗口转场动画类型枚举。 |
| [WindowType](arkts-arkui-window-windowtype-e.md) | 窗口类型枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AnimationType](arkts-arkui-window-animationtype-e-sys.md) | 窗口动画类型枚举。 |
| [BlurStyle](arkts-arkui-window-blurstyle-e-sys.md) | 窗口模糊类型枚举。 |
| [ExtensionWindowAttribute](arkts-arkui-window-extensionwindowattribute-e-sys.md) | 扩展窗口的属性枚举。 |
| [WindowMode](arkts-arkui-window-windowmode-e-sys.md) | 窗口模式枚举。 |
| [WindowType](arkts-arkui-window-windowtype-e-sys.md) | 窗口类型枚举。 |
| [WindowLayoutMode](arkts-arkui-window-windowlayoutmode-e-sys.md) | 窗口布局模式枚举。 |
<!--DelEnd-->
