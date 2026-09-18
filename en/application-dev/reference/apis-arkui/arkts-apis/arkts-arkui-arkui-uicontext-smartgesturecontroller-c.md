# SmartGestureController

Provides the capability to enable smart gestures, monitor them, control the selection state, and dynamically determine smart gesture behavior.

> **NOTE:** 
> 
> The following APIs must be called using a **SmartGestureController** instance obtained via
> [getSmartGestureController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getsmartgesturecontroller) in **UIContext**.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## clearMonitors

```TypeScript
clearMonitors(): void
```

Clears all monitoring callbacks registered for the current **UIContext**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clearSelected

```TypeScript
clearSelected(): void
```

Clears the currently selected node of smart gestures.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableSmartTapAndSlideGestures

```TypeScript
enableSmartTapAndSlideGestures(enabled: boolean): void
```

Sets whether to enable the tap and slide operations of smart gestures.

> **NOTE:** 
> 
> - This API affects only the tap and slide smart gestures, not the wrist-turn gesture.
> 
> - When disabled, the [smartGestureShortcut](../arkts-components/arkts-arkui-commonmethod-c.md#smartgestureshortcut)attribute on the component side is retained, but the tap and slide smart gestures will not be responded to.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the tap and slide smart gesture handling. The value **true** means to enable it, and **false** means to disable it. |

## registerMonitor

```TypeScript
registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void
```

Registers a smart gesture monitoring callback. Before the system processes the current smart gesture, the application can receive the default action handling of the current gesture and apply custom intervention. The callback is used for asynchronous callbacks.

> **NOTE:** 
> 
> - This API enables the application to receive the system's handling intent for the current smart gesture event before it is processed by the system and apply custom intervention.
> 
> - Users can customize the behavior of the current smart gesture through this callback.
> 
> - Multiple monitoring callbacks can be registered. They are triggered in the reverse order of registration (the last registered one is executed first). When a monitoring callback consumes the smart gesture event, that is,when the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md).isConsumed is **true**,subsequent monitoring callbacks will not be executed.
> 
> - If the same callback is registered repeatedly, only the first registration takes effect; duplicate registrations are ignored.
> 
> - The return value of the callback must be a valid [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)instance; otherwise, the modification will not take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitorCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BaseGestureHandlingProposal](arkts-arkui-arkui-uicontext-basegesturehandlingproposal-c.md), [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)&gt; | Yes | Smart gesture monitoring callback. The callback parameter is the default action handling provided by the system, and the return value is used to declare whether to consume the current smart gesture and whether to replace the default action handling. |

## requestSelected

```TypeScript
requestSelected(id: string): void
```

Requests to set the specified component as the current smart gesture selected node. After successful selection, a selection prompt box is displayed. The style of the selection box varies by device.

> **NOTE:** 
> 
> - The request takes effect only when all the following conditions are met: the target component can respond to smart gestures, the component is visible on the screen, and the component has an onClick event bound or a [TapGesture](../arkts-components/arkts-arkui-gesturecontrol-n.md#tapgesture) gesture bound.
> 
> - Whether a component can respond to smart gestures is determined by **enabled** in [smartGestureShortcut](../arkts-components/arkts-arkui-commonmethod-c.md#smartgestureshortcut).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Component id. |

## unregisterMonitor

```TypeScript
unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void
```

Unregisters a smart gesture monitoring callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitorCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BaseGestureHandlingProposal](arkts-arkui-arkui-uicontext-basegesturehandlingproposal-c.md), [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)&gt; | Yes | The smart gesture monitoring callback to unregister. |
