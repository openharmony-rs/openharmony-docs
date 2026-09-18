# OverlayManagerOptions

Provides the parameters used for initializing [OverlayManager](arkts-arkui-arkui-uicontext-uicontext-c.md).

@interface OverlayManagerOptions

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## onBackPress

```TypeScript
onBackPress?: OnOverlayBackPressCallback
```

Callback for intercepting back-press events on an overlay.

**NOTE:** 
1. When this callback is registered and **enableBackPressedEvent** is set to **true**,
the back-press event will not close the overlay automatically. Instead, the overlay invokes this callback to decide whether the event should be propagated to the underlying components.
2. Return **true** to intercept the event (the event is consumed and will not be passed
to lower layers), or **false** to allow the event to propagate through to the components below the overlay.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableBackPressedEvent

```TypeScript
enableBackPressedEvent?: boolean
```

hether to enable the swipe-to-dismiss gesture for **ComponentContent** under **OverlayManager**. The value **true** means to enable the swipe-to-dismiss gesture, and **false** means the opposite. Default value: **false**.<br> **Atomic service API**: This API can be used in atomic services since API version 19.

**Type:** boolean

**Default:** false

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## renderRootOverlay

```TypeScript
renderRootOverlay?: boolean
```

Whether to render the overlay root node. The value **true** means to render the overlay root node, and **false** means the opposite. The default value is **true**.<br> **Atomic service API**: This API can be used in atomic services since API version 15.

**Type:** boolean

**Default:** true

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
