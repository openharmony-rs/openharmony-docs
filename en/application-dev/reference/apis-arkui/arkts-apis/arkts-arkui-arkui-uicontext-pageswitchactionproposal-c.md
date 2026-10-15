# PageSwitchActionProposal

```TypeScript
export class PageSwitchActionProposal extends TargetedGestureProposal
```

Handles the smart gesture page turning action. The default direction is forward page turning, including rightward and downward. When dynamically customizing smart gesture behavior through the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor) API, setting the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)'s **selectedProposal** to an object of this typetriggers the page turning operation of the target component.

**Inheritance/Implementation:** PageSwitchActionProposal extends [TargetedGestureProposal](arkts-arkui-arkui-uicontext-targetedgestureproposal-c.md)

**Since:** 26.0.0

<!--Device-unnamed-export class PageSwitchActionProposal extends TargetedGestureProposal--><!--Device-unnamed-export class PageSwitchActionProposal extends TargetedGestureProposal-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(node: FrameNode, pageCount: number)
```

Constructor for the smart gesture page turning action handling.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PageSwitchActionProposal-constructor(node: FrameNode, pageCount: int)--><!--Device-PageSwitchActionProposal-constructor(node: FrameNode, pageCount: int)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node that responds to the page turning action. |
| pageCount | number | Yes | Number of pages to turn.<br>Value range: [0, +∞). Values less than 0 are treated as 0.<br>Unit: page. |

## pageCount

```TypeScript
pageCount: number
```

Number of pages for the smart gesture page turning.

Value range: [0, +∞). Values less than 0 are treated as 0.

Unit: page.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PageSwitchActionProposal-pageCount: int--><!--Device-PageSwitchActionProposal-pageCount: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
