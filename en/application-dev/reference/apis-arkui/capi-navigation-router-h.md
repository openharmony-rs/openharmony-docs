# navigation_router.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-18T09:09:44.244Z pushedAt=2026-11-20T01:52:52.047Z nl=1 -->

## Overview

Defines the enumerations related to the **NavDestination** and **Router** components.

**File to include:** <arkui/node_attributes/navigation_router.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[NDKNavigation](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKNavigation)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_NavDestinationState](#arkui_navdestinationstate) | ArkUI_NavDestinationState | Enumerates the states of the **NavDestination** component, used to describe the lifecycle state changes of **NavDestination** during navigation. |
| [ArkUI_RouterPageState](#arkui_routerpagestate) | ArkUI_RouterPageState | Enumerates the states of the [Router](arkts-apis-uicontext-router.md) component (route page), used to describe the lifecycle state changes of **Router** during routing. |

## Enumeration Description

### ArkUI_NavDestinationState

```c
enum ArkUI_NavDestinationState
```

**Description**

Enumerates the states of the **NavDestination** component, used to describe the lifecycle state changes of **NavDestination** during navigation.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_NAV_DESTINATION_STATE_ON_SHOW = 0 | The **NavDestination** component is displayed.|
| ARKUI_NAV_DESTINATION_STATE_ON_HIDE = 1 | The **NavDestination** component is hidden.|
| ARKUI_NAV_DESTINATION_STATE_ON_APPEAR = 2 | The **NavDestination** component is mounted to the component tree. |
| ARKUI_NAV_DESTINATION_STATE_ON_DISAPPEAR = 3 | The **NavDestination** component is unmounted from the component tree.|
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_SHOW = 4 | The **NavDestination** is about to be displayed.|
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_HIDE = 5 | The **NavDestination** is about to be hidden.|
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_APPEAR = 6 | The **NavDestination** is about to be mounted to the component tree.|
| ARKUI_NAV_DESTINATION_STATE_ON_WILL_DISAPPEAR = 7 | The **NavDestination** component is about to be unmounted from the component tree.|
| ARKUI_NAV_DESTINATION_STATE_ON_ACTIVE = 8 | The **NavDestination** component is in the active state.<br>**Since:** 26.1.0 |
| ARKUI_NAV_DESTINATION_STATE_ON_INACTIVE = 9 | The **NavDestination** component is in the inactive state.<br>**Since:** 26.1.0 |
| ARKUI_NAV_DESTINATION_STATE_ON_BACK_PRESS = 100 | The **NavDestination** component receives a back operation, for example, when the user taps the back key or calls the back navigation API. |

### ArkUI_RouterPageState

```c
enum ArkUI_RouterPageState
```

**Description**

Enumerates the states of the [Router](arkts-apis-uicontext-router.md) component (route page), used to describe the lifecycle state changes of **Router** during routing.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0 | The page is about to appear. |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1 | The page is about to disappear. |
| ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2 | The page is displayed.|
| ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3 | The page is hidden.|
| ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4 | The page receives a back operation, for example, when the user taps the back key or calls the back navigation API. |


