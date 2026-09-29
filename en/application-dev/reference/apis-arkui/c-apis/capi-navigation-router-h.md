# navigation_router.h

## Overview

Defines the enumerations related to the **NavDestination** and **Router** components.

**Library**: libace_ndk.z.so

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

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

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_NAV_DESTINATION_STATE_ON_SHOW = 0 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_HIDE = 1 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_APPEAR = 2 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR = 3 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW = 4 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE = 5 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR = 6 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR = 7 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_ACTIVE = 8 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_INACTIVE = 9 |  |
| ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100 |  |

### ArkUI_RouterPageState

```c
enum ArkUI_RouterPageState
```

**Description**

Enumerates the states of the Router component (route page), used to describe the lifecycle state changes of **Router** during routing.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0 |  |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4 |  |


