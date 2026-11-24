# navigation_router.h

## Overview

Defines the enumerations related to the **NavDestination** and **Router** components.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NavDestinationState](#arkui_navdestinationstate) | ArkUI_NavDestinationState | Enumerates the states of the **NavDestination** component, used to describe the lifecycle state changes of **<br>NavDestination** during navigation. |
| [ArkUI_RouterPageState](#arkui_routerpagestate) | ArkUI_RouterPageState | Enumerates the states of the Router component (route page), used to describe the lifecycle state changes of **Router** during routing. |

## Enum type description

### ArkUI_NavDestinationState

```c
enum ArkUI_NavDestinationState
```

**Description**

Enumerates the states of the **NavDestination** component, used to describe the lifecycle state changes of **<br>NavDestination** during navigation.

<!--Device-enum ArkUI_NavDestinationState--><!--Device-enum ArkUI_NavDestinationState-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_NAV_DESTINATION_STATE_ON_SHOW = 0 | The NavDestination show.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_SHOW = 0--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_SHOW = 0-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_HIDE = 1 | The NavDestination hide.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_HIDE = 1--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_HIDE = 1-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_APPEAR = 2 | The NavDestination is mounted to the component tree.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_APPEAR = 2--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_APPEAR = 2-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR = 3 | The NavDestination removed from the component tree.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR = 3--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR = 3-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW = 4 | Before the NavDestination show.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW = 4--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW = 4-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE = 5 | Before the NavDestination hide.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE = 5--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE = 5-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR = 6 | Before the NavDestination mount to the component tree.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR = 6--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR = 6-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR = 7 | Before the NavDestination removed from the component tree.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR = 7--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR = 7-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_ACTIVE = 8 | The NavDestination component is active.<br>**Since**: 26.1.0<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_ACTIVE = 8--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_ACTIVE = 8-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_INACTIVE = 9 | The NavDestination component is inactive.<br>**Since**: 26.1.0<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_INACTIVE = 9--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_INACTIVE = 9-End--> |
| ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100 | The NavDestination returns from the component.<br>**Since**: 12<br><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100--><!--Device-ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100-End--> |

### ArkUI_RouterPageState

```c
enum ArkUI_RouterPageState
```

**Description**

Enumerates the states of the Router component (route page), used to describe the lifecycle state changes of **Router** during routing.

<!--Device-enum ArkUI_RouterPageState--><!--Device-enum ArkUI_RouterPageState-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0 | The Router Page is about to be created.<br>**Since**: 12<br><!--Device-ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0--><!--Device-ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0-End--> |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1 | The Router Page is about to be destroyed.<br>**Since**: 12<br><!--Device-ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1--><!--Device-ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1-End--> |
| ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2 | The Router Page show.<br>**Since**: 12<br><!--Device-ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2--><!--Device-ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2-End--> |
| ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3 | The Router Page hide.<br>**Since**: 12<br><!--Device-ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3--><!--Device-ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3-End--> |
| ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4 | The Router Page returns.<br>**Since**: 12<br><!--Device-ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4--><!--Device-ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4-End--> |


