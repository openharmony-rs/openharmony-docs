# @ohos.arkui.observer

提供UI组件行为变化的无感监听能力。

> **说明：**

> - 以下API需先使用UIContext中的{@link getUIObserver()}方法获取到UIObserver对象，再通过该对象调用对应方法。

> - UIObserver仅能监听到本进程内的相关信息，不支持获取<!--Del-->[UIExtensionComponent](../arkts-components/arkts-arkui-uiextensioncomponent.md)等<!--DelEnd-->跨进程场景的信  
> 息。

**起始版本：** 11

<!--Device-unnamed-declare namespace uiObserver--><!--Device-unnamed-declare namespace uiObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off](arkts-arkui-uiobserver-off-f.md#off) | 取消监听NavDestination组件的状态变化。与[uiObserver.off](uiObserver.off(type: 'navDestinationUpdate', callback?:Callback<NavDestinationInfo>))相比，新增了options参数，即支持指定监听的Navigation的id。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-1) | 取消监听NavDestination组件的状态变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-2) | Removes a callback function that was previously registered with `on()`. |
| [off](arkts-arkui-uiobserver-off-f.md#off-3) | Removes a callback function that was previously registered with `on()`. |
| [off](arkts-arkui-uiobserver-off-f.md#off-4) | 取消监听router中page页面的状态变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-5) | 取消监听屏幕像素密度的变化。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-6) | 取消监听每一帧绘制指令下发情况。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-7) | 取消监听每一帧布局完成情况。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-8) | 取消监听指定Tabs组件id的TabContent页面切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-9) | 取消监听TabContent页面的切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-10) | 取消监听Navigation的页面切换事件。 |
| [off](arkts-arkui-uiobserver-off-f.md#off-11) | 取消监听Navigation的页面切换事件。与[uiObserver.off](uiObserver.off( type: 'navDestinationSwitch', context:UIAbilityContext \| UIContext, callback?: Callback<NavDestinationSwitchInfo> ))相比，新增了observerOptions参数，即支持设置监听选项。 |
| [on](arkts-arkui-uiobserver-on-f.md#on) | 监听NavDestination组件的状态变化。与* [uiObserver.on](uiObserver.on(type: 'navDestinationUpdate', callback:Callback<NavDestinationInfo>))相比，新增了options参数，即支持指定监听的Navigation的id。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-1) | 监听NavDestination组件的状态变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-2) | Registers a callback function to be called when the scroll event start or stop. |
| [on](arkts-arkui-uiobserver-on-f.md#on-3) | Registers a callback function to be called when the scroll event start or stop. |
| [on](arkts-arkui-uiobserver-on-f.md#on-4) | 监听router中page页面的状态变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-5) | 监听屏幕像素密度变化。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-6) | 监听每一帧绘制指令下发情况。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-7) | 监听每一帧布局完成情况。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-8) | 监听指定Tabs组件id的TabContent页面切换事件。相比[on('tabChange')](@ohos.arkui.UIContext:UIObserver#on(type: 'tabChange',callback: Callback<observer.TabContentInfo>))，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-9) | 监听TabContent页面的切换事件。相比[on('tabChange')](@ohos.arkui.UIContext:UIObserver#on(type: 'tabChange', callback:Callback<observer.TabContentInfo>))，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-10) | 监听Navigation的页面切换事件。 |
| [on](arkts-arkui-uiobserver-on-f.md#on-11) | 监听Navigation的页面切换事件。与[uiObserver.on](uiObserver.on( type: 'navDestinationSwitch', context: UIAbilityContext \|UIContext, callback: Callback<NavDestinationSwitchInfo> ))相比，新增了observerOptions参数，即支持设置监听选项。 |

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
| [RouterPageState](arkts-arkui-uiobserver-routerpagestate-e.md) | routerPage生命周期触发时对应的状态。RouterPageState用于[RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md)中，作为[routerPageUpdate](uiObserver.on(type: 'routerPageUpdate', context: UIAbilityContext \| UIContext, callback:Callback<RouterPageInfo>))无感监听的返回值。 |
| [ScrollEventType](arkts-arkui-uiobserver-scrolleventtype-e.md) | ScrollEvent type. |
| [TabContentState](arkts-arkui-uiobserver-tabcontentstate-e.md) | TabContent组件的状态。 |

