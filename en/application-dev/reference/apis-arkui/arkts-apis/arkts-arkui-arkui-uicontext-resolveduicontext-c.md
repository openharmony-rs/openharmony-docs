# ResolvedUIContext

```TypeScript
export class ResolvedUIContext extends UIContext
```

**ResolvedUIContext** instance object.

> **NOTE:** 
> 
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.
> 
> - **ResolvedUIContext** is inherited from [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md). Objects of this class contain the [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) instance and its parsing policy.

**Inheritance/Implementation:** ResolvedUIContext extends [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## strategy

```TypeScript
strategy: ResolveStrategy
```

Resolving strategy of the UIContext.

**Type:** [ResolveStrategy](arkts-arkui-arkui-uicontext-resolvestrategy-e.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
