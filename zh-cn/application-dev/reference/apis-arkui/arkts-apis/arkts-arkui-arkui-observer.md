# @ohos.arkui.observer(无感监听)

本模块提供UI组件行为变化的无感监听能力，包括监听页面状态、滚动事件、页面路由、屏幕像素密度、布局和绘制、页面切换以及TabContent状态变化等。适用于需要在不侵入组件业务逻辑的情况下感知UI状态变化的场景。推荐使用[UIObserver](arkts-arkui-arkui-uicontext-uicontext-c.md)进行组件监听。

> **说明：** 
> 
> - UIObserver仅能监听到本进程内的相关信息，不支持获取<!--Del-->[UIExtensionComponent](../arkts-components/arkts-arkui-uiextensioncomponent-comp-sys.md#ui_extension_componentsystem-api)等<!--DelEnd-->跨进程场景的信息。

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
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationupdate) | 取消监听NavDestination组件的状态变化。与[uiObserver.off](arkts-arkui-uiobserver-off-f.md#offnavdestinationupdate)相比，新增了options参数，即支持指定监听的Navigation的id。 |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationupdate) | 取消监听NavDestination组件的状态变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#offscrollevent) | 取消监听指定id的滚动组件滚动事件的开始和结束。滚动组件包括[List](../arkts-components/arkts-arkui-list-comp.md#list)、[Grid](../arkts-components/arkts-arkui-grid-comp.md#grid)、[Scroll](../arkts-components/arkts-arkui-scroll-comp.md#scroll)、[WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md#water_flow)、[ArcList](../arkts-components/arkts-arkui-arclist-comp.md#ohosarkuiarclist)。 |
| [off](arkts-arkui-uiobserver-off-f.md#offscrollevent) | 取消监听所有滚动组件滚动事件的开始和结束。滚动组件包括[List](../arkts-components/arkts-arkui-list-comp.md#list)、[Grid](../arkts-components/arkts-arkui-grid-comp.md#grid)、[Scroll](../arkts-components/arkts-arkui-scroll-comp.md#scroll)、[WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md#water_flow)、[ArcList](../arkts-components/arkts-arkui-arclist-comp.md#ohosarkuiarclist)。 |
| [off](arkts-arkui-uiobserver-off-f.md#offrouterpageupdate) | 取消监听router中page页面的状态变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#offdensityupdate) | 取消监听屏幕像素密度的变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#offwilldraw) | 取消监听每一帧绘制指令下发情况。 |
| [off](arkts-arkui-uiobserver-off-f.md#offdidlayout) | 取消监听每一帧布局完成情况。 |
| [off](arkts-arkui-uiobserver-off-f.md#offtabcontentupdate) | 取消监听指定Tabs组件id的TabContent页面切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#offtabcontentupdate) | 取消监听TabContent页面的切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationswitch) | 取消监听Navigation的页面切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationswitch) | 取消监听Navigation的页面切换事件。与uiObserver.off相比，新增了observerOptions参数，即支持设置监听选项。 |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationupdate) | 监听NavDestination组件的状态变化。与[uiObserver.on](arkts-arkui-uiobserver-on-f.md#onnavdestinationupdate)相比，新增了options参数，即支持指定监听的Navigation的id。 |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationupdate) | 监听NavDestination组件的状态变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#onscrollevent) | 监听指定id的滚动组件滚动事件的开始和结束。滚动组件包括[List](../arkts-components/arkts-arkui-list-comp.md#list)、[Grid](../arkts-components/arkts-arkui-grid-comp.md#grid)、[Scroll](../arkts-components/arkts-arkui-scroll-comp.md#scroll)、[WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md#water_flow)、[ArcList](../arkts-components/arkts-arkui-arclist-comp.md#ohosarkuiarclist)。 |
| [on](arkts-arkui-uiobserver-on-f.md#onscrollevent) | 监听所有滚动组件滚动事件的开始和结束。滚动组件包括[List](../arkts-components/arkts-arkui-list-comp.md#list)、[Grid](../arkts-components/arkts-arkui-grid-comp.md#grid)、[Scroll](../arkts-components/arkts-arkui-scroll-comp.md#scroll)、[WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md#water_flow)、[ArcList](../arkts-components/arkts-arkui-arclist-comp.md#ohosarkuiarclist)。 |
| [on](arkts-arkui-uiobserver-on-f.md#onrouterpageupdate) | 监听router中page页面的状态变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#ondensityupdate) | 监听屏幕像素密度变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#onwilldraw) | 监听每一帧绘制指令下发情况。 |
| [on](arkts-arkui-uiobserver-on-f.md#ondidlayout) | 监听每一帧布局完成情况。 |
| [on](arkts-arkui-uiobserver-on-f.md#ontabcontentupdate) | 监听指定Tabs组件id的TabContent页面切换事件。相比[on('tabChange')](../../../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#ontabchange22)，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。 |
| [on](arkts-arkui-uiobserver-on-f.md#ontabcontentupdate) | 监听TabContent页面的切换事件。相比[on('tabChange')](../../../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#ontabchange22)，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。 |
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
| [ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md) | ScrollEvent滚动信息。 |
| [TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md) | TabContent页面的切换信息。 |
| [TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md) | 输入框文本变化的信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NavDestinationState](arkts-arkui-uiobserver-navdestinationstate-e.md) | NavDestination组件状态。 |
| [RouterPageState](arkts-arkui-uiobserver-routerpagestate-e.md) | routerPage生命周期触发时对应的状态。RouterPageState用于[RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md)中，作为routerPageUpdate无感监听的返回值。 |
| [ScrollEventType](arkts-arkui-uiobserver-scrolleventtype-e.md) | 滚动事件的类型。 |
| [TabContentState](arkts-arkui-uiobserver-tabcontentstate-e.md) | TabContent组件的状态。 |
