# PageInfo

```TypeScript
export interface PageInfo
```

Router和NavDestination等页面信息，若无对应的Router或NavDestination页面信息，则对应属性为undefined。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## navDestinationInfo

```TypeScript
navDestinationInfo?: observer.NavDestinationInfo
```

NavDestination页面信息，包含当前NavDestination页面的导航状态和页面信息。当页面为NavDestination页面时，可通过此属性获取对应的NavDestination页面信息；若当前页面不是NavDestination页面，则该属性为undefined。若无对应的NavDestination页面信息，则该属性为undefined。

**类型：** [observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## routerPageInfo

```TypeScript
routerPageInfo?: observer.RouterPageInfo
```

Router页面信息，包含当前Router页面的路由状态和页面信息。当页面为Router页面时，可通过此属性获取对应的Router页面信息；若当前页面不是Router页面，则该属性为undefined。若无对应的Router页面信息，则该属性为undefined。

**类型：** [observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
