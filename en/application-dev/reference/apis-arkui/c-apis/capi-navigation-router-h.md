# navigation_router.h

## Overview

Defines a set of navigation or router enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NavDestinationState](#arkui_navdestinationstate) | ArkUI_NavDestinationState | Defines the state of the NavDestination component. |
| [ArkUI_RouterPageState](#arkui_routerpagestate) | ArkUI_RouterPageState | Define the state of Router Page. |

## Enum type description

### ArkUI_NavDestinationState

```c
enum ArkUI_NavDestinationState
```

**Description**

Defines the state of the NavDestination component.

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
| ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100 |  |

### ArkUI_RouterPageState

```c
enum ArkUI_RouterPageState
```

**Description**

Define the state of Router Page.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0 |  |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4 |  |


