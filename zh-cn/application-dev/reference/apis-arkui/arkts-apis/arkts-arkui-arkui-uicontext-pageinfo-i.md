# PageInfo

Defines the PageInfo type.The value of routerPageInfo indicates the information of the router page, or undefined if the frameNode does not have router page information. And the value of navDestinationInfo indicates the information of the navDestination, or undefined if the frameNode does not have navDestination information.

**起始版本：** 12

<!--Device-unnamed-export interface PageInfo--><!--Device-unnamed-export interface PageInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## navDestinationInfo

```TypeScript
navDestinationInfo?: observer.NavDestinationInfo
```

the property of navDestination information.

**类型：** observer.NavDestinationInfo

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PageInfo-navDestinationInfo?: observer.NavDestinationInfo--><!--Device-PageInfo-navDestinationInfo?: observer.NavDestinationInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## routerPageInfo

```TypeScript
routerPageInfo?: observer.RouterPageInfo
```

the property of router page information.

**类型：** observer.RouterPageInfo

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PageInfo-routerPageInfo?: observer.RouterPageInfo--><!--Device-PageInfo-routerPageInfo?: observer.RouterPageInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

