# SmartGestureController

```TypeScript
export class SmartGestureController
```

Provides the capabilities of smart gestures enabling, listening, selected state control, and dynamic smart gesture behaviors decision. It is suitable for scenarios where an app integrates smart gestures, listens for the system's default gesture handling intent, and customizes gesture response behaviors, helping the app flexibly control the smart gesture interaction process.

> **NOTE:** 
> 
> To use the following APIs, you need to obtain a **SmartGestureController** instance using
> [getSmartGestureController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getsmartgesturecontroller) in **UIContext**.

**Since:** 26.0.0

<!--Device-unnamed-export class SmartGestureController--><!--Device-unnamed-export class SmartGestureController-End-->

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

Clears all callbacks for listening to smart gestures, which are registered in the current UI context.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SmartGestureController-clearMonitors(): void--><!--Device-SmartGestureController-clearMonitors(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

This example shows how to clear all callbacks for listening to smart gestures using the clearMonitors API. For details, see Example 1: Enabling Smart Gestures and Customizing Action Handling.

```TypeScript
import {
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    return new GestureHandlingResolution(true);
  };

  aboutToAppear(): void {
    this.controller.enableSmartTapAndSlideGestures(true);
    this.controller.registerMonitor(this.smartGestureMonitor);
  }

  aboutToDisappear(): void {
    this.controller.clearMonitors();
    this.controller.enableSmartTapAndSlideGestures(false);
  }

  build() {
    Scroll() {
      Column({ space: 12 }) {
        Text('Text component')
          .id('target_text')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```

## clearSelected

```TypeScript
clearSelected(): void
```

Clears the node selected by the current smart gesture.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SmartGestureController-clearSelected(): void--><!--Device-SmartGestureController-clearSelected(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

This example shows how to request the component to be selected and the selected state to be automatically cleared in 5,000 ms using the requestSelected and clearSelected APIs. For details, see Example 1: Enabling Smart Gestures and Customizing Action Handling.

```TypeScript
@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();

  aboutToAppear(): void {
    this.controller.enableSmartTapAndSlideGestures(true);
  }

  aboutToDisappear(): void {
    this.controller.enableSmartTapAndSlideGestures(false);
  }

  build() {
    Scroll() {
      Column({ space: 12 }) {
        Text('Text component')
          .id('target_text')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
        Button('Request Selection')
          .onClick(() => {
            this.controller.requestSelected('target_text');
            setTimeout(() => {
              this.controller.clearSelected();
              console.info('smartGesture selected is clear');
            }, 5000);
          })
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```

## enableSmartTapAndSlideGestures

```TypeScript
enableSmartTapAndSlideGestures(enabled: boolean): void
```

Sets whether to enable tap and slide gestures in smart gestures.

> **NOTE:** 
> 
> - This API affects only tap and slide gestures in smart gestures, but does not affect a wrist rotation gesture.
> 
> - After disabled, the [smartGestureShortcut](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#smartgestureshortcut) configuration on the component side will be retained, but tap and slide gestures in smart gestures will not be responded.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SmartGestureController-enableSmartTapAndSlideGestures(enabled: boolean): void--><!--Device-SmartGestureController-enableSmartTapAndSlideGestures(enabled: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable tap and slide gestures in smart gestures. The value **true** indicates yes, and **false** indicates no. |

**Examples**

This example shows how to enable and disable smart gestures using the enableSmartTapAndSlideGestures API. For details, see Example 1: Enabling Smart Gestures and Customizing Action Handling.

```TypeScript
@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  aboutToAppear(): void {
    this.controller.enableSmartTapAndSlideGestures(true);
  }

  aboutToDisappear(): void {
    this.controller.enableSmartTapAndSlideGestures(false);
  }

  build() {
    Scroll() {
      Column({ space: 12 }) {
        Text('Text component')
          .id('target_text')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```

## registerMonitor

```TypeScript
registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void
```

Registers a callback for listening to smart gestures. Before the system handles the current smart gesture, an application can receive the default action handling of the current gesture and perform custom intervention. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - This API allows an app to receive the processing intent of the current smart gesture event before the system handles it, and perform custom intervention.
> 
> - An app can use this callback to customize the behavior decision for the current smart gesture.
> 
> - An app can register multiple listener callbacks, which are triggered in last-registered-first-executed order.When a listener callback consumes the smart gesture event, that is, when the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md).isConsumed is **true**, subsequent listener callbacks will not be executed.
> 
> - When an app registers the same callback repeatedly, only the first registered callback is retained, and duplicate registrations do not take effect.
> 
> - The callback return value must be a valid [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)instance; otherwise, the current override does not take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SmartGestureController-registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void--><!--Device-SmartGestureController-registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitorCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BaseGestureHandlingProposal](arkts-arkui-arkui-uicontext-basegesturehandlingproposal-c.md), [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)&gt; | Yes | Smart gesture listener callback. The callback parameter is the default action handling provided by the system, and the return value declares whether to consume the current smart gesture and whether to replace the default action handling. |

**Examples**

This example shows how to register a callback for listening to smart gestures using the registerMonitor API. For details, see Example 1: Enabling Smart Gestures and Customizing Action Handling.

```TypeScript
import {
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    // Consume the current smart gesture and follow the system default action handling.
    return new GestureHandlingResolution(true);
  };

  aboutToAppear(): void {
    this.controller.enableSmartTapAndSlideGestures(true);
    this.controller.registerMonitor(this.smartGestureMonitor);
  }

  aboutToDisappear(): void {
    this.controller.unregisterMonitor(this.smartGestureMonitor);
    this.controller.enableSmartTapAndSlideGestures(false);
  }

  build() {
    Scroll() {
      Column({ space: 12 }) {
        Text('Text component')
          .id('target_text')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```

## requestSelected

```TypeScript
requestSelected(id: string): void
```

Requests to set a specified component as the node selected by the current smart gesture. After the selection is successful, a selection dialog box is displayed. The style of the selection dialog box varies depending on the device.

> **NOTE:** 
> 
> - The request takes effect only when the target component meets all of the following conditions: the component can respond to smart gestures, the component is visible on the screen, and the component is bound with [onClick](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onclick) or a tap gesture [TapGesture](../arkts-components/arkts-arkui-gesturecontrol-n.md#tapgesture).
> 
> - Whether a component can respond to smart gestures is determined by **enabled** in [smartGestureShortcut](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#smartgestureshortcut).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SmartGestureController-requestSelected(id: string): void--><!--Device-SmartGestureController-requestSelected(id: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Component [id](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id). The target component corresponding to this ID must meet the following requirements: it can respond to smart gestures, is visible on the screen, and is bound with [onClick](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onclick) or [TapGesture](../arkts-components/arkts-arkui-gesturecontrol-n.md#tapgesture). |

**Examples**

This example shows how to request the component to be selected and the selected state to be automatically cleared in 5,000 ms using the requestSelected and clearSelected APIs. For details, see Example 1: Enabling Smart Gestures and Customizing Action Handling.

```TypeScript
@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();

  aboutToAppear(): void {
    this.controller.enableSmartTapAndSlideGestures(true);
  }

  aboutToDisappear(): void {
    this.controller.enableSmartTapAndSlideGestures(false);
  }

  build() {
    Scroll() {
      Column({ space: 12 }) {
        Text('Text component')
          .id('target_text')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
        Button('Request Selection')
          .onClick(() => {
            this.controller.requestSelected('target_text');
            setTimeout(() => {
              this.controller.clearSelected();
              console.info('smartGesture selected is clear');
            }, 5000);
          })
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```

## unregisterMonitor

```TypeScript
unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void
```

Unregisters a callback for listening to smart gestures.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SmartGestureController-unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void--><!--Device-SmartGestureController-unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitorCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BaseGestureHandlingProposal](arkts-arkui-arkui-uicontext-basegesturehandlingproposal-c.md), [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)&gt; | Yes | Smart gesture listener callback to unregister. |

**Examples**

This example shows how to unregister a callback for listening to smart gestures using the unregisterMonitor API. For details, see Example 1: Enabling Smart Gestures and Customizing Action Handling.

```TypeScript
import {
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    return new GestureHandlingResolution(true);
  };

  aboutToAppear(): void {
    this.controller.enableSmartTapAndSlideGestures(true);
    this.controller.registerMonitor(this.smartGestureMonitor);
  }

  aboutToDisappear(): void {
    this.controller.unregisterMonitor(this.smartGestureMonitor);
    this.controller.enableSmartTapAndSlideGestures(false);
  }

  build() {
    Scroll() {
      Column({ space: 12 }) {
        Text('Text component')
          .id('target_text')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```
