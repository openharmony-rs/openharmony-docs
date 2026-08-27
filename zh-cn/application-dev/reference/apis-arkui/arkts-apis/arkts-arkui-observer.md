# @ohos.arkui.observer

UIObserver提供了UI组件行为变化的无感监听能力，支持监听Navigation页面状态变化（NavDestination）、滚动事件、路由页面状态、屏幕像素密度变化、绘制指令下发、布局完成、页面切换等多种UI组件行为。 开发者可以通过该模块实现对UI组件状态的实时感知和追踪，适用于需要监控页面生命周期、处理滚动事件、优化渲染性能等场景，帮助开发者更好地理解和管理UI组件的行为变化。无感监听是指在组件状态变化时， 系统自动触发回调函数通知开发者，无需开发者手动轮询或主动查询组件状态。监听器通过注册回调函数实现，当目标组件状态改变时，系统内部的事件分发机制会调用已注册的回调函数，携带状态变化信息。

> **说明：**

> - 以下API需先使用UIContext中的[getUIObserver](arkts-arkui-arkui-uicontext-uicontext-c.md#getuiobserver)方法获取到UIObserver对象，再通过该对象调用对应方法。

> - UIObserver仅能监听到本进程内的UI组件状态变化信息，
> - 不支持获取<!--Del-->UIExtensionComponent等<!--DelEnd-->跨进程场景的信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationupdate) | 取消监听NavDestination组件的状态变化。与uiObserver.off相比，新增了options参数，即支持指定监听的Navigation的id。 |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationupdate) | 取消监听NavDestination组件的状态变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#offscrollevent) | Removes a callback function that was previously registered with `on()`. |
| [off](arkts-arkui-uiobserver-off-f.md#offscrollevent) | Removes a callback function that was previously registered with `on()`. |
| [off](arkts-arkui-uiobserver-off-f.md#offrouterpageupdate) | 取消监听router中page页面的状态变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#offdensityupdate) | 取消监听屏幕像素密度的变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#offwilldraw) | 取消监听每一帧绘制指令下发情况。 |
| [off](arkts-arkui-uiobserver-off-f.md#offdidlayout) | 取消监听每一帧布局完成情况。 |
| [off](arkts-arkui-uiobserver-off-f.md#offtabcontentupdate) | 取消监听指定Tabs组件id的TabContent页面切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#offtabcontentupdate) | 取消监听TabContent页面的切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationswitch) | 取消监听Navigation的页面切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationswitch) | 取消监听Navigation的页面切换事件。与uiObserver.off相比，新增了observerOptions参数，即支持设置监听选项。 |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationupdate) | 监听NavDestination组件的状态变化。与  * uiObserver.on相比，新增了options参数，即支持指定监听的Navigation的id。 |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationupdate) | 监听NavDestination组件的状态变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#onscrollevent) | Registers a callback function to be called when the scroll event start or stop. |
| [on](arkts-arkui-uiobserver-on-f.md#onscrollevent) | Registers a callback function to be called when the scroll event start or stop. |
| [on](arkts-arkui-uiobserver-on-f.md#onrouterpageupdate) | 监听router中page页面的状态变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#ondensityupdate) | 监听屏幕像素密度变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#onwilldraw) | 监听每一帧绘制指令下发情况。 |
| [on](arkts-arkui-uiobserver-on-f.md#ondidlayout) | 监听每一帧布局完成情况。 |
| [on](arkts-arkui-uiobserver-on-f.md#ontabcontentupdate) | 监听指定Tabs组件id的TabContent页面切换事件。相比on('tabChange')，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。 |
| [on](arkts-arkui-uiobserver-on-f.md#ontabcontentupdate) | 监听TabContent页面的切换事件。相比on('tabChange')，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。 |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationswitch) | 监听Navigation的页面切换事件。 |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationswitch) | 监听Navigation的页面切换事件。与uiObserver.on相比，新增了observerOptions参数，即支持设置监听选项。 |

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
| [ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md) | ScrollEvent info.@interface ScrollEventInfo |
| [TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md) | TabContent页面的切换信息。 |
| [TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md) | Text change event info@interface TextChangeEventInfo |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NavDestinationState](arkts-arkui-uiobserver-navdestinationstate-e.md) | NavDestination组件状态。 |
| [RouterPageState](arkts-arkui-uiobserver-routerpagestate-e.md) | routerPage生命周期触发时对应的状态。RouterPageState用于[RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md)中，作为 routerPageUpdate无感监听的返回值。 |
| [ScrollEventType](arkts-arkui-uiobserver-scrolleventtype-e.md) | ScrollEvent type.@enum { number } |
| [TabContentState](arkts-arkui-uiobserver-tabcontentstate-e.md) | TabContent组件的状态。 |
