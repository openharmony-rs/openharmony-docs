# navigation_router.h

## 概述

定义Navigation或Router组件的枚举和接口。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_NavDestinationState](#arkui_navdestinationstate) | ArkUI_NavDestinationState | 定义NavDestination组件的状态。 |
| [ArkUI_RouterPageState](#arkui_routerpagestate) | ArkUI_RouterPageState | 定义[Router](arkts-apis-uicontext-router.md)（路由页面）的状态。 |

## 枚举类型说明

### ArkUI_NavDestinationState

```c
enum ArkUI_NavDestinationState
```

**描述**

定义NavDestination组件的状态。

**起始版本：** 12

| 枚举项 | 描述 |
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

**描述**

定义[Router](arkts-apis-uicontext-router.md)（路由页面）的状态。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_APPEAR = 0 |  |
| ARKUI_ROUTER_PAGE_STATE_ABOUT_TO_DISAPPEAR = 1 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_SHOW = 2 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_HIDE = 3 |  |
| ARKUI_ROUTER_PAGE_STATE_ON_BACK_PRESS = 4 |  |


