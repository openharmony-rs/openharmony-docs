# @ohos.arkui.observer

UIObserver提供了UI组件行为变化的无感监听能力，支持监听Navigation页面状态变化（NavDestination）、滚动事件、路由页面状态、屏幕像素密度变化、绘制指令下发、布局完成、页面切换等多种UI组件行为。 开发者可以通过该模块实现对UI组件状态的实时感知和追踪，适用于需要监控页面生命周期、处理滚动事件、优化渲染性能等场景，帮助开发者更好地理解和管理UI组件的行为变化。无感监听是指在组件状态变化时， 系统自动触发回调函数通知开发者，无需开发者手动轮询或主动查询组件状态。监听器通过注册回调函数实现，当目标组件状态改变时，系统内部的事件分发机制会调用已注册的回调函数，携带状态变化信息。 > **说明：** > - 以下API需先使用UIContext中的[getUIObserver](arkts-arkui-arkui-uicontext-uicontext-c.md#getUIObserver)方法获取到UIObserver对象，再通过该对象调用对应方法。 > - UIObserver仅能监听到本进程内的UI组件状态变化信息， > - 不支持获取&lt;!--Del--&gt;UIExtensionComponent等&lt;!--DelEnd--&gt;跨进程场景的信息。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace uiObserver--><!--Device-unnamed-declare namespace uiObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off_densityUpdate](arkts-arkui-uiobserver-offdensityupdate-f.md#off_densityUpdate) | 取消监听屏幕像素密度的变化。 |
| [off_didLayout](arkts-arkui-uiobserver-offdidlayout-f.md#off_didLayout) | 取消监听每一帧布局完成情况。 |
| [off_navDestinationSwitch](arkts-arkui-uiobserver-offnavdestinationswitch-f.md#off_navDestinationSwitch) | 取消监听Navigation的页面切换事件。 |
| [off_navDestinationSwitch](arkts-arkui-uiobserver-offnavdestinationswitch-f.md#off_navDestinationSwitch) | 取消监听Navigation的页面切换事件。与[uiObserver.off](arkts-arkui-uiobserver-offnavdestinationupdate-f.md#off_navDestinationUpdate)相比，新增了observerOptions参数，即支持设置监听选项。 |
| [off_navDestinationUpdate](arkts-arkui-uiobserver-offnavdestinationupdate-f.md#off_navDestinationUpdate) | 取消监听NavDestination组件的状态变化。与[uiObserver.off](arkts-arkui-uiobserver-offnavdestinationupdate-f.md#off_navDestinationUpdate)相比，新增了options参数，即支持指定监听的Navigation的id。 |
| [off_navDestinationUpdate](arkts-arkui-uiobserver-offnavdestinationupdate-f.md#off_navDestinationUpdate) | 取消监听NavDestination组件的状态变化。 |
| [off_routerPageUpdate](arkts-arkui-uiobserver-offrouterpageupdate-f.md#off_routerPageUpdate) | 取消监听router中page页面的状态变化。 |
| [off_scrollEvent](arkts-arkui-uiobserver-offscrollevent-f.md#off_scrollEvent) | Removes a callback function that was previously registered with `on()`. |
| [off_scrollEvent](arkts-arkui-uiobserver-offscrollevent-f.md#off_scrollEvent) | Removes a callback function that was previously registered with `on()`. |
| [off_tabContentUpdate](arkts-arkui-uiobserver-offtabcontentupdate-f.md#off_tabContentUpdate) | 取消监听指定Tabs组件id的TabContent页面切换事件。 |
| [off_tabContentUpdate](arkts-arkui-uiobserver-offtabcontentupdate-f.md#off_tabContentUpdate) | 取消监听TabContent页面的切换事件。 |
| [off_willDraw](arkts-arkui-uiobserver-offwilldraw-f.md#off_willDraw) | 取消监听每一帧绘制指令下发情况。 |
| [on_densityUpdate](arkts-arkui-uiobserver-ondensityupdate-f.md#on_densityUpdate) | 监听屏幕像素密度变化。 |
| [on_didLayout](arkts-arkui-uiobserver-ondidlayout-f.md#on_didLayout) | 监听每一帧布局完成情况。 |
| [on_navDestinationSwitch](arkts-arkui-uiobserver-onnavdestinationswitch-f.md#on_navDestinationSwitch) | 监听Navigation的页面切换事件。 |
| [on_navDestinationSwitch](arkts-arkui-uiobserver-onnavdestinationswitch-f.md#on_navDestinationSwitch) | 监听Navigation的页面切换事件。与[uiObserver.on](arkts-arkui-uiobserver-onnavdestinationupdate-f.md#on_navDestinationUpdate)相比，新增了observerOptions参数，即支持设置监听选项。 |
| [on_navDestinationUpdate](arkts-arkui-uiobserver-onnavdestinationupdate-f.md#on_navDestinationUpdate) | 监听NavDestination组件的状态变化。与 * [uiObserver.on](arkts-arkui-uiobserver-onnavdestinationupdate-f.md#on_navDestinationUpdate)相比，新增了options参数，即支持指定监听的Navigation的id。 |
| [on_navDestinationUpdate](arkts-arkui-uiobserver-onnavdestinationupdate-f.md#on_navDestinationUpdate) | 监听NavDestination组件的状态变化。 |
| [on_routerPageUpdate](arkts-arkui-uiobserver-onrouterpageupdate-f.md#on_routerPageUpdate) | 监听router中page页面的状态变化。 |
| [on_scrollEvent](arkts-arkui-uiobserver-onscrollevent-f.md#on_scrollEvent) | Registers a callback function to be called when the scroll event start or stop. |
| [on_scrollEvent](arkts-arkui-uiobserver-onscrollevent-f.md#on_scrollEvent) | Registers a callback function to be called when the scroll event start or stop. |
| [on_tabContentUpdate](arkts-arkui-uiobserver-ontabcontentupdate-f.md#on_tabContentUpdate) | 监听指定Tabs组件id的TabContent页面切换事件。相比[on('tabChange')](arkts-arkui-arkui-uicontext-uiobserver-c.md#on_navDestinationUpdate)，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。 |
| [on_tabContentUpdate](arkts-arkui-uiobserver-ontabcontentupdate-f.md#on_tabContentUpdate) | 监听TabContent页面的切换事件。相比[on('tabChange')](arkts-arkui-arkui-uicontext-uiobserver-c.md#on_navDestinationUpdate)，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。 |
| [on_willDraw](arkts-arkui-uiobserver-onwilldraw-f.md#on_willDraw) | 监听每一帧绘制指令下发情况。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md) | 屏幕像素密度变化回调包含的信息。 |
| [RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md) | RouterPageInfo包含的信息，由系统返回给开发者。 |
| [WindowSizeLayoutBreakpointInfo](arkts-arkui-uiobserver-windowsizelayoutbreakpointinfo-c.md) | 窗口尺寸布局断点变化回调的信息。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md) | NavDestination组件信息，由系统返回给开发者。 |
| [NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md) | Navigation组件页面切换的信息。 |
| [NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | Navigation组件页面切换事件的监听选项。 |
| [NavigationInfo](arkts-arkui-uiobserver-navigationinfo-i.md) | Navigation组件信息。 |
| [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Observer选项。 |
| [ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md) | ScrollEvent info. |
| [TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md) | TabContent页面的切换信息。 |
| [TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md) | Text change event info |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NavDestinationState](arkts-arkui-uiobserver-navdestinationstate-e.md) | NavDestination组件状态。 |
| [RouterPageState](arkts-arkui-uiobserver-routerpagestate-e.md) | routerPage生命周期触发时对应的状态。RouterPageState用于[RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md#RouterPageInfo)中，作为 [routerPageUpdate](arkts-arkui-uiobserver-onnavdestinationupdate-f.md#on_navDestinationUpdate)无感监听的返回值。 |
| [ScrollEventType](arkts-arkui-uiobserver-scrolleventtype-e.md) | ScrollEvent type. |
| [TabContentState](arkts-arkui-uiobserver-tabcontentstate-e.md) | TabContent组件的状态。 |

