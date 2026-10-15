# GestureObserverConfigs

```TypeScript
export interface GestureObserverConfigs
```

Specifies the gesture callback phases to listen for (passing an empty array means no gesture callback stage is listened for). Notifications are sent only when the gesture triggers the specified phases.

**Since:** 20

<!--Device-unnamed-export interface GestureObserverConfigs--><!--Device-unnamed-export interface GestureObserverConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## actionPhases

```TypeScript
actionPhases: Array<GestureActionPhase>
```

Gesture callback phases to listen for. An empty array is invalid. Notifications are sent only when the gesture triggers the specified phases.

**Type:** Array&lt;[GestureActionPhase](arkts-arkui-arkui-uicontext-gestureactionphase-e.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-GestureObserverConfigs-actionPhases: Array<GestureActionPhase>--><!--Device-GestureObserverConfigs-actionPhases: Array<GestureActionPhase>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
