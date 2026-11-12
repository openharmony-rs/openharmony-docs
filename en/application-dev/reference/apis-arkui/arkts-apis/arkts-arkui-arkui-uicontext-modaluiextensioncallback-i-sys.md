# ModalUIExtensionCallback (System API)

```TypeScript
export interface ModalUIExtensionCallback
```

Lifecycle callbacks for a modal UIExtension.

**Since:** 26.0.1

<!--Device-unnamed-export interface ModalUIExtensionCallback--><!--Device-unnamed-export interface ModalUIExtensionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## onDrawReady

```TypeScript
onDrawReady?: Callback<void>
```

Callback invoked after the UIExtensionAbility draws its first frame.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModalUIExtensionCallback-onDrawReady?: Callback<void>--><!--Device-ModalUIExtensionCallback-onDrawReady?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onError

```TypeScript
onError?: ErrorCallback
```

Callback invoked when an error occurs in the UIExtensionAbility.

**Type:** [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModalUIExtensionCallback-onError?: ErrorCallback--><!--Device-ModalUIExtensionCallback-onError?: ErrorCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onReceive

```TypeScript
onReceive?: ReceiveCallback
```

Callback invoked when data is received from the UIExtensionAbility.

**Type:** [ReceiveCallback](../arkts-components/arkts-arkui-uiextensioncomponent-comp-receivecallback-t-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModalUIExtensionCallback-onReceive?: ReceiveCallback--><!--Device-ModalUIExtensionCallback-onReceive?: ReceiveCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onRemoteReady

```TypeScript
onRemoteReady?: Callback<UIExtensionProxy>
```

Callback invoked after the UIExtensionAbility connection is established.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UIExtensionProxy](../arkts-components/arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md)&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModalUIExtensionCallback-onRemoteReady?: Callback<UIExtensionProxy>--><!--Device-ModalUIExtensionCallback-onRemoteReady?: Callback<UIExtensionProxy>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

Callback invoked when the UIExtensionAbility is terminated.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TerminationInfo](../arkts-components/arkts-arkui-embeddedcomponent-comp-terminationinfo-i.md)&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModalUIExtensionCallback-onTerminated?: Callback<TerminationInfo>--><!--Device-ModalUIExtensionCallback-onTerminated?: Callback<TerminationInfo>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
