# ModalUIExtensionOptions (System API)

```TypeScript
export interface ModalUIExtensionOptions
```

Options for creating a modal UIExtension.

**Since:** 26.0.1

<!--Device-unnamed-export interface ModalUIExtensionOptions--><!--Device-unnamed-export interface ModalUIExtensionOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: DpiFollowStrategy
```

DPI follow strategy for the modal UIExtension.

**Type:** [DpiFollowStrategy](../arkts-components/arkts-arkui-uiextensioncomponent-comp-dpifollowstrategy-e-sys.md)

**Default:** DpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModalUIExtensionOptions-dpiFollowStrategy?: DpiFollowStrategy--><!--Device-ModalUIExtensionOptions-dpiFollowStrategy?: DpiFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## transition

```TypeScript
transition?: TransitionEffect
```

Transition effect played when the modal UIExtension is shown or closed.

**Type:** [TransitionEffect](../arkts-components/arkts-arkui-common-comp-transitioneffect-c.md)

**Default:** TransitionEffect.IDENTITY

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModalUIExtensionOptions-transition?: TransitionEffect--><!--Device-ModalUIExtensionOptions-transition?: TransitionEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: WindowModeFollowStrategy
```

Window mode follow strategy for the modal UIExtension.

**Type:** [WindowModeFollowStrategy](../arkts-components/arkts-arkui-uiextensioncomponent-comp-windowmodefollowstrategy-e-sys.md)

**Default:** WindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModalUIExtensionOptions-windowModeFollowStrategy?: WindowModeFollowStrategy--><!--Device-ModalUIExtensionOptions-windowModeFollowStrategy?: WindowModeFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
