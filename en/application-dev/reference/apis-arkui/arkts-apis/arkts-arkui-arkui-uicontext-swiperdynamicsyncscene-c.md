# SwiperDynamicSyncScene

```TypeScript
export class SwiperDynamicSyncScene extends DynamicSyncScene
```

Provides frame rate configuration APIs for the **Swiper** component.

> **NOTE:** 

> - The initial APIs of this class are supported since API version 12.
> 
> - **SwiperDynamicSyncScene** inherits from [DynamicSyncScene](arkts-arkui-arkui-uicontext-uicontext-c.md) and represents the dynamic sync scene of the **Swiper** component.

**Inheritance/Implementation:** SwiperDynamicSyncScene extends [DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## type

```TypeScript
readonly type: SwiperDynamicSyncSceneType
```

Dynamic sync scene of the **Swiper** component.

**Type:** [SwiperDynamicSyncSceneType](arkts-arkui-arkui-uicontext-swiperdynamicsyncscenetype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
