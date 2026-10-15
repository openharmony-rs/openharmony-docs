# OverlayManagerOptions

```TypeScript
export interface OverlayManagerOptions
```

Provides the parameters used for initializing [OverlayManager](arkts-arkui-arkui-uicontext-uicontext-c.md).

@interface OverlayManagerOptions

**Since:** 15

<!--Device-unnamed-export interface OverlayManagerOptions--><!--Device-unnamed-export interface OverlayManagerOptions-End-->

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

Callback for intercepting the overlay swipe-back event.

**NOTE:** 
1. When this callback is registered and **enableBackPressedEvent** is set to **true**,
the swipe-back event does not automatically close the overlay. Instead, this callback is invoked to determine whether the event is passed to lower-level components.
2. The value **true** indicates that the event is intercepted (consumed and not passed to
lower-level components), and **false** indicates that the event is not intercepted and will be passed through to lower-level components.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OverlayManagerOptions-onBackPress?: OnOverlayBackPressCallback--><!--Device-OverlayManagerOptions-onBackPress?: OnOverlayBackPressCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableBackPressedEvent

```TypeScript
enableBackPressedEvent?: boolean
```

Whether to support closing the **ComponentContent** under **OverlayManager** through a swipe gesture. The value **true** indicates yes, and **false** indicates no. The default value is **false**.<br> **Atomic service API**: This API can be used in atomic services since API version 19.

**Type:** boolean

**Default:** false

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-OverlayManagerOptions-enableBackPressedEvent?: boolean--><!--Device-OverlayManagerOptions-enableBackPressedEvent?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## renderRootOverlay

```TypeScript
renderRootOverlay?: boolean
```

Whether to render the overlay root node. The value **true** indicates that the overlay root node is rendered, and **false** indicates the opposite. The default value is **true**. By setting this parameter to **false**, you can resolve the issue where **PhotoPickerComponent** cannot select photos when **OverlayManager** is displayed on top of it.<br> **Atomic service API**: This API can be used in atomic services since API version 15.

**Type:** boolean

**Default:** true

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-OverlayManagerOptions-renderRootOverlay?: boolean--><!--Device-OverlayManagerOptions-renderRootOverlay?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
