# DragController

```TypeScript
export class DragController
```

Provides drag-and-drag control capabilities, supporting the proactive initiation of dragging with attached drag information when the application receives events such as touch or long press. It also supports creating drag actions, obtaining the drag preview, controlling drag event reporting and drag start requests, canceling drag data loading, and displaying the drop-disallowed badge when dropping onto a target area is not allowed.

> **NOTE:** 
> 
> In the following API examples, you must first use [getDragController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) in
> **UIContext** to obtain a **DragController** instance, and then call the APIs using the obtained instance.

**Since:** 11

<!--Device-unnamed-export class DragController--><!--Device-unnamed-export class DragController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## interruptFollowHandMorphDropAnimation

```TypeScript
interruptFollowHandMorphDropAnimation(): boolean
```

Interrupt the pending follow-hand morph drop animation and trigger the finish sequence immediately.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DragController-interruptFollowHandMorphDropAnimation(): boolean--><!--Device-DragController-interruptFollowHandMorphDropAnimation(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Interruption result.<br>Returns **true** if the interruption is successful, and **false** if there is no pending follow-hand morph drop animation to interrupt. |
