# PageInfo

```TypeScript
export interface PageInfo
```

Represents the page information of the router or navigation destination. If there is no related page information, **undefined** is returned.

**Since:** 12

<!--Device-unnamed-export interface PageInfo--><!--Device-unnamed-export interface PageInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

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

Navigation destination information.

**Type:** [observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PageInfo-navDestinationInfo?: observer.NavDestinationInfo--><!--Device-PageInfo-navDestinationInfo?: observer.NavDestinationInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## routerPageInfo

```TypeScript
routerPageInfo?: observer.RouterPageInfo
```

Router information.

**Type:** [observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PageInfo-routerPageInfo?: observer.RouterPageInfo--><!--Device-PageInfo-routerPageInfo?: observer.RouterPageInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
