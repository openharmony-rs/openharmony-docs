# TargetInfo

```TypeScript
export interface TargetInfo
```

Specifies the target node for component binding.

**Since:** 18

<!--Device-unnamed-export interface TargetInfo--><!--Device-unnamed-export interface TargetInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## componentId

```TypeScript
componentId?: number
```

**UniqueID** of the custom component where the target node is located. When the above **id** is specified as the string type and the target node needs to be found within a specified custom component scope, this property can be used to define the scope, making it easier for you to ensure the uniqueness of **id: string** within a certain range. By default, no custom component scope is specified.

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TargetInfo-componentId?: number--><!--Device-TargetInfo-componentId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: string | number
```

Target node for binding popups or menus.<br>**NOTE:** <br>1. When **id** is a number, it corresponds to the component's **UniqueID**, whose uniqueness is guaranteed by the system.<br>2. When **id** is a string, it corresponds to the component specified by the universal attribute [id](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id). You must ensure the uniqueness of this ID, although there may be multiple instances.

**Type:** string &#124; number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TargetInfo-id: string | number--><!--Device-TargetInfo-id: string | number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
