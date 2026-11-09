# ApplicationShortcutCallbackInfo

```TypeScript
export interface ApplicationShortcutCallbackInfo
```

Provides information about the UI instance that triggers an application-level keyboard shortcut.

**Since:** 26.1.0

<!--Device-unnamed-export interface ApplicationShortcutCallbackInfo--><!--Device-unnamed-export interface ApplicationShortcutCallbackInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler, GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback, SwiperContentInfo, SwiperItemInfo, BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## uiContext

```TypeScript
uiContext: UIContext
```

UIContext of the UI instance that triggers the application-level keyboard shortcut.

**Type:** [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ApplicationShortcutCallbackInfo-uiContext: UIContext--><!--Device-ApplicationShortcutCallbackInfo-uiContext: UIContext-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
