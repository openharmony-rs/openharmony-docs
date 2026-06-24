# window

Window manager.

**起始版本：** 6

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createWindow](arkts-arkui-window-createwindow-f.md#createWindow-1) | 创建子窗口或者系统窗口，使用callback异步回调。<br/><br/>非[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是<br/>[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。<br/><br/>自由窗口状态下，子窗口参数[decorEnabled](arkts-arkui-window-configuration-i.md#Configuration)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口<br/>创建后为非沉浸式布局。<br/> |
| [createWindow](arkts-arkui-window-createwindow-f.md#createWindow-2) | 创建子窗口或者系统窗口，使用Promise异步回调。<br/><br/>非[自由窗口](../../../../windowmanager/window-terminology.md#自由窗口)状态下，子窗口创建后默认是<br/>[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。<br/><br/>自由窗口状态下，子窗口参数[decorEnabled](arkts-arkui-window-configuration-i.md#Configuration)为false时，子窗口创建后为沉浸式布局；子窗口参数decorEnabled为true，子窗口<br/>创建后为非沉浸式布局。<br/> |
| [create](arkts-arkui-window-create-f.md#create-1) | 创建子窗口，使用callback异步回调。<br/><br/>子窗口创建后默认是[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃，参数id传入null或undefined时，可能会导致callback无法得到执行，建议使用<br/>&gt; [createWindow()](window.createWindow(config: Configuration, callback: AsyncCallback&lt;Window&gt;))替代。<br/> |
| [create](arkts-arkui-window-create-f.md#create-2) | 创建子窗口，使用Promise异步回调。<br/><br/>子窗口创建后默认是[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃，建议使用[createWindow()](arkts-arkui-window-createwindow-f.md#createWindow-2)替代。<br/> |
| [create](arkts-arkui-window-create-f.md#create-3) | 创建系统窗口，使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 8开始支持，从API version 9开始废弃，建议使用[createWindow()](arkts-arkui-window-createwindow-f.md#createWindow-2)替代。<br/> |
| [create](arkts-arkui-window-create-f.md#create-4) | 创建系统窗口，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 8开始支持，从API version 9开始废弃，建议使用<br/>&gt; [createWindow()](window.createWindow(config: Configuration, callback: AsyncCallback&lt;Window&gt;))替代。<br/> |
| <!--DelRow-->[createSubWindowAndBindParent](arkts-arkui-window-createsubwindowandbindparent-f-sys.md#createSubWindowAndBindParent-1) | 创建一个子窗，并绑定父窗。使用Promise异步回调。<br/><br/>子窗跟随父窗显示/隐藏，但并不跟随父窗销毁，子窗通过回调函数监听父窗生命周期变化。<br/><br/>建议在父窗销毁后主动销毁创建的子窗。<br/> |
| [find](arkts-arkui-window-find-f.md#find-1) | 查找id所对应的窗口，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃，建议使用[findWindow()](arkts-arkui-window-findwindow-f.md#findWindow-1)替代。<br/> |
| [find](arkts-arkui-window-find-f.md#find-2) | 查找id所对应的窗口，使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃，建议使用[findWindow()](arkts-arkui-window-findwindow-f.md#findWindow-1)替代。<br/> |
| [findWindow](arkts-arkui-window-findwindow-f.md#findWindow-1) | 查找指定名称对应的窗口。<br/> |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md#getTopWindow-1) | 获取当前应用内最后显示的窗口，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 6开始支持，从API version 9开始废弃，建议使用<br/>&gt; [getLastWindow()](window.getLastWindow(ctx: BaseContext, callback: AsyncCallback&lt;Window&gt;))替代。<br/> |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md#getTopWindow-2) | 获取当前应用内最后显示的窗口，使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 6开始支持，从API version 9开始废弃，建议使用[getLastWindow()](arkts-arkui-window-getlastwindow-f.md#getLastWindow-2)替代。<br/> |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md#getTopWindow-3) | 获取当前应用内最后显示的窗口，使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 8开始支持，从API version 9开始废弃，建议使用[getLastWindow()](arkts-arkui-window-getlastwindow-f.md#getLastWindow-2)替代。<br/> |
| [getTopWindow](arkts-arkui-window-gettopwindow-f.md#getTopWindow-4) | 获取当前应用内最后显示的窗口，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 8开始支持，从API version 9开始废弃，参数ctx传入null或undefined时，可能会导致callback无法得到执行，建议使用<br/>&gt; [getLastWindow()](window.getLastWindow(ctx: BaseContext, callback: AsyncCallback&lt;Window&gt;))替代。<br/> |
| [getLastWindow](arkts-arkui-window-getlastwindow-f.md#getLastWindow-1) | 获取当前应用内层级最高的子窗口，使用callback异步回调。<br/><br/>若无应用子窗口或子窗口未调用[showWindow()](@ohos.window:window.Window.showWindow(callback: AsyncCallback&lt;void&gt;))进行显示，则返回应用主<br/>窗口。<br/> |
| [getLastWindow](arkts-arkui-window-getlastwindow-f.md#getLastWindow-2) | 获取当前应用内层级最高的子窗口，使用Promise异步回调。<br/><br/>若无应用子窗口或子窗口未调用[showWindow()](@ohos.window:window.Window.showWindow(callback: AsyncCallback&lt;void&gt;))进行显示，则返回应用主<br/>窗口。<br/> |
| <!--DelRow-->[minimizeAll](arkts-arkui-window-minimizeall-f-sys.md#minimizeAll-1) | 最小化指定ID的屏幕中的所有主窗口。<br/> |
| <!--DelRow-->[minimizeAll](arkts-arkui-window-minimizeall-f-sys.md#minimizeAll-2) | 最小化指定ID的屏幕中的所有主窗口，使用Promise异步回调。<br/> |
| <!--DelRow-->[minimizeAllWithExclusion](arkts-arkui-window-minimizeallwithexclusion-f-sys.md#minimizeAllWithExclusion-1) | 最小化指定ID的屏幕中除指定窗口之外的所有主窗口，使用Promise异步回调。<br/> |
| <!--DelRow-->[toggleShownStateForAllAppWindows](arkts-arkui-window-toggleshownstateforallappwindows-f-sys.md#toggleShownStateForAllAppWindows-1) | 多窗口快速切换时隐藏或者恢复应用窗口。<br/> |
| <!--DelRow-->[toggleShownStateForAllAppWindows](arkts-arkui-window-toggleshownstateforallappwindows-f-sys.md#toggleShownStateForAllAppWindows-2) | 多窗口快速切换时隐藏或者恢复应用窗口，使用Promise异步回调。<br/> |
| <!--DelRow-->[setWindowLayoutMode](arkts-arkui-window-setwindowlayoutmode-f-sys.md#setWindowLayoutMode-1) | 设置窗口布局模式，使用callback异步回调。<br/> |
| <!--DelRow-->[setWindowLayoutMode](arkts-arkui-window-setwindowlayoutmode-f-sys.md#setWindowLayoutMode-2) | 设置窗口布局模式，使用Promise异步回调。<br/> |
| <!--DelRow-->[setGestureNavigationEnabled](arkts-arkui-window-setgesturenavigationenabled-f-sys.md#setGestureNavigationEnabled-1) | 设置手势导航启用状态。使用callback异步回调。系统出于安全的考虑，不会干预手势的禁用和恢复。应用调用本接口禁用手势后异常退出的情况下，如果想要恢复手势，需自行实现自动拉起机制并再次调用本接口恢复手势。<br/> |
| <!--DelRow-->[setGestureNavigationEnabled](arkts-arkui-window-setgesturenavigationenabled-f-sys.md#setGestureNavigationEnabled-2) | 设置手势导航启用状态。使用Promise异步回调。系统出于安全的考虑，不会干预手势的禁用和恢复。应用调用本接口禁用手势后异常退出的情况下，如果想要恢复手势，需自行实现自动拉起机制并再次调用本接口恢复手势。<br/> |
| <!--DelRow-->[setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md#setWaterMarkImage-1) | 设置屏幕水印图片显示状态。使用Promise异步回调。<br/> |
| <!--DelRow-->[setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md#setWaterMarkImage-2) | 设置屏幕水印图片的显示状态，并设定水印的优先级。使用Promise异步回调。当priority等于0时，当前接口与<br/>[setWaterMarkImage](window.setWaterMarkImage(pixelMap: image.PixelMap, enable: boolean, callback: AsyncCallback&lt;void&gt;))<br/>等价。<br/> |
| <!--DelRow-->[setWaterMarkImage](arkts-arkui-window-setwatermarkimage-f-sys.md#setWaterMarkImage-3) | 设置屏幕水印图片显示状态。使用callback异步回调。<br/> |
| [shiftAppWindowFocus](arkts-arkui-window-shiftappwindowfocus-f.md#shiftAppWindowFocus-1) | 在同应用内将窗口焦点从源窗口转移到目标窗口，仅支持应用主窗、子窗范围内的焦点转移。使用Promise异步回调。<br/><br/>目标窗口需确保具有获得焦点的能力（可通过<br/>[setWindowFocusable()](@ohos.window:window.Window.setWindowFocusable(isFocusable: boolean, callback: AsyncCallback&lt;void&gt;))<br/>设置），并确保调用[showWindow()](@ohos.window:window.Window.showWindow(callback: AsyncCallback&lt;void&gt;))成功且执行完毕。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 在调用shiftAppWindowFocus()前，建议确保目标窗口已调用<br/>&gt; [loadContent()](@ohos.window:window.Window.loadContent(path: string, storage: LocalStorage, callback: AsyncCallback&lt;void&gt;))<br/>&gt; 或[setUIContent()](@ohos.window:window.Window.setUIContent(path: string, callback: AsyncCallback&lt;void&gt;))并生效，<br/>&gt; 否则可能会导致不可见窗口获取焦点，造成功能异常或影响用户体验。<br/> |
| <!--DelRow-->[setSpecificSystemWindowZIndex](arkts-arkui-window-setspecificsystemwindowzindex-f-sys.md#setSpecificSystemWindowZIndex-1) | 设置系统窗口的窗口层级。使用Promise异步回调。<br/><br/>将所有该类型系统窗口zIndex调整为所设置的值，调整前后，该类型窗口之间相对层级保持不变，焦点窗口不发生变化。当应用关闭之后该类型窗口层级恢复默认值。<br/><br/>推荐不同类型窗口设置不同的zIndex，如果已经存在相同zIndex的窗口，设置前后，窗口之间的相对层级保持不变。<br/> |
| [shiftAppWindowPointerEvent](arkts-arkui-window-shiftappwindowpointerevent-f.md#shiftAppWindowPointerEvent-1) | 主窗口和子窗口可正常调用，用于将鼠标输入事件从源窗口转移到目标窗口。使用Promise异步回调。<br/><br/>源窗口仅在[onTouch](../../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch)事件（事件类型必须为<br/>TouchType.Down）的回调方法中调用此接口才会有鼠标输入事件转移效果，成功调用此接口后，系统会向源窗口补发鼠标按键抬起（TouchType.Up）事件，并且向目标窗口补发鼠标按键按下（TouchType.Down）事件。<br/> |
| [shiftAppWindowTouchEvent](arkts-arkui-window-shiftappwindowtouchevent-f.md#shiftAppWindowTouchEvent-1) | 主窗口和子窗口可正常调用，用于将触屏输入事件从源窗口转移到目标窗口。使用Promise异步回调。<br/><br/>源窗口仅在[onTouch](../../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch)事件（事件类型必须为<br/>TouchType.Down）的回调方法中调用此接口才会有触屏输入事件转移效果，成功调用此接口后，系统会向源窗口补发触屏抬起（TouchType.Up）事件，并且向目标窗口补发触屏按下（TouchType.Down）事件。<br/> |
| <!--DelRow-->[getVisibleWindowInfo](arkts-arkui-window-getvisiblewindowinfo-f-sys.md#getVisibleWindowInfo-1) | 获取当前屏幕的可见主窗口（未退至后台的主窗口）信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[getTopNavDestinationName](arkts-arkui-window-gettopnavdestinationname-f-sys.md#getTopNavDestinationName-1) | 获取指定的前台窗口当前栈顶[Navigation](./@internal/component/ets/navigation)中的<br/>[NavDestination](./@internal/component/ets/nav_destination)名称，使用Promise异步回调。<br/> |
| <!--DelRow-->[getSnapshot](arkts-arkui-window-getsnapshot-f-sys.md#getSnapshot-1) | 获取指定窗口相同尺寸截图，使用Promise异步回调。若当前窗口设置为隐私模式（可通过<br/>[setWindowPrivacyMode](@ohos.window:window.Window.setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback&lt;void&gt;))<br/>接口设置），截图结果为白屏。<br/> |
| [getWindowsByCoordinate](arkts-arkui-window-getwindowsbycoordinate-f.md#getWindowsByCoordinate-1) | 查询本应用指定坐标下的可见窗口数组，按当前窗口层级排列，层级最高的窗口对应数组下标为0，使用Promise异步回调。<br/> |
| [getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md#getAllWindowLayoutInfo-1) | 获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。<br/> |
| [getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md#getAllWindowLayoutInfo-2) | 根据option指定的过滤条件获取指定屏幕上可见的窗口布局信息数组，其中返回的每个Rect的宽、高是已经过缩放计算后的值，按当前窗口层级排列，层级最高的对应数组index为0，使用Promise异步回调。当未传入option或其中<br/>的字段都为默认值时，当前接口与[getAllWindowLayoutInfo](arkts-arkui-window-getallwindowlayoutinfo-f.md#getAllWindowLayoutInfo-1)等价。<br/> |
| [getGlobalWindowMode](arkts-arkui-window-getglobalwindowmode-f.md#getGlobalWindowMode-1) | 获取指定屏幕上生命周期位于前台的窗口对应的窗口模式，使用Promise异步回调。<br/> |
| <!--DelRow-->[on](arkts-arkui-window-on-f-sys.md#on-1) | 开启状态栏、导航栏属性变化的监听。<br/> |
| <!--DelRow-->[off](arkts-arkui-window-off-f-sys.md#off-1) | 关闭状态栏、导航栏属性变化的监听。<br/> |
| <!--DelRow-->[on](arkts-arkui-window-on-f-sys.md#on-2) | 添加手势导航启用状态变化的监听。<br/> |
| <!--DelRow-->[off](arkts-arkui-window-off-f-sys.md#off-2) | 移除手势导航启用状态变化的监听。<br/> |
| <!--DelRow-->[on](arkts-arkui-window-on-f-sys.md#on-3) | 添加水印启用状态变化的监听。<br/> |
| <!--DelRow-->[off](arkts-arkui-window-off-f-sys.md#off-3) | 移除水印启用状态变化的监听。<br/> |
| [onApplicationFocusStateChange](arkts-arkui-window-onapplicationfocusstatechange-f.md#onApplicationFocusStateChange-1) | 开启应用进程获焦状态变化的监听。此监听针对应用间的获焦状态变化，若同应用内窗口间的获焦状态发生变化，则不会触发回调函数。<br/> |
| [offApplicationFocusStateChange](arkts-arkui-window-offapplicationfocusstatechange-f.md#offApplicationFocusStateChange-1) | 关闭应用进程获焦状态变化的监听。<br/> |
| [setStartWindowBackgroundColor](arkts-arkui-window-setstartwindowbackgroundcolor-f.md#setStartWindowBackgroundColor-1) | 设置同一应用包名下指定moduleName、abilityName对应UIAbility的启动页背景色，使用Promise异步回调。<br/><br/>该接口对同一应用包名下的所有进程生效，例如多实例或应用分身场景。<br/> |
| <!--DelRow-->[notifyScreenshotEvent](arkts-arkui-window-notifyscreenshotevent-f-sys.md#notifyScreenshotEvent-1) | 通知屏幕截屏的事件类型，使用Promise异步回调。<br/> |
| [setWatermarkImageForAppWindows](arkts-arkui-window-setwatermarkimageforappwindows-f.md#setWatermarkImageForAppWindows-1) | 设置或取消本应用进程下窗口的水印图片，使用Promise异步回调。该接口需要在<br/>[loadContent()](@ohos.window:window.Window.loadContent(path: string, storage: LocalStorage, callback: AsyncCallback&lt;void&gt;))<br/>或[setUIContent()](@ohos.window:window.Window.setUIContent(path: string, callback: AsyncCallback&lt;void&gt;))调用生效后使<br/>用。<br/> |
| [getAllMainWindowInfo](arkts-arkui-window-getallmainwindowinfo-f.md#getAllMainWindowInfo-1) | 获取全部主窗口信息，使用Promise异步回调。<br/> |
| [getMainWindowSnapshot](arkts-arkui-window-getmainwindowsnapshot-f.md#getMainWindowSnapshot-1) | 获取一个或多个指定windowId的主窗口截图，使用Promise异步回调。<br/> |
| <!--DelRow-->[moveMainWindowToTargetDisplay](arkts-arkui-window-movemainwindowtotargetdisplay-f-sys.md#moveMainWindowToTargetDisplay-1) | 将指定的主窗口迁移到指定的屏幕上。使用Promise异步回调。<br/><br/>- 对于[主屏](../../../../displaymanager/display-terminology.md#主屏)/<br/>[扩展屏](../../../../displaymanager/display-terminology.md#扩展屏)与<br/>[虚拟屏](../../../../displaymanager/display-terminology.md#虚拟屏)之间以及虚拟屏与虚拟屏之间的窗口迁移，仅主窗及其子窗会一起被迁移到对应屏幕上且被抬升，如果存在子窗，最上层可获焦子<br/>窗会获取焦点，否则主窗口获焦。<br/>- 对于主屏与扩展屏之间的窗口迁移，只会将主窗口迁移到对应屏幕，抬升并获取焦点。<br/><br/>&lt;!--RP3--&gt;&lt;!--RP3End--&gt;<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[SystemBarProperties](arkts-arkui-window-systembarproperties-i.md) | 状态栏&lt;!--Del--&gt;、三键导航栏的&lt;!--DelEnd--&gt;属性。<br/> |
| [StatusBarProperty](arkts-arkui-window-statusbarproperty-i.md) | 状态栏的属性。在获取状态栏属性信息时返回。<br/> |
| <!--DelRow-->[SystemBarStyle](arkts-arkui-window-systembarstyle-i.md) | 状态栏的属性。在设置页面级状态栏属性时使用。<br/> |
| <!--DelRow-->[SystemBarRegionTint](arkts-arkui-window-systembarregiontint-i-sys.md) | 单个导航栏或状态栏回调信息。<br/> |
| <!--DelRow-->[SystemBarTintState](arkts-arkui-window-systembartintstate-i-sys.md) | 当前系统栏回调信息集合。<br/> |
| [FrameMetrics](arkts-arkui-window-framemetrics-i.md) | 帧率指标。<br/> |
| [Rect](arkts-arkui-window-rect-i.md) | 窗口矩形区域。<br/> |
| [RectInVP](arkts-arkui-window-rectinvp-i.md) | 窗口矩形区域，单位为vp。<br/> |
| [Position](arkts-arkui-window-position-i.md) | 窗口或组件的位置。<br/> |
| <!--DelRow-->[WindowAnchorInfo](arkts-arkui-window-windowanchorinfo-i-sys.md) | 一级子窗与主窗保持相对位置的窗口锚点参数信息。<br/> |
| <!--DelRow-->[SubWindowAttachOptions](arkts-arkui-window-subwindowattachoptions-i-sys.md) | 子窗与主窗保持相对位置不变时的参数。<br/> |
| [AvoidArea](arkts-arkui-window-avoidarea-i.md) | 窗口内容的避让区域。<br/><br/>窗口内容做[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)适配时，需要按照<br/>[AvoidAreaType](arkts-arkui-window-avoidareatype-e.md#AvoidAreaType)对应的AvoidArea做窗口内容避让。<br/><br/>在避让区域内，应用窗口内容被遮挡且无法响应用户点击事件。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 示意图展示了leftRect、topRect、rightRect、bottomRect的含义。<br/>&gt;<br/>&gt; ![avoidArea](../../../../reference/apis-arkui/figures/avoidArea.png)<br/> |
| [UIEnvAvoidAreaVP](arkts-arkui-window-uienvavoidareavp-i.md) | 以vp为单位表示的窗口避让区域信息，在进行[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)适配时需关注。<br/> |
| [Size](arkts-arkui-window-size-i.md) | 窗口大小，单位为px。<br/> |
| [SizeInVP](arkts-arkui-window-sizeinvp-i.md) | 窗口大小，单位为vp。<br/> |
| [WindowInfo](arkts-arkui-window-windowinfo-i.md) | 当前窗口的详细信息。<br/> |
| <!--DelRow-->[WindowInfo](arkts-arkui-window-windowinfo-i-sys.md) | 当前窗口的详细信息。<br/> |
| [WindowDensityInfo](arkts-arkui-window-windowdensityinfo-i.md) | 窗口所在显示设备和窗口自定义的显示密度信息，是与像素单位无关的缩放系数，即显示大小缩放系数。<br/> |
| [WindowProperties](arkts-arkui-window-windowproperties-i.md) | 窗口属性。<br/> |
| [DecorButtonStyle](arkts-arkui-window-decorbuttonstyle-i.md) | 系统装饰栏按钮样式。<br/> |
| <!--DelRow-->[ScaleOptions](arkts-arkui-window-scaleoptions-i-sys.md) | 缩放参数。<br/> |
| <!--DelRow-->[RotateOptions](arkts-arkui-window-rotateoptions-i-sys.md) | 旋转参数。<br/> |
| <!--DelRow-->[TranslateOptions](arkts-arkui-window-translateoptions-i-sys.md) | 平移参数。<br/> |
| <!--DelRow-->[TransitionContext](arkts-arkui-window-transitioncontext-i-sys.md) | 属性转换的上下文信息。<br/> |
| <!--DelRow-->[TransitionController](arkts-arkui-window-transitioncontroller-i-sys.md) | 属性转换控制器。使用其子接口之前得先创建系统窗口，参照示例代码。<br/> |
| [Configuration](arkts-arkui-window-configuration-i.md) | 创建子窗口或系统窗口时的参数。<br/> |
| <!--DelRow-->[Configuration](arkts-arkui-window-configuration-i-sys.md) | 创建子窗口或系统窗口时的参数。<br/> |
| [WindowLimits](arkts-arkui-window-windowlimits-i.md) | 窗口尺寸限制参数，应用可以通过[getWindowLimits](arkts-arkui-window-window-i.md#getWindowLimits-1)获得当前窗口的尺寸限制（单位为px）；从API version 2<br/>2开始，还可以通过[getWindowLimitsVP](arkts-arkui-window-window-i.md#getWindowLimitsVP-1)获取窗口尺寸限制（单位为vp）。<br/><br/>窗口尺寸限制的最终生效结果由默认系统限制、应用配置和运行时设置的数据取交集得到，优先级从高到低依次为：<br/><br/>1. 应用通过[setWindowLimits](arkts-arkui-window-window-i.md#setWindowLimits-1)设置窗口尺寸限制。<br/>2. 应用在[startAbility](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#startAbility-3)拉起窗口时通过[StartOptions](@ohos.app.ability.StartOptions:StartOptions)指定窗口尺寸限制（API version 17开始支持）。<br/>3. 应用在[module.json5配置文件中的abilities标签](../../../../quick-start/module-configuration-file.md#abilities标签)中配置windowLimits。<br/>4. 默认系统限制（基于不同产品和窗口类型，其windowLimits系统默认限制存在差异）。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 针对maxWidth、maxHeight、minWidth、minHeight属性：<br/>&gt;<br/>&gt; - 默认单位为px，从API version 22开始支持通过pixelUnit设置单位为px或vp。<br/>&gt;<br/>&gt; - 参数为整数，浮点数会向下取整。<br/>&gt;<br/>&gt; - 默认值为0，表示属性不发生变化。<br/>&gt;<br/>&gt; - 可生效范围下限值：系统限定的最小高度/宽度。<br/>&gt;<br/>&gt; - 可生效范围上限值：系统限定的最大高度/宽度。<br/> |
| [TitleButtonRect](arkts-arkui-window-titlebuttonrect-i.md) | 标题栏上的最小化、最大化、关闭按钮矩形区域，该区域位置坐标相对窗口右上角。<br/> |
| [RectChangeOptions](arkts-arkui-window-rectchangeoptions-i.md) | 窗口矩形（窗口位置及窗口大小）变化返回的值及变化原因。<br/> |
| [AvoidAreaOptions](arkts-arkui-window-avoidareaoptions-i.md) | 系统避让区变化后返回当前避让区域以及避让区域类型。<br/> |
| [UIEnvWindowAvoidAreaInfoPX](arkts-arkui-window-uienvwindowavoidareainfopx-i.md) | 窗口不同类型避让区域信息组成的[环境变量](../../../../ui/arkts-env-system-property.md)数据类型，每种类型避让区域单位为px。<br/> |
| [UIEnvWindowAvoidAreaInfoVP](arkts-arkui-window-uienvwindowavoidareainfovp-i.md) | 窗口不同类型避让区域信息组成的[环境变量](../../../../ui/arkts-env-system-property.md)数据类型，每种类型避让区域单位为vp。<br/> |
| [MainWindowInfo](arkts-arkui-window-mainwindowinfo-i.md) | 主窗口信息。<br/> |
| [WindowSnapshotConfiguration](arkts-arkui-window-windowsnapshotconfiguration-i.md) | 主窗口截图的配置项。<br/> |
| [OrientationResult](arkts-arkui-window-orientationresult-i.md) | 设置窗口显示方向的执行结果。<br/> |
| [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md) | 窗口旋转变化时的窗口信息。<br/> |
| [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) | 应用在窗口旋转变化时返回的信息，系统会根据此信息改变当前窗口矩形区域大小。当返回主窗口旋转变化的信息时，系统不改变主窗口的大小。<br/><br/>应用窗口与系统窗口大小存在限制，具体限制与相关规则可见<br/>[resize](@ohos.window:window.Window.resize(width: int, height: int, callback: AsyncCallback&lt;void&gt;))。<br/> |
| [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md) | 窗口动画参数配置。<br/> |
| [TransitionAnimation](arkts-arkui-window-transitionanimation-i.md) | 窗口转场动画配置。<br/> |
| [MaximizeOptions](arkts-arkui-window-maximizeoptions-i.md) | 最大化窗口时的可选配置。<br/> |
| [MoveConfiguration](arkts-arkui-window-moveconfiguration-i.md) | 窗口移动选项。<br/> |
| <!--DelRow-->[StartAnimationSystemParams](arkts-arkui-window-startanimationsystemparams-i-sys.md) | 启动动画配置，仅对全屏应用生效。<br/><br/>不同应用间跳转场景不生效，仍保持系统默认动效。<br/> |
| [StartAnimationParams](arkts-arkui-window-startanimationparams-i.md) | 启动动画配置。<br/><br/>仅对同应用的不同ability间跳转生效。<br/><br/>仅对全屏应用生效。<br/> |
| [WindowCreateParams](arkts-arkui-window-windowcreateparams-i.md) | 应用启动时的窗口参数配置。<br/> |
| <!--DelRow-->[WindowCreateParams](arkts-arkui-window-windowcreateparams-i-sys.md) | 应用启动时的窗口参数配置。<br/> |
| [WindowSnapshotAnimationConfig](arkts-arkui-window-windowsnapshotanimationconfig-i.md) | 窗口截图动效的配置。<br/> |
| [KeyboardInfo](arkts-arkui-window-keyboardinfo-i.md) | 软键盘窗口信息。<br/> |
| [KeyFramePolicy](arkts-arkui-window-keyframepolicy-i.md) | 关键帧的策略配置。<br/> |
| [Window](arkts-arkui-window-window-i.md) | 当前窗口实例，窗口管理器管理的基本单元。<br/><br/>下列API示例中都需先使用<br/>[getLastWindow()](@ohos.window:window.getLastWindow(ctx: BaseContext, callback: AsyncCallback&lt;Window&gt;))、<br/>[createWindow()](@ohos.window:window.createWindow(config: Configuration, callback: AsyncCallback&lt;Window&gt;))、<br/>[findWindow()](arkts-arkui-window-findwindow-f.md#findWindow-1)中的任一方法获取到Window实例（windowClass），再通过此实例调用对应方法。<br/> |
| <!--DelRow-->[Window](arkts-arkui-window-window-i-sys.md) | 当前窗口实例，窗口管理器管理的基本单元。<br/><br/>下列API示例中都需先使用<br/>[getLastWindow()](@ohos.window:window.getLastWindow(ctx: BaseContext, callback: AsyncCallback&lt;Window&gt;))、<br/>[createWindow()](@ohos.window:window.createWindow(config: Configuration, callback: AsyncCallback&lt;Window&gt;))、<br/>[findWindow()](arkts-arkui-window-findwindow-f.md#findWindow-1)中的任一方法获取到Window实例（windowClass），再通过此实例调用对应方法。<br/> |
| [ShowWindowOptions](arkts-arkui-window-showwindowoptions-i.md) | 显示子窗口或系统窗口时的参数。<br/> |
| [SubWindowOptions](arkts-arkui-window-subwindowoptions-i.md) | 子窗口创建参数。<br/> |
| <!--DelRow-->[SubWindowOptions](arkts-arkui-window-subwindowoptions-i-sys.md) | 子窗口创建参数。<br/> |
| [WindowStage](arkts-arkui-window-windowstage-i.md) | 窗口管理器。管理各个基本窗口单元，即[Window](arkts-window.md)实例。<br/><br/>下列API示例中都需在[onWindowStageCreate()](../../apis-ability-kit/arkts-apis/arkts-ability-uiability-c.md#onWindowStageCreate-1)函数中使用WindowStage<br/>的实例调用对应方法。<br/> |
| <!--DelRow-->[WindowStage](arkts-arkui-window-windowstage-i-sys.md) | 窗口管理器。管理各个基本窗口单元，即[Window](arkts-window.md)实例。<br/><br/>下列API示例中都需在[onWindowStageCreate()](../../apis-ability-kit/arkts-apis/arkts-ability-uiability-c.md#onWindowStageCreate-1)函数中使用WindowStage<br/>的实例调用对应方法。<br/> |
| <!--DelRow-->[SystemWindowOptions](arkts-arkui-window-systemwindowoptions-i-sys.md) | 系统窗口的创建参数。<br/> |
| <!--DelRow-->[ExtensionWindowConfig](arkts-arkui-window-extensionwindowconfig-i-sys.md) | 创建扩展窗口时需要配置的参数。<br/> |
| [WindowLayoutInfo](arkts-arkui-window-windowlayoutinfo-i.md) | 窗口布局信息。<br/> |
| [WindowInfoOptions](arkts-arkui-window-windowinfooptions-i.md) | 窗口布局信息过滤选项。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WindowType](arkts-arkui-window-windowtype-e.md) | 窗口类型枚举。<br/> |
| <!--DelRow-->[WindowType](arkts-arkui-window-windowtype-e-sys.md) | 窗口类型枚举。<br/> |
| [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) | 窗口内容的避让区域的类型枚举。<br/><br/>窗口内容做[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)适配时，需要按照AvoidAreaType对应的<br/>[AvoidArea](arkts-arkui-window-avoidarea-i.md#AvoidArea)做窗口内容避让。<br/><br/>&lt;!--RP13--&gt;<br/><br/>&lt;!--RP13End--&gt;<br/> |
| <!--DelRow-->[WindowMode](arkts-arkui-window-windowmode-e-sys.md) | 窗口模式枚举。<br/> |
| [SplitRatioPreference](arkts-arkui-window-splitratiopreference-e.md) | 描述分屏窗口分屏比例<br/> |
| <!--DelRow-->[WindowLayoutMode](arkts-arkui-window-windowlayoutmode-e-sys.md) | 窗口布局模式枚举。<br/> |
| [WindowStatusType](arkts-arkui-window-windowstatustype-e.md) | 窗口模式枚举。<br/> |
| [PixelUnit](arkts-arkui-window-pixelunit-e.md) | 像素单位枚举。<br/><br/>物理像素单位和虚拟像素单位换算可使用[px2vp](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#px2vp12)和<br/>[vp2px](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#vp2px12)。<br/> |
| [WindowAnimationCurve](arkts-arkui-window-windowanimationcurve-e.md) | 窗口动画曲线类型。<br/> |
| [WindowTransitionType](arkts-arkui-window-windowtransitiontype-e.md) | 窗口转场动画类型枚举。<br/> |
| [AnimationType](arkts-arkui-window-animationtype-e.md) | 窗口动画类型枚举。<br/> |
| <!--DelRow-->[AnimationType](arkts-arkui-window-animationtype-e-sys.md) | 窗口动画类型枚举。<br/> |
| [WindowAnchor](arkts-arkui-window-windowanchor-e.md) | 窗口锚点枚举。<br/> |
| [ColorSpace](arkts-arkui-window-colorspace-e.md) | 色域模式。<br/> |
| [RectChangeReason](arkts-arkui-window-rectchangereason-e.md) | 窗口矩形（窗口位置及窗口大小）变化的原因。<br/> |
| [OcclusionState](arkts-arkui-window-occlusionstate-e.md) | 窗口可见性状态枚举。<br/> |
| [Orientation](arkts-arkui-window-orientation-e.md) | 窗口显示方向类型枚举。&lt;!--Del--&gt;不同枚举值之间的区别可查询<br/>[窗口Orientation枚举值8\~10或12和枚举值13\~16的区别(API9)](../../../../faqs/faqs-window-manager.md#窗口orientation枚举值810或12和枚举值1316的区别api9)<br/>。&lt;!--DelEnd--&gt;<br/> |
| [OrientationExecutionResult](arkts-arkui-window-orientationexecutionresult-e.md) | 窗口显示方向的执行结果枚举。<br/> |
| [RotationChangeType](arkts-arkui-window-rotationchangetype-e.md) | 窗口旋转事件类型。<br/> |
| [RectType](arkts-arkui-window-recttype-e.md) | 窗口矩形区域坐标系类型。<br/> |
| [ScreenshotEventType](arkts-arkui-window-screenshoteventtype-e.md) | 截屏事件类型枚举。<br/> |
| [RotationInfoType](arkts-arkui-window-rotationinfotype-e.md) | 旋转信息类型枚举。<br/> |
| <!--DelRow-->[BlurStyle](arkts-arkui-window-blurstyle-e-sys.md) | 窗口模糊类型枚举。<br/> |
| [WindowEventType](arkts-arkui-window-windoweventtype-e.md) | 窗口生命周期。<br/> |
| [MaximizePresentation](arkts-arkui-window-maximizepresentation-e.md) | 窗口最大化时的布局枚举。<br/> |
| [AcrossDisplayPresentation](arkts-arkui-window-acrossdisplaypresentation-e.md) | 在可折叠的2in1设备的半折叠状态下，最大化窗口时用于控制瀑布流模式切换策略的枚举。<br/> |
| [GlobalWindowMode](arkts-arkui-window-globalwindowmode-e.md) | 窗口模式。<br/> |
| [WindowStageEventType](arkts-arkui-window-windowstageeventtype-e.md) | WindowStage生命周期状态枚举。<br/> |
| [WindowStageLifecycleEventType](arkts-arkui-window-windowstagelifecycleeventtype-e.md) | WindowStage生命周期的状态类型枚举。<br/> |
| [ModalityType](arkts-arkui-window-modalitytype-e.md) | 子窗口模态类型枚举。<br/> |
| <!--DelRow-->[ExtensionWindowAttribute](arkts-arkui-window-extensionwindowattribute-e-sys.md) | 扩展窗口的属性枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RotationChangeCallback](arkts-arkui-window-rotationchangecallback-t.md) | 旋转事件通知通用回调函数。<br/><br/>开发者在使用时，回调函数参数类型为[RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md#RotationChangeInfo)，返回值类型为<br/>[RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md#RotationChangeResult) \\| void。<br/> |
| [SpecificSystemBar](arkts-arkui-window-specificsystembar-t.md) | 当前支持显示或隐藏的系统栏类型。<br/> |

