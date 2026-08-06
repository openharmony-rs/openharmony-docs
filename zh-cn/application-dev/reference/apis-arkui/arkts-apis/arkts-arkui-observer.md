# @ohos.arkui.observer

Register callbacks to observe ArkUI behavior.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare namespace uiObserver--><!--Device-unnamed-declare namespace uiObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offDensityUpdate](arkts-arkui-uiobserver-offdensityupdate-f.md#offdensityupdate) | Removes a callback function that was previously registered with \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |
| [offDidLayout](arkts-arkui-uiobserver-offdidlayout-f.md#offdidlayout) | Removes a callback function that was previously registered with \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |
| [offNavDestinationSwitch](arkts-arkui-uiobserver-offnavdestinationswitch-f.md#offnavdestinationswitch) | 取消监听Navigation的页面切换事件。 |
| [offNavDestinationSwitch](arkts-arkui-uiobserver-offnavdestinationswitch-f.md#offnavdestinationswitch-1) | 取消监听Navigation的页面切换事件。 |
| [offNavDestinationUpdate](arkts-arkui-uiobserver-offnavdestinationupdate-f.md#offnavdestinationupdate) | 取消监听NavDestination组件的状态变化。 |
| [offNavDestinationUpdate](arkts-arkui-uiobserver-offnavdestinationupdate-f.md#offnavdestinationupdate-1) | 取消监听NavDestination组件的状态变化。 |
| [offRouterPageUpdate](arkts-arkui-uiobserver-offrouterpageupdate-f.md#offrouterpageupdate) | 取消监听router中page页面的状态变化。 |
| [offScrollEvent](arkts-arkui-uiobserver-offscrollevent-f.md#offscrollevent) | Removes a callback function that was previously registered with \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |
| [offScrollEvent](arkts-arkui-uiobserver-offscrollevent-f.md#offscrollevent-1) | Removes a callback function that was previously registered with \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |
| [offTabContentUpdate](arkts-arkui-uiobserver-offtabcontentupdate-f.md#offtabcontentupdate) | 取消监听TabContent页面的切换事件。 |
| [offTabContentUpdate](arkts-arkui-uiobserver-offtabcontentupdate-f.md#offtabcontentupdate-1) | 取消监听TabContent页面的切换事件。 |
| [offWillDraw](arkts-arkui-uiobserver-offwilldraw-f.md#offwilldraw) | Removes a callback function that was previously registered with \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |
| [onDensityUpdate](arkts-arkui-uiobserver-ondensityupdate-f.md#ondensityupdate) | Registers a callback function to be called when the screen density is updated. |
| [onDidLayout](arkts-arkui-uiobserver-ondidlayout-f.md#ondidlayout) | Registers a callback function to be called when the layout is done. |
| [onNavDestinationSwitch](arkts-arkui-uiobserver-onnavdestinationswitch-f.md#onnavdestinationswitch) | 监听Navigation的页面切换事件。 |
| [onNavDestinationSwitch](arkts-arkui-uiobserver-onnavdestinationswitch-f.md#onnavdestinationswitch-1) | 监听Navigation的页面切换事件。 |
| [onNavDestinationUpdate](arkts-arkui-uiobserver-onnavdestinationupdate-f.md#onnavdestinationupdate) | 监听NavDestination组件的状态变化。 |
| [onNavDestinationUpdate](arkts-arkui-uiobserver-onnavdestinationupdate-f.md#onnavdestinationupdate-1) | 监听NavDestination组件的状态变化。 |
| [onRouterPageUpdate](arkts-arkui-uiobserver-onrouterpageupdate-f.md#onrouterpageupdate) | 监听router中page页面的状态变化。 |
| [onScrollEvent](arkts-arkui-uiobserver-onscrollevent-f.md#onscrollevent) | Registers a callback function to be called when the scroll event starts or stops. |
| [onScrollEvent](arkts-arkui-uiobserver-onscrollevent-f.md#onscrollevent-1) | Registers a callback function to be called when the scroll event starts or stops. |
| [onTabContentUpdate](arkts-arkui-uiobserver-ontabcontentupdate-f.md#ontabcontentupdate) | 监听TabContent页面的切换事件。 |
| [onTabContentUpdate](arkts-arkui-uiobserver-ontabcontentupdate-f.md#ontabcontentupdate-1) | 监听TabContent页面的切换事件。 |
| [onWillDraw](arkts-arkui-uiobserver-onwilldraw-f.md#onwilldraw) | Registers a callback function to be called when the draw command will be drawn. |

### 类

| 名称 | 说明 |
| --- | --- |
| [DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md) | Density info. |
| [RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md) | RouterPageInfo包含的信息。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md) | NavDestination组件信息。 |
| [NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md) | Navigation组件页面切换的信息。 |
| [NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | Indicates the options of NavDestination switch. |
| [NavigationInfo](arkts-arkui-uiobserver-navigationinfo-i.md) | Navigation组件信息。 |
| [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | observer options. |
| [ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md) | ScrollEvent info. |
| [TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md) | TabContent页面的切换信息。 |
| [TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md) | 文本更改事件信息 |
| [WindowSizeLayoutBreakpointInfo](arkts-arkui-uiobserver-windowsizelayoutbreakpointinfo-i.md) | 定义窗口大小断点信息。 这个接口定义了当前窗口长宽的断点信息，基于配置好的断点阈值。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NavDestinationState](arkts-arkui-uiobserver-navdestinationstate-e.md) | NavDestination组件状态。 |
| [RouterPageState](arkts-arkui-uiobserver-routerpagestate-e.md) | routerPage生命周期触发时对应的状态。 |
| [ScrollEventType](arkts-arkui-uiobserver-scrolleventtype-e.md) | ScrollEvent type. |
| [TabContentState](arkts-arkui-uiobserver-tabcontentstate-e.md) | TabContent组件的状态。 |

