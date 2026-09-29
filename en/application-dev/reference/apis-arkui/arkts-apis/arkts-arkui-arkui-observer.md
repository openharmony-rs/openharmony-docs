# @ohos.arkui.observer(Observer)

Provides APIs for listening for UI component behavior changes, including listening for page states, scroll events, page routing, screen pixel density, layout and drawing, page switching, and **TabContent** state changes. It is suitable for scenarios where UI state changes need to be sensed without intruding into the component service logic. [UIObserver](arkts-arkui-arkui-uicontext-uicontext-c.md) is recommended for component observation.

> **NOTE:** 
> 
> - UIObserver can only listen for relevant information within the current process and does not support obtaining information in cross-process scenarios<!--Del--> such as [UIExtensionComponent](../arkts-components/arkts-arkui-uiextensioncomponent-comp-sys.md)<!--DelEnd-->.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace uiObserver--><!--Device-unnamed-declare namespace uiObserver-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationupdate) | Unsubscribes from status changes of the **NavDestination** component. Compared with [uiObserver.off](arkts-arkui-uiobserver-off-f.md#offnavdestinationupdate), this API supports the **options** parameter, which enables you to specify the ID of the target **Navigation** component to observe. |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationupdate) | Unsubscribes from status changes of the **NavDestination** component. |
| [off](arkts-arkui-uiobserver-off-f.md#offscrollevent) | Unregisters the listener for the start and end of scroll events of a specific scrollable component identified by its ID. Supported components include [List](../arkts-components/arkts-arkui-list-comp.md), [Grid](../arkts-components/arkts-arkui-grid-comp.md), [Scroll](../arkts-components/arkts-arkui-scroll-comp.md), [WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md), and [ArcList](../arkts-components/arkts-arkui-arclist-comp.md). |
| [off](arkts-arkui-uiobserver-off-f.md#offscrollevent) | Unregisters the listener for the start and end of scroll events of all scrollable components. Supported components include [List](../arkts-components/arkts-arkui-list-comp.md), [Grid](../arkts-components/arkts-arkui-grid-comp.md), [Scroll](../arkts-components/arkts-arkui-scroll-comp.md), [WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md), and [ArcList](../arkts-components/arkts-arkui-arclist-comp.md). |
| [off](arkts-arkui-uiobserver-off-f.md#offrouterpageupdate) | Unsubscribes from state changes of the page during routing. |
| [off](arkts-arkui-uiobserver-off-f.md#offdensityupdate) | Unregisters the listener for screen pixel density changes. |
| [off](arkts-arkui-uiobserver-off-f.md#offwilldraw) | Unregisters the listener for drawing instruction dispatch in each frame. |
| [off](arkts-arkui-uiobserver-off-f.md#offdidlayout) | Unregisters the listener for layout completion status in each frame. |
| [off](arkts-arkui-uiobserver-off-f.md#offtabcontentupdate) | Unsubscribes from **TabContent** page switching events for the specified **Tabs** component identified by its ID. |
| [off](arkts-arkui-uiobserver-off-f.md#offtabcontentupdate) | Unsubscribes from the **TabContent** switching event. |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationswitch) | Unsubscribes from **Navigation** component page switching events. |
| [off](arkts-arkui-uiobserver-off-f.md#offnavdestinationswitch) | Unsubscribes from **Navigation** component page switching events. Compared with uiObserver.off, this API supports the **observerOptions** parameter, which enables you to configure observation options. |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationupdate) | Subscribes to status changes of the **NavDestination** component. Compared with [uiObserver.on](arkts-arkui-uiobserver-on-f.md#onnavdestinationupdate), this API supports the **options** parameter, which enables you to specify the ID of the target **Navigation** component to observe. |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationupdate) | Subscribes to status changes of the **NavDestination** component. |
| [on](arkts-arkui-uiobserver-on-f.md#onscrollevent) | Listens for the start and end of scroll events of a specific scrollable component identified by its ID. Supported components include [List](../arkts-components/arkts-arkui-list-comp.md), [Grid](../arkts-components/arkts-arkui-grid-comp.md), [Scroll](../arkts-components/arkts-arkui-scroll-comp.md), [WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md), and [ArcList](../arkts-components/arkts-arkui-arclist-comp.md). |
| [on](arkts-arkui-uiobserver-on-f.md#onscrollevent) | Listens for the start and end of scroll events of all scrollable components. Supported components include [List](../arkts-components/arkts-arkui-list-comp.md), [Grid](../arkts-components/arkts-arkui-grid-comp.md), [Scroll](../arkts-components/arkts-arkui-scroll-comp.md), [WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md), and [ArcList](../arkts-components/arkts-arkui-arclist-comp.md). |
| [on](arkts-arkui-uiobserver-on-f.md#onrouterpageupdate) | Subscribes to state changes of the page during routing. |
| [on](arkts-arkui-uiobserver-on-f.md#ondensityupdate) | Listens for screen pixel density changes. |
| [on](arkts-arkui-uiobserver-on-f.md#onwilldraw) | Listens for drawing instruction dispatch in each frame. |
| [on](arkts-arkui-uiobserver-on-f.md#ondidlayout) | Listens for layout completion status in each frame. |
| [on](arkts-arkui-uiobserver-on-f.md#ontabcontentupdate) | Subscribes to **TabContent** page switching events for the specified **Tabs** component identified by its ID. Unlike [on('tabChange')](../../../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#ontabchange22), this API does not support listening for the initial tab display event when the **Tabs** component is initialized. |
| [on](arkts-arkui-uiobserver-on-f.md#ontabcontentupdate) | Subscribes to **TabContent** switch events. Unlike [on('tabChange')](../../../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#ontabchange22), this API does not support listening for the initial tab display event when the **Tabs** component is initialized. |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationswitch) | Subscribes to **Navigation** component page switching events. |
| [on](arkts-arkui-uiobserver-on-f.md#onnavdestinationswitch) | Subscribes to **Navigation** component page switching events. Compared with uiObserver.on, this API supports the **observerOptions** parameter, which enables you to configure observation options. |

### Classes

| Name | Description |
| --- | --- |
| [DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md) | Provides the information contained in the callback when the screen pixel density changes. |
| [RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md) | Provides the information contained in **RouterPageInfo**, returned by the system to developers. |
| [WindowSizeLayoutBreakpointInfo](arkts-arkui-uiobserver-windowsizelayoutbreakpointinfo-c.md) | Provides information about window size layout breakpoint changes. |

### Interfaces

| Name | Description |
| --- | --- |
| [NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md) | Provides information about the **NavDestination** component, returned by the system to developers. |
| [NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md) | Provides the information about page switching of the **Navigation** component. |
| [NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | Provides the observer options for the page switching event of the **Navigation** component. |
| [NavigationInfo](arkts-arkui-uiobserver-navigationinfo-i.md) | Provides information about the **Navigation** component. |
| [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Describes the observer options. |
| [ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md) | Provides the scroll event information. |
| [TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md) | Provides the **TabContent** switching information. |
| [TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md) | Provides information about text changes in input fields. |

### Enums

| Name | Description |
| --- | --- |
| [NavDestinationState](arkts-arkui-uiobserver-navdestinationstate-e.md) | Describes the state of the **NavDestination** component. |
| [RouterPageState](arkts-arkui-uiobserver-routerpagestate-e.md) | Enumerates the states of a page during routing. **RouterPageState** is used in [RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md) as the callback parameter for passive observation via routerPageUpdate. |
| [ScrollEventType](arkts-arkui-uiobserver-scrolleventtype-e.md) | Enumerates the scroll event types. |
| [TabContentState](arkts-arkui-uiobserver-tabcontentstate-e.md) | Enumerates the **TabContent** component states. |
