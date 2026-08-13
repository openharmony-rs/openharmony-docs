# @ohos.arkui.observer

Register callbacks to observe ArkUI behavior.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace uiObserver--><!--Device-unnamed-declare namespace uiObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offDensityUpdate](arkts-na-uiobserver-offdensityupdate-f.md#offDensityUpdate) | Removes a callback function that was previously registered with `on()`. |
| [offDidLayout](arkts-na-uiobserver-offdidlayout-f.md#offDidLayout) | Removes a callback function that was previously registered with `on()`. |
| [offNavDestinationSwitch](arkts-na-uiobserver-offnavdestinationswitch-f.md#offNavDestinationSwitch) | 取消监听Navigation的页面切换事件。 |
| [offNavDestinationSwitch](arkts-na-uiobserver-offnavdestinationswitch-f.md#offNavDestinationSwitch) | 取消监听Navigation的页面切换事件。 |
| [offNavDestinationUpdate](arkts-na-uiobserver-offnavdestinationupdate-f.md#offNavDestinationUpdate) | 取消监听NavDestination组件的状态变化。 |
| [offNavDestinationUpdate](arkts-na-uiobserver-offnavdestinationupdate-f.md#offNavDestinationUpdate) | 取消监听NavDestination组件的状态变化。 |
| [offRouterPageUpdate](arkts-na-uiobserver-offrouterpageupdate-f.md#offRouterPageUpdate) | 取消监听router中page页面的状态变化。 |
| [offScrollEvent](arkts-na-uiobserver-offscrollevent-f.md#offScrollEvent) | Removes a callback function that was previously registered with `onScrollEvent()`. |
| [offScrollEvent](arkts-na-uiobserver-offscrollevent-f.md#offScrollEvent) | Removes a callback function that was previously registered with `onScrollEvent()`. |
| [offTabContentUpdate](arkts-na-uiobserver-offtabcontentupdate-f.md#offTabContentUpdate) | 取消监听TabContent页面的切换事件。 |
| [offTabContentUpdate](arkts-na-uiobserver-offtabcontentupdate-f.md#offTabContentUpdate) | 取消监听TabContent页面的切换事件。 |
| [offWillDraw](arkts-na-uiobserver-offwilldraw-f.md#offWillDraw) | Removes a callback function that was previously registered with `on()`. |
| [onDensityUpdate](arkts-na-uiobserver-ondensityupdate-f.md#onDensityUpdate) | Registers a callback function to be called when the screen density is updated. |
| [onDidLayout](arkts-na-uiobserver-ondidlayout-f.md#onDidLayout) | Registers a callback function to be called when the layout is done. |
| [onNavDestinationSwitch](arkts-na-uiobserver-onnavdestinationswitch-f.md#onNavDestinationSwitch) | 监听Navigation的页面切换事件。 |
| [onNavDestinationSwitch](arkts-na-uiobserver-onnavdestinationswitch-f.md#onNavDestinationSwitch) | 监听Navigation的页面切换事件。 |
| [onNavDestinationUpdate](arkts-na-uiobserver-onnavdestinationupdate-f.md#onNavDestinationUpdate) | 监听NavDestination组件的状态变化。 |
| [onNavDestinationUpdate](arkts-na-uiobserver-onnavdestinationupdate-f.md#onNavDestinationUpdate) | 监听NavDestination组件的状态变化。 |
| [onRouterPageUpdate](arkts-na-uiobserver-onrouterpageupdate-f.md#onRouterPageUpdate) | 监听router中page页面的状态变化。 |
| [onScrollEvent](arkts-na-uiobserver-onscrollevent-f.md#onScrollEvent) | Registers a callback function to be called when the scroll event starts or stops. |
| [onScrollEvent](arkts-na-uiobserver-onscrollevent-f.md#onScrollEvent) | Registers a callback function to be called when the scroll event starts or stops. |
| [onTabContentUpdate](arkts-na-uiobserver-ontabcontentupdate-f.md#onTabContentUpdate) | 监听TabContent页面的切换事件。 |
| [onTabContentUpdate](arkts-na-uiobserver-ontabcontentupdate-f.md#onTabContentUpdate) | 监听TabContent页面的切换事件。 |
| [onWillDraw](arkts-na-uiobserver-onwilldraw-f.md#onWillDraw) | Registers a callback function to be called when the draw command will be drawn. |

### 类

| 名称 | 说明 |
| --- | --- |
| [DensityInfo](arkts-na-uiobserver-densityinfo-c.md) | Density info. |
| [RouterPageInfo](arkts-na-uiobserver-routerpageinfo-c.md) | RouterPageInfo包含的信息。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [NavDestinationInfo](arkts-na-uiobserver-navdestinationinfo-i.md) | NavDestination组件信息。 |
| [NavDestinationSwitchInfo](arkts-na-uiobserver-navdestinationswitchinfo-i.md) | Navigation组件页面切换的信息。 |
| [NavDestinationSwitchObserverOptions](arkts-na-uiobserver-navdestinationswitchobserveroptions-i.md) | Indicates the options of NavDestination switch. |
| [NavigationInfo](arkts-na-uiobserver-navigationinfo-i.md) | Navigation组件信息。 |
| [ObserverOptions](arkts-na-uiobserver-observeroptions-i.md) | observer options. |
| [ScrollEventInfo](arkts-na-uiobserver-scrolleventinfo-i.md) | ScrollEvent info. |
| [TabContentInfo](arkts-na-uiobserver-tabcontentinfo-i.md) | TabContent页面的切换信息。 |
| [TextChangeEventInfo](arkts-na-uiobserver-textchangeeventinfo-i.md) | 文本更改事件信息 |
| [WindowSizeLayoutBreakpointInfo](arkts-na-uiobserver-windowsizelayoutbreakpointinfo-i.md) | 定义窗口大小断点信息。 这个接口定义了当前窗口长宽的断点信息，基于配置好的断点阈值。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NavDestinationState](arkts-na-uiobserver-navdestinationstate-e.md) | NavDestination组件状态。 |
| [RouterPageState](arkts-na-uiobserver-routerpagestate-e.md) | routerPage生命周期触发时对应的状态。 |
| [ScrollEventType](arkts-na-uiobserver-scrolleventtype-e.md) | ScrollEvent type. |
| [TabContentState](arkts-na-uiobserver-tabcontentstate-e.md) | TabContent组件的状态。 |

