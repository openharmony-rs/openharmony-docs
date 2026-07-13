# window

Window manager.

**起始版本：** 6

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createWindow](arkts-arkui-createwindow-f.md#createwindow-1) | 创建子窗口或者系统窗口，使用callback异步回调。非[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。自由窗口状态下，子窗口参数[decorEnabled](arkts-arkui-configuration-i.md)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口创建后为非沉浸式布局。 |
| [createWindow](arkts-arkui-createwindow-f.md#createwindow-2) | 创建子窗口或者系统窗口，使用Promise异步回调。非[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。自由窗口状态下，子窗口参数[decorEnabled](arkts-arkui-configuration-i.md)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口创建后为非沉浸式布局。 |
| [create](arkts-arkui-create-f.md#create-1) | 创建子窗口，使用callback异步回调。子窗口创建后默认是[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。@link window.createWindow(config: Configuration, callback: AsyncCallback&lt;Window&gt;)}替代。 |
| [create](arkts-arkui-create-f.md#create-2) | 创建子窗口，使用Promise异步回调。子窗口创建后默认是[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。@link window.createWindow(config: Configuration)}替代。 |
| [create](arkts-arkui-create-f.md#create-3) | 创建系统窗口，使用Promise异步回调。@link window.createWindow(config: Configuration)}替代。 |
| [create](arkts-arkui-create-f.md#create-4) | 创建系统窗口，使用callback异步回调。@link window.createWindow(config: Configuration, callback: AsyncCallback&lt;Window&gt;)}替代。 |
| [find](arkts-arkui-find-f.md#find-1) | 查找id所对应的窗口，使用callback异步回调。@link window.findWindow}替代。 |
| [find](arkts-arkui-find-f.md#find-2) | 查找id所对应的窗口，使用Promise异步回调。@link window.findWindow}替代。 |
| [findWindow](arkts-arkui-findwindow-f.md#findwindow-1) | 查找指定名称对应的窗口。 |
| [getTopWindow](arkts-arkui-gettopwindow-f.md#gettopwindow-1) | 获取当前应用内最后显示的窗口，使用callback异步回调。@link window.getLastWindow(ctx: BaseContext, callback: AsyncCallback&lt;Window&gt;)}替代。 |
| [getTopWindow](arkts-arkui-gettopwindow-f.md#gettopwindow-2) | 获取当前应用内最后显示的窗口，使用Promise异步回调。@link window.getLastWindow(ctx: BaseContext)}替代。 |
| [getTopWindow](arkts-arkui-gettopwindow-f.md#gettopwindow-3) | 获取当前应用内最后显示的窗口，使用Promise异步回调。@link window.getLastWindow(ctx: BaseContext)}替代。 |
| [getTopWindow](arkts-arkui-gettopwindow-f.md#gettopwindow-4) | 获取当前应用内最后显示的窗口，使用callback异步回调。@link window.getLastWindow(ctx: BaseContext, callback: AsyncCallback&lt;Window&gt;)}替代。 |
| [getLastWindow](arkts-arkui-getlastwindow-f.md#getlastwindow-1) | 获取当前应用内层级最高的子窗口，使用callback异步回调。若无应用子窗口或子窗口未调用[showWindow()](arkts-arkui-window-i.md#showwindow-1)进行显示，则返回应用主窗口。 |
| [getLastWindow](arkts-arkui-getlastwindow-f.md#getlastwindow-2) | 获取当前应用内层级最高的子窗口，使用Promise异步回调。若无应用子窗口或子窗口未调用[showWindow()](arkts-arkui-window-i.md#showwindow-1)进行显示，则返回应用主窗口。 |
| [shiftAppWindowFocus](arkts-arkui-shiftappwindowfocus-f.md#shiftappwindowfocus-1) | 在同应用内将窗口焦点从源窗口转移到目标窗口，仅支持应用主窗、子窗范围内的焦点转移。使用Promise异步回调。目标窗口需确保具有获得焦点的能力（可通过[setWindowFocusable()](arkts-arkui-window-i.md#setwindowfocusable-2)设置），并确保调用[showWindow()](arkts-arkui-window-i.md#showwindow-1)成功且执行完毕。@link @ohos.window:window.Window.loadContent(path: string, storage: LocalStorage, callback: AsyncCallback&lt;void&gt;)}&gt; 或[setUIContent()](arkts-arkui-window-i.md#setuicontent-1)并生效，&gt; 否则可能会导致不可见窗口获取焦点，造成功能异常或影响用户体验。 |
| [shiftAppWindowPointerEvent](arkts-arkui-shiftappwindowpointerevent-f.md#shiftappwindowpointerevent-1) | 主窗口和子窗口可正常调用，用于将鼠标输入事件从源窗口转移到目标窗口。使用Promise异步回调。源窗口仅在[onTouch](../../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch)事件（事件类型必须为TouchType.Down）的回调方法中调用此接口才会有鼠标输入事件转移效果，成功调用此接口后，系统会向源窗口补发鼠标按键抬起（TouchType.Up）事件，并且向目标窗口补发鼠标按键按下（TouchType.Down）事件。 |
| [shiftAppWindowTouchEvent](arkts-arkui-shiftappwindowtouchevent-f.md#shiftappwindowtouchevent-1) | 主窗口和子窗口可正常调用，用于将触屏输入事件从源窗口转移到目标窗口。使用Promise异步回调。源窗口仅在[onTouch](../../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch)事件（事件类型必须为TouchType.Down）的回调方法中调用此接口才会有触屏输入事件转移效果，成功调用此接口后，系统会向源窗口补发触屏抬起（TouchType.Up）事件，并且向目标窗口补发触屏按下（TouchType.Down）事件。 |
| [getWindowsByCoordinate](arkts-arkui-getwindowsbycoordinate-f.md#getwindowsbycoordinate-1) | 查询本应用指定坐标下的可见窗口数组，按当前窗口层级排列，层级最高的窗口对应数组下标为0，使用Promise异步回调。 |
| [getAllWindowLayoutInfo](arkts-arkui-getallwindowlayoutinfo-f.md#getallwindowlayoutinfo-1) | 获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。 |
| [getAllWindowLayoutInfo](arkts-arkui-getallwindowlayoutinfo-f.md#getallwindowlayoutinfo-2) | 根据option指定的过滤条件获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。当未传入option或其中的字段都为默认值时，当前接口与[getAllWindowLayoutInfo](arkts-arkui-getallwindowlayoutinfo-f.md#getallwindowlayoutinfo-1)等价。 |
| [getGlobalWindowMode](arkts-arkui-getglobalwindowmode-f.md#getglobalwindowmode-1) | 获取指定屏幕上生命周期位于前台的窗口对应的窗口模式，使用Promise异步回调。 |
| [onApplicationFocusStateChange](arkts-arkui-onapplicationfocusstatechange-f.md#onapplicationfocusstatechange-1) | 开启应用进程获焦状态变化的监听。此监听针对应用间的获焦状态变化，若同应用内窗口间的获焦状态发生变化，则不会触发回调函数。 |
| [offApplicationFocusStateChange](arkts-arkui-offapplicationfocusstatechange-f.md#offapplicationfocusstatechange-1) | 关闭应用进程获焦状态变化的监听。 |
| [setStartWindowBackgroundColor](arkts-arkui-setstartwindowbackgroundcolor-f.md#setstartwindowbackgroundcolor-1) | 设置同一应用包名下指定moduleName、abilityName对应UIAbility的启动页背景色，使用Promise异步回调。该接口对同一应用包名下的所有进程生效，例如多实例或应用分身场景。 |
| [setWatermarkImageForAppWindows](arkts-arkui-setwatermarkimageforappwindows-f.md#setwatermarkimageforappwindows-1) | 设置或取消本应用进程下窗口的水印图片，使用Promise异步回调。该接口需要在[loadContent()](arkts-arkui-window-i.md#loadcontent-1)或[setUIContent()](arkts-arkui-window-i.md#setuicontent-1)调用生效后使用。 |
| [getAllMainWindowInfo](arkts-arkui-getallmainwindowinfo-f.md#getallmainwindowinfo-1) | 获取全部主窗口信息，使用Promise异步回调。 |
| [getMainWindowSnapshot](arkts-arkui-getmainwindowsnapshot-f.md#getmainwindowsnapshot-1) | 获取一个或多个指定windowId的主窗口截图，使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createSubWindowAndBindParent](arkts-arkui-createsubwindowandbindparent-f-sys.md#createsubwindowandbindparent-1) | 创建一个子窗，并绑定父窗。使用Promise异步回调。子窗跟随父窗显示/隐藏，但并不跟随父窗销毁，子窗通过回调函数监听父窗生命周期变化。建议在父窗销毁后主动销毁创建的子窗。 |
| [minimizeAll](arkts-arkui-minimizeall-f-sys.md#minimizeall-1) | 最小化指定ID的屏幕中的所有主窗口。 |
| [minimizeAll](arkts-arkui-minimizeall-f-sys.md#minimizeall-2) | 最小化指定ID的屏幕中的所有主窗口，使用Promise异步回调。 |
| [minimizeAllWithExclusion](arkts-arkui-minimizeallwithexclusion-f-sys.md#minimizeallwithexclusion-1) | 最小化指定ID的屏幕中除指定窗口之外的所有主窗口，使用Promise异步回调。 |
| [toggleShownStateForAllAppWindows](arkts-arkui-toggleshownstateforallappwindows-f-sys.md#toggleshownstateforallappwindows-1) | 多窗口快速切换时隐藏或者恢复应用窗口。 |
| [toggleShownStateForAllAppWindows](arkts-arkui-toggleshownstateforallappwindows-f-sys.md#toggleshownstateforallappwindows-2) | 多窗口快速切换时隐藏或者恢复应用窗口，使用Promise异步回调。 |
| [setWindowLayoutMode](arkts-arkui-setwindowlayoutmode-f-sys.md#setwindowlayoutmode-1) | 设置窗口布局模式，使用callback异步回调。 |
| [setWindowLayoutMode](arkts-arkui-setwindowlayoutmode-f-sys.md#setwindowlayoutmode-2) | 设置窗口布局模式，使用Promise异步回调。 |
| [setGestureNavigationEnabled](arkts-arkui-setgesturenavigationenabled-f-sys.md#setgesturenavigationenabled-1) | 设置手势导航启用状态。使用callback异步回调。系统出于安全的考虑，不会干预手势的禁用和恢复。应用调用本接口禁用手势后异常退出的情况下，如果想要恢复手势，需自行实现自动拉起机制并再次调用本接口恢复手势。 |
| [setGestureNavigationEnabled](arkts-arkui-setgesturenavigationenabled-f-sys.md#setgesturenavigationenabled-2) | 设置手势导航启用状态。使用Promise异步回调。系统出于安全的考虑，不会干预手势的禁用和恢复。应用调用本接口禁用手势后异常退出的情况下，如果想要恢复手势，需自行实现自动拉起机制并再次调用本接口恢复手势。 |
| [setWaterMarkImage](arkts-arkui-setwatermarkimage-f-sys.md#setwatermarkimage-1) | 设置屏幕水印图片显示状态。使用Promise异步回调。 |
| [setWaterMarkImage](arkts-arkui-setwatermarkimage-f-sys.md#setwatermarkimage-2) | 设置屏幕水印图片的显示状态，并设定水印的优先级。使用Promise异步回调。当priority等于0时，当前接口与[setWaterMarkImage](arkts-arkui-setwatermarkimage-f-sys.md#setwatermarkimage-3)等价。 |
| [setWaterMarkImage](arkts-arkui-setwatermarkimage-f-sys.md#setwatermarkimage-3) | 设置屏幕水印图片显示状态。使用callback异步回调。 |
| [setSpecificSystemWindowZIndex](arkts-arkui-setspecificsystemwindowzindex-f-sys.md#setspecificsystemwindowzindex-1) | 设置系统窗口的窗口层级。使用Promise异步回调。将所有该类型系统窗口zIndex调整为所设置的值，调整前后，该类型窗口之间相对层级保持不变，焦点窗口不发生变化。当应用关闭之后该类型窗口层级恢复默认值。推荐不同类型窗口设置不同的zIndex，如果已经存在相同zIndex的窗口，设置前后，窗口之间的相对层级保持不变。 |
| [getVisibleWindowInfo](arkts-arkui-getvisiblewindowinfo-f-sys.md#getvisiblewindowinfo-1) | 获取当前屏幕的可见主窗口（未退至后台的主窗口）信息。使用Promise异步回调。 |
| [getTopNavDestinationName](arkts-arkui-gettopnavdestinationname-f-sys.md#gettopnavdestinationname-1) | 获取指定的前台窗口当前栈顶[Navigation](./@internal/component/ets/navigation)中的[NavDestination](./@internal/component/ets/nav_destination)名称，使用Promise异步回调。 |
| [getSnapshot](arkts-arkui-getsnapshot-f-sys.md#getsnapshot-1) | 获取指定窗口相同尺寸截图，使用Promise异步回调。若当前窗口设置为隐私模式（可通过[setWindowPrivacyMode](arkts-arkui-window-i.md#setwindowprivacymode-2)接口设置），截图结果为白屏。 |
| [on](arkts-arkui-on-f-sys.md#on-1) | 开启状态栏、导航栏属性变化的监听。 |
| [off](arkts-arkui-off-f-sys.md#off-1) | 关闭状态栏、导航栏属性变化的监听。 |
| [on](arkts-arkui-on-f-sys.md#on-2) | 添加手势导航启用状态变化的监听。 |
| [off](arkts-arkui-off-f-sys.md#off-2) | 移除手势导航启用状态变化的监听。 |
| [on](arkts-arkui-on-f-sys.md#on-3) | 添加水印启用状态变化的监听。 |
| [off](arkts-arkui-off-f-sys.md#off-3) | 移除水印启用状态变化的监听。 |
| [notifyScreenshotEvent](arkts-arkui-notifyscreenshotevent-f-sys.md#notifyscreenshotevent-1) | 通知屏幕截屏的事件类型，使用Promise异步回调。 |
| [moveMainWindowToTargetDisplay](arkts-arkui-movemainwindowtotargetdisplay-f-sys.md#movemainwindowtotargetdisplay-1) | 将指定的主窗口迁移到指定的屏幕上。使用Promise异步回调。- 对于[主屏](../../../../displaymanager/display-terminology.md#主屏)/[扩展屏](../../../../displaymanager/display-terminology.md#扩展屏)与[虚拟屏](../../../../displaymanager/display-terminology.md#虚拟屏)之间以及虚拟屏与虚拟屏之间的窗口迁移，仅主窗及其子窗会一起被迁移到对应屏幕上且被抬升，如果存在子窗，最上层可获焦子窗会获取焦点，否则主窗口获焦。- 对于主屏与扩展屏之间的窗口迁移，只会将主窗口迁移到对应屏幕，抬升并获取焦点。&lt;!--RP3--&gt;&lt;!--RP3End--&gt; |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [StatusBarProperty](arkts-arkui-statusbarproperty-i.md) | 状态栏的属性。在获取状态栏属性信息时返回。 |
| [FrameMetrics](arkts-arkui-framemetrics-i.md) | 帧率指标。 |
| [Rect](arkts-arkui-rect-i.md) | 窗口矩形区域。 |
| [RectInVP](arkts-arkui-rectinvp-i.md) | 窗口矩形区域，单位为vp。 |
| [Position](arkts-arkui-position-i.md) | 窗口或组件的位置。 |
| [AvoidArea](arkts-arkui-avoidarea-i.md) | 窗口内容的避让区域。窗口内容做[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)适配时，需要按照[AvoidAreaType](arkts-arkui-avoidareatype-e.md)对应的AvoidArea做窗口内容避让。在避让区域内，应用窗口内容被遮挡且无法响应用户点击事件。 |
| [UIEnvAvoidAreaVP](arkts-arkui-uienvavoidareavp-i.md) | 以vp为单位表示的窗口避让区域信息，在进行[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)适配时需关注。 |
| [Size](arkts-arkui-size-i.md) | 窗口大小，单位为px。 |
| [SizeInVP](arkts-arkui-sizeinvp-i.md) | 窗口大小，单位为vp。 |
| [WindowInfo](arkts-arkui-windowinfo-i.md) | 当前窗口的详细信息。 |
| [WindowDensityInfo](arkts-arkui-windowdensityinfo-i.md) | 窗口所在显示设备和窗口自定义的显示密度信息，是与像素单位无关的缩放系数，即显示大小缩放系数。 |
| [WindowProperties](arkts-arkui-windowproperties-i.md) | 窗口属性。 |
| [DecorButtonStyle](arkts-arkui-decorbuttonstyle-i.md) | 系统装饰栏按钮样式。 |
| [Configuration](arkts-arkui-configuration-i.md) | 创建子窗口或系统窗口时的参数。 |
| [WindowLimits](arkts-arkui-windowlimits-i.md) | 窗口尺寸限制参数，应用可以通过[getWindowLimits](arkts-arkui-window-i.md#getwindowlimits-1)获得当前窗口的尺寸限制（单位为px）；从API version 22开始，还可以通过[getWindowLimitsVP](arkts-arkui-window-i.md#getwindowlimitsvp-1)获取窗口尺寸限制（单位为vp）。窗口尺寸限制的最终生效结果由默认系统限制、应用配置和运行时设置的数据取交集得到，优先级从高到低依次为：1. 应用通过[setWindowLimits](arkts-arkui-window-i.md#setwindowlimits-1)设置窗口尺寸限制。2. 应用在[startAbility](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#startability-3)拉起窗口时通过[StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-startoptions-c.md)指定窗口尺寸限制（API version 17开始支持）。3. 应用在[module.json5配置文件中的abilities标签](../../../../quick-start/module-configuration-file.md#abilities标签)中配置windowLimits。4. 默认系统限制（基于不同产品和窗口类型，其windowLimits系统默认限制存在差异）。 |
| [TitleButtonRect](arkts-arkui-titlebuttonrect-i.md) | 标题栏上的最小化、最大化、关闭按钮矩形区域，该区域位置坐标相对窗口右上角。 |
| [RectChangeOptions](arkts-arkui-rectchangeoptions-i.md) | 窗口矩形（窗口位置及窗口大小）变化返回的值及变化原因。 |
| [AvoidAreaOptions](arkts-arkui-avoidareaoptions-i.md) | 系统避让区变化后返回当前避让区域以及避让区域类型。 |
| [UIEnvWindowAvoidAreaInfoPX](arkts-arkui-uienvwindowavoidareainfopx-i.md) | 窗口不同类型避让区域信息组成的[环境变量](../../../../ui/arkts-env-system-property.md)数据类型，每种类型避让区域单位为px。 |
| [UIEnvWindowAvoidAreaInfoVP](arkts-arkui-uienvwindowavoidareainfovp-i.md) | 窗口不同类型避让区域信息组成的[环境变量](../../../../ui/arkts-env-system-property.md)数据类型，每种类型避让区域单位为vp。 |
| [MainWindowInfo](arkts-arkui-mainwindowinfo-i.md) | 主窗口信息。 |
| [WindowSnapshotConfiguration](arkts-arkui-windowsnapshotconfiguration-i.md) | 主窗口截图的配置项。 |
| [OrientationResult](arkts-arkui-orientationresult-i.md) | 设置窗口显示方向的执行结果。 |
| [RotationChangeInfo](arkts-arkui-rotationchangeinfo-i.md) | 窗口旋转变化时的窗口信息。 |
| [RotationChangeResult](arkts-arkui-rotationchangeresult-i.md) | 应用在窗口旋转变化时返回的信息，系统会根据此信息改变当前窗口矩形区域大小。当返回主窗口旋转变化的信息时，系统不改变主窗口的大小。应用窗口与系统窗口大小存在限制，具体限制与相关规则可见[resize](arkts-arkui-window-i.md#resize-2)。 |
| [WindowAnimationConfig](arkts-arkui-windowanimationconfig-i.md) | 窗口动画参数配置。 |
| [TransitionAnimation](arkts-arkui-transitionanimation-i.md) | 窗口转场动画配置。 |
| [MaximizeOptions](arkts-arkui-maximizeoptions-i.md) | 最大化窗口时的可选配置。 |
| [MoveConfiguration](arkts-arkui-moveconfiguration-i.md) | 窗口移动选项。 |
| [StartAnimationParams](arkts-arkui-startanimationparams-i.md) | 启动动画配置。仅对同应用的不同ability间跳转生效。仅对全屏应用生效。 |
| [WindowCreateParams](arkts-arkui-windowcreateparams-i.md) | 应用启动时的窗口参数配置。 |
| [WindowSnapshotAnimationConfig](arkts-arkui-windowsnapshotanimationconfig-i.md) | 窗口截图动效的配置。 |
| [KeyboardInfo](arkts-arkui-keyboardinfo-i.md) | 软键盘窗口信息。 |
| [KeyFramePolicy](arkts-arkui-keyframepolicy-i.md) | 关键帧的策略配置。 |
| [Window](arkts-arkui-window-i.md) | 当前窗口实例，窗口管理器管理的基本单元。下列API示例中都需先使用[getLastWindow()](arkts-arkui-getlastwindow-f.md#getlastwindow-1)、[createWindow()](arkts-arkui-createwindow-f.md#createwindow-1)、[findWindow()](arkts-arkui-findwindow-f.md#findwindow-1)中的任一方法获取到Window实例（windowClass），再通过此实例调用对应方法。 |
| [ShowWindowOptions](arkts-arkui-showwindowoptions-i.md) | 显示子窗口或系统窗口时的参数。 |
| [SubWindowOptions](arkts-arkui-subwindowoptions-i.md) | 子窗口创建参数。 |
| [WindowStage](arkts-arkui-windowstage-i.md) | 窗口管理器。管理各个基本窗口单元，即[Window](arkts-window.md)实例。下列API示例中都需在[onWindowStageCreate()](../../apis-ability-kit/arkts-apis/arkts-ability-uiability-c.md#onwindowstagecreate-1)函数中使用WindowStage的实例调用对应方法。 |
| [WindowLayoutInfo](arkts-arkui-windowlayoutinfo-i.md) | 窗口布局信息。 |
| [WindowInfoOptions](arkts-arkui-windowinfooptions-i.md) | 窗口布局信息过滤选项。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SystemBarProperties](arkts-arkui-systembarproperties-i.md) | 状态栏&lt;!--Del--&gt;、三键导航栏的&lt;!--DelEnd--&gt;属性。 |
| [SystemBarStyle](arkts-arkui-systembarstyle-i.md) | 状态栏的属性。在设置页面级状态栏属性时使用。 |
| [SystemBarRegionTint](arkts-arkui-systembarregiontint-i-sys.md) | 单个导航栏或状态栏回调信息。 |
| [SystemBarTintState](arkts-arkui-systembartintstate-i-sys.md) | 当前系统栏回调信息集合。 |
| [WindowAnchorInfo](arkts-arkui-windowanchorinfo-i-sys.md) | 一级子窗与主窗保持相对位置的窗口锚点参数信息。 |
| [SubWindowAttachOptions](arkts-arkui-subwindowattachoptions-i-sys.md) | 子窗与主窗保持相对位置不变时的参数。 |
| [WindowInfo](arkts-arkui-windowinfo-i-sys.md) | 当前窗口的详细信息。 |
| [ScaleOptions](arkts-arkui-scaleoptions-i-sys.md) | 缩放参数。 |
| [RotateOptions](arkts-arkui-rotateoptions-i-sys.md) | 旋转参数。 |
| [TranslateOptions](arkts-arkui-translateoptions-i-sys.md) | 平移参数。 |
| [TransitionContext](arkts-arkui-transitioncontext-i-sys.md) | 属性转换的上下文信息。 |
| [TransitionController](arkts-arkui-transitioncontroller-i-sys.md) | 属性转换控制器。使用其子接口之前得先创建系统窗口，参照示例代码。 |
| [Configuration](arkts-arkui-configuration-i-sys.md) | 创建子窗口或系统窗口时的参数。 |
| [StartAnimationSystemParams](arkts-arkui-startanimationsystemparams-i-sys.md) | 启动动画配置，仅对全屏应用生效。不同应用间跳转场景不生效，仍保持系统默认动效。 |
| [WindowCreateParams](arkts-arkui-windowcreateparams-i-sys.md) | 应用启动时的窗口参数配置。 |
| [Window](arkts-arkui-window-i-sys.md) | 当前窗口实例，窗口管理器管理的基本单元。下列API示例中都需先使用[getLastWindow()](arkts-arkui-getlastwindow-f.md#getlastwindow-1)、[createWindow()](arkts-arkui-createwindow-f.md#createwindow-1)、[findWindow()](arkts-arkui-findwindow-f.md#findwindow-1)中的任一方法获取到Window实例（windowClass），再通过此实例调用对应方法。 |
| [SubWindowOptions](arkts-arkui-subwindowoptions-i-sys.md) | 子窗口创建参数。 |
| [WindowStage](arkts-arkui-windowstage-i-sys.md) | 窗口管理器。管理各个基本窗口单元，即[Window](arkts-window.md)实例。下列API示例中都需在[onWindowStageCreate()](../../apis-ability-kit/arkts-apis/arkts-ability-uiability-c.md#onwindowstagecreate-1)函数中使用WindowStage的实例调用对应方法。 |
| [SystemWindowOptions](arkts-arkui-systemwindowoptions-i-sys.md) | 系统窗口的创建参数。 |
| [ExtensionWindowConfig](arkts-arkui-extensionwindowconfig-i-sys.md) | 创建扩展窗口时需要配置的参数。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WindowType](arkts-arkui-windowtype-e.md) | 窗口类型枚举。 |
| [AvoidAreaType](arkts-arkui-avoidareatype-e.md) | 窗口内容的避让区域的类型枚举。窗口内容做[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)适配时，需要按照AvoidAreaType对应的[AvoidArea](arkts-arkui-avoidarea-i.md)做窗口内容避让。&lt;!--RP13--&gt;&lt;!--RP13End--&gt; |
| [SplitRatioPreference](arkts-arkui-splitratiopreference-e.md) | 描述分屏窗口分屏比例 |
| [WindowStatusType](arkts-arkui-windowstatustype-e.md) | 窗口模式枚举。 |
| [PixelUnit](arkts-arkui-pixelunit-e.md) | 像素单位枚举。物理像素单位和虚拟像素单位换算可使用[px2vp](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#px2vp12)和[vp2px](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#vp2px12)。 |
| [WindowAnimationCurve](arkts-arkui-windowanimationcurve-e.md) | 窗口动画曲线类型。 |
| [WindowTransitionType](arkts-arkui-windowtransitiontype-e.md) | 窗口转场动画类型枚举。 |
| [AnimationType](arkts-arkui-animationtype-e.md) | 窗口动画类型枚举。 |
| [WindowAnchor](arkts-arkui-windowanchor-e.md) | 窗口锚点枚举。 |
| [ColorSpace](arkts-arkui-colorspace-e.md) | 色域模式。 |
| [RectChangeReason](arkts-arkui-rectchangereason-e.md) | 窗口矩形（窗口位置及窗口大小）变化的原因。 |
| [OcclusionState](arkts-arkui-occlusionstate-e.md) | 窗口可见性状态枚举。 |
| [Orientation](arkts-arkui-orientation-e.md) | 窗口显示方向类型枚举。&lt;!--Del--&gt;不同枚举值之间的区别可查询[窗口Orientation枚举值8\~10或12和枚举值13\~16的区别(API9)](../../../../faqs/faqs-window-manager.md#窗口orientation枚举值810或12和枚举值1316的区别api9)。&lt;!--DelEnd--&gt; |
| [OrientationExecutionResult](arkts-arkui-orientationexecutionresult-e.md) | 窗口显示方向的执行结果枚举。 |
| [RotationChangeType](arkts-arkui-rotationchangetype-e.md) | 窗口旋转事件类型。 |
| [RectType](arkts-arkui-recttype-e.md) | 窗口矩形区域坐标系类型。 |
| [ScreenshotEventType](arkts-arkui-screenshoteventtype-e.md) | 截屏事件类型枚举。 |
| [RotationInfoType](arkts-arkui-rotationinfotype-e.md) | 旋转信息类型枚举。 |
| [WindowEventType](arkts-arkui-windoweventtype-e.md) | 窗口生命周期。 |
| [MaximizePresentation](arkts-arkui-maximizepresentation-e.md) | 窗口最大化时的布局枚举。 |
| [AcrossDisplayPresentation](arkts-arkui-acrossdisplaypresentation-e.md) | 在可折叠的2in1设备的半折叠状态下，最大化窗口时用于控制瀑布流模式切换策略的枚举。 |
| [GlobalWindowMode](arkts-arkui-globalwindowmode-e.md) | 窗口模式。 |
| [WindowStageEventType](arkts-arkui-windowstageeventtype-e.md) | WindowStage生命周期状态枚举。 |
| [WindowStageLifecycleEventType](arkts-arkui-windowstagelifecycleeventtype-e.md) | WindowStage生命周期的状态类型枚举。 |
| [ModalityType](arkts-arkui-modalitytype-e.md) | 子窗口模态类型枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [WindowType](arkts-arkui-windowtype-e-sys.md) | 窗口类型枚举。 |
| [WindowMode](arkts-arkui-windowmode-e-sys.md) | 窗口模式枚举。 |
| [WindowLayoutMode](arkts-arkui-windowlayoutmode-e-sys.md) | 窗口布局模式枚举。 |
| [AnimationType](arkts-arkui-animationtype-e-sys.md) | 窗口动画类型枚举。 |
| [BlurStyle](arkts-arkui-blurstyle-e-sys.md) | 窗口模糊类型枚举。 |
| [ExtensionWindowAttribute](arkts-arkui-extensionwindowattribute-e-sys.md) | 扩展窗口的属性枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [RotationChangeCallback](arkts-arkui-rotationchangecallback-t.md) | 旋转事件通知通用回调函数。开发者在使用时，回调函数参数类型为[RotationChangeInfo](arkts-arkui-rotationchangeinfo-i.md)，返回值类型为[RotationChangeResult](arkts-arkui-rotationchangeresult-i.md) \\| void。 |
| [SpecificSystemBar](arkts-arkui-specificsystembar-t.md) | 当前支持显示或隐藏的系统栏类型。 |

