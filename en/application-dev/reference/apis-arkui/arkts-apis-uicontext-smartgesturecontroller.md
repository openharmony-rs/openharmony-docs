# Class (SmartGestureController)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

Provides capabilities to enable, listen to, and control the selected state of smart gestures, as well as dynamically determine smart gesture behavior.

> **NOTE**
>
> To use the following APIs, you need to obtain the **SmartGestureController** instance using [getSmartGestureController()](./arkts-apis-uicontext-uicontext.md#getsmartgesturecontroller) in **UIContext**.

**Since**: 26.0.0

## enableSmartTapAndSlideGestures

enableSmartTapAndSlideGestures(enabled: boolean): void

Sets whether to enable tap and slide gestures in smart gestures.

> **NOTE**
>
> - This API affects only tap and slide gestures in smart gestures, but does not affect a wrist rotation gesture.
> - After disabled, the [smartGestureShortcut](arkui-ts/ts-universal-attributes-smart-gesture-shortcut.md#smartgestureshortcut) configuration on the component side will be retained, but tap and slide gestures in smart gestures will not be responded.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| enabled | boolean | Yes| Whether to enable tap and slide gestures in smart gestures. The value **true** indicates to enable, and **false** indicates the opposite.|

**Example**

This example shows how to enable and disable smart gestures using the **enableSmartTapAndSlideGestures** API. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
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
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```
![smartgesture_01](figures/smartgesture_01.png)

## registerMonitor

registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void

Registers a callback for listening to smart gestures. Before the system handles the current smart gesture, an application can receive the default action handling of the current gesture and perform custom intervention. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> - This API allows an application to receive the handling intent of the current smart gesture event before the system handles it and perform custom intervention.
> - You can use this callback to customize the behavior of the current smart gesture.
> - You can register multiple listener callbacks, which are triggered in the principle of "last registered, first executed". When a listener callback consumes the smart gesture event, that is, the return value of [GestureHandlingResolution](#gesturehandlingresolution).isConsumed is **true**, subsequent listener callbacks will not be executed.
> - If the same callback is registered repeatedly, only the callback registered for the first time is saved, and repeated registrations do not take effect.
> - The return value of the callback must be a valid [GestureHandlingResolution](#gesturehandlingresolution) instance. Otherwise, the handling does not take effect.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| monitorCallback | [Callback](arkui-ts/ts-types.md#callback12)&lt;[BaseGestureHandlingProposal](#basegesturehandlingproposal), [GestureHandlingResolution](#gesturehandlingresolution)&gt; | Yes| Callback for listening to smart gestures. The callback parameter is the default action handling provided by the system. The return value is used to declare whether to consume the current smart gesture and whether to replace the default action handling.|

**Example**

This example shows how to register a callback for listening to smart gestures using the **registerMonitor** API. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
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
  }

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
![smartgesture_01](figures/smartgesture_01.png)

## unregisterMonitor

unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void

Unregisters a callback for listening to smart gestures.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| monitorCallback | [Callback](arkui-ts/ts-types.md#callback12)&lt;[BaseGestureHandlingProposal](#basegesturehandlingproposal), [GestureHandlingResolution](#gesturehandlingresolution)&gt; | Yes| Callback to unregister.|

**Example**

This example shows how to unregister a callback for listening to smart gestures using the **unregisterMonitor** API. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
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
  }

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
![smartgesture_01](figures/smartgesture_01.png)

## clearMonitors

clearMonitors(): void

Clears all callbacks for listening to smart gestures, which are registered in the current UI context.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

This example shows how to clear all callbacks for listening to smart gestures using the **clearMonitors** API. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
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
  }

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
![smartgesture_01](figures/smartgesture_01.png)

## requestSelected

requestSelected(id: string): void

Requests to set a specified component as the node selected by the current smart gesture. After the selection is successful, a selection dialog box is displayed. The style of the selection dialog box varies depending on the device.

> **NOTE**
> 
> - The request takes effect only when the target component meets all of the following conditions: The component can respond to smart gestures, the component is visible on the screen, and the component is bound to [onClick](./arkui-ts/ts-universal-events-click.md#onclick) or [a tap gesture](using the ./arkui-ts/ts-basic-gestures-tapgesture.md#apis).
> - Whether a component can respond to smart gestures is determined by **enabled** in [smartGestureShortcut](arkui-ts/ts-universal-attributes-smart-gesture-shortcut.md#smartgestureshortcut).

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| id | string | Yes| [ID](./arkui-ts/ts-universal-attributes-component-id.md#id) of the component.|

**Example**

This example shows how to request the component to be selected and the selected state to be automatically cleared in 5,000 ms using the **requestSelected** and **clearSelected** APIs. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
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
            }, 5000)
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
![smartgesture_02](figures/smartgesture_02.png)

## clearSelected

clearSelected(): void

Clears the node selected by the current smart gesture.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

This example shows how to request the component to be selected and the selected state to be automatically cleared in 5,000 ms using the **requestSelected** and **clearSelected** APIs. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
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
            }, 5000)
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
![smartgesture_02](figures/smartgesture_02.png)

## BaseGestureHandlingProposal

Base class for smart gesture handling. When the [registerMonitor](#registermonitor) API is used to dynamically customize smart gesture behavior, the callback parameter type is an instance of a specific subclass type.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| action | [SmartGestureAction](arkui-ts/ts-appendix-enums.md#smartgestureaction) | No| No| Final action to be taken by a smart gesture.|
| operateIntention | [OperateIntention](arkui-ts/ts-appendix-enums.md#operateintention) | No| No| Underlying operation intent of a smart gesture.|

**Example**

This example shows how to obtain smart gesture handling information from **BaseGestureHandlingProposal** in the smart gesture listening callback. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
import {
  BaseGestureHandlingProposal, GestureHandlingResolution,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    console.info('smartGesture action is ', proposal.action, ', operateIntention is ', proposal.operateIntention)
    return new GestureHandlingResolution(true);
  }

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
![smartgesture_01](figures/smartgesture_01.png)

## TargetedGestureProposal

Base class for smart gesture handling with a target node.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| node | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | No| No| Target node for handling the current smart gesture.|

**Example**

This example shows how to obtain smart gesture handling information from **TargetedGestureProposal** in the smart gesture listening callback. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
import {
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
  TargetedGestureProposal,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    let targetProposal = proposal as TargetedGestureProposal;
    console.info('smartGesture action is', targetProposal.action, ', operateIntention is',
      targetProposal.operateIntention, ', nodeId is', targetProposal.node.getId());
    return new GestureHandlingResolution(true);
  }

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
![smartgesture_01](figures/smartgesture_01.png)

## ClickActionProposal

Handles the click action of a smart gesture. When the [registerMonitor](#registermonitor) API is used to dynamically customize smart gesture behavior, if **selectedProposal** in the returned object [GestureHandlingResolution](#gesturehandlingresolution) is set to an object of the click type, the click action of the target component will be triggered.

> **NOTE**
> 
> - The action handling follows the semantic of "select first, then click".
> - If the target node has not been selected, the selection state is established first in this handling, and the click action is not triggered immediately.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(node: FrameNode)

Constructor for handling the click action of a smart gesture.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| node | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | Yes| Target node that responds to the click action.|

**Example**

This example shows how to customize the smart gesture action as the click action for handling in the smart gesture listening callback. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
import {
  BaseGestureHandlingProposal,
  ClickActionProposal,
  GestureHandlingResolution,
  TargetedGestureProposal,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    let targetProposal = proposal as TargetedGestureProposal;
    let result = new GestureHandlingResolution(true);
    console.info('smartGesture action is', targetProposal.action, ', operateIntention is',
      targetProposal.operateIntention, ', nodeId is', targetProposal.node.getId());
    if (targetProposal.node && targetProposal.node.getId() == 'target_text') {
      let clickProposal = new ClickActionProposal(targetProposal.node)
      result.selectedProposal = clickProposal;
    }
    return result;
  }

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
![smartgesture_01](figures/smartgesture_01.png)

## SelectActionProposal

Handles the selection action of a smart gesture. When the [registerMonitor](#registermonitor) API is used to dynamically customize smart gesture behavior, if **selectedProposal** in the returned object [GestureHandlingResolution](#gesturehandlingresolution) is set to an object of the selection type, the target component will be selected.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(node: FrameNode)

Constructor for handling the selection action of a smart gesture.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| node | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | Yes| Target node that responds to the selected action.|

**Example**

This example shows how to customize the smart gesture action as the selection action for handling in the smart gesture listening callback. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
import {
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
  SelectActionProposal,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    let result = new GestureHandlingResolution(true);
    let node = this.getUIContext().getFrameNodeById('target_text2');
    if (node) {
      let selectProposal = new SelectActionProposal(node)
      result.selectedProposal = selectProposal;
    }
    return result;
  }

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
        Text('Text component 1')
          .id('target_text1')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
        Text('Text component 2')
          .id('target_text2')
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
![smartgesture_03](figures/smartgesture_03.png)

## NoneActionProposal

Handles the empty action of a smart gesture. When the [registerMonitor](#registermonitor) API is used to dynamically customize smart gesture behavior, if **selectedProposal** in the returned object [GestureHandlingResolution](#gesturehandlingresolution) is set to an object of the empty type, no action will be triggered.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

Constructor for handling the empty action of a smart gesture.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

This example shows how to customize the smart gesture action as the empty action for handling in the smart gesture listening callback. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
import {
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
  NoneActionProposal,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    let result = new GestureHandlingResolution(true);
    let noneProposal = new NoneActionProposal()
    result.selectedProposal = noneProposal;
    return result;
  }

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
        Text('Text component 1')
          .id('target_text1')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
        Text('Text component 2')
          .id('target_text2')
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
![smartgesture_07](figures/smartgesture_07.png)

## BackPressActionProposal

Handles the back action of a smart gesture. When the [registerMonitor](#registermonitor) API is used to dynamically customize smart gesture behavior, if **selectedProposal** in the returned object [GestureHandlingResolution](#gesturehandlingresolution) is set to an object of the back type, the previous page will be returned.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

Constructor for handling the back action of a smart gesture.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

This example shows how to customize the smart gesture action as the back action for handling in the smart gesture listening callback. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
import {
  BackPressActionProposal,
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    let result = new GestureHandlingResolution(true);
    let backProposal = new BackPressActionProposal()
    result.selectedProposal = backProposal;
    return result;
  }

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
        Text('Text component 1')
          .id('target_text1')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })
        Text('Text component 2')
          .id('target_text2')
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
![smartgesture_07](figures/smartgesture_07.png)

## PageSwitchActionProposal

Handles the page switching action of a smart gesture. The default direction is forward, including rightward and downward. When the [registerMonitor](#registermonitor) API is used to dynamically customize smart gesture behavior, if **selectedProposal** in the returned object [GestureHandlingResolution](#gesturehandlingresolution) is set to an object of the page switching type, the page switching action of the target component will be triggered.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(node: FrameNode, pageCount: number)

Constructor for handling the page switching action of a smart gesture.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| node | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | Yes| Target node that responds to the page switching action.|
| pageCount | number | Yes| Number of pages to be switched.<br>Value range: [0, +∞). A value less than 0 evaluates to the value **0**.<br>The unit is page.|

### Attributes

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| pageCount | number | No| No| Number of pages to be switched by a smart gesture.<br>Value range: [0, +∞). A value less than 0 evaluates to the value **0**.<br>The unit is page.|

**Example**

This example shows how to customize the smart gesture action as the page switching action for handling in the smart gesture listening callback. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling)](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
import {
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
  PageSwitchActionProposal,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    let result = new GestureHandlingResolution(true);
    let node = this.getUIContext().getFrameNodeById('target_swiper');
    if (node) {
      let pageSwitchProposal = new PageSwitchActionProposal(node, 2);
      result.selectedProposal = pageSwitchProposal;
    }
    return result;
  }

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
        Swiper() {
          Column({ space: 8 }) {
            Text('page 0')
          }
          .justifyContent(FlexAlign.Start)
          .padding(12)

          Column({ space: 8 }) {
            Text('page 1')
          }
          .justifyContent(FlexAlign.Start)
          .padding(12)

          Column({ space: 8 }) {
            Text('page 2')
          }
          .justifyContent(FlexAlign.Start)
          .padding(12)
        }
        .width(180)
        .height(180)
        .id('target_swiper')
        .index(0)
        .loop(false)
        .borderRadius(12)
        .borderWidth(1)
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```
![smartgesture_04](figures/smartgesture_04.png)

## ScrollActionProposal

Handles the scrolling action of a smart gesture. The default direction is forward, including rightward and downward. When the [registerMonitor](#registermonitor) API is used to dynamically customize smart gesture behavior, if **selectedProposal** in the returned object [GestureHandlingResolution](#gesturehandlingresolution) is set to an object of the scrolling type, the scrolling action of the target component will be triggered.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(node: FrameNode, distance: number)

Constructor for handling the scrolling action of a smart gesture.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| node | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | Yes| Target node that responds to the scrolling action.|
| distance | number | Yes| Scrolling distance.<br>Value range: [0, +∞). A value less than 0 evaluates to the value **0**.<br>The unit is vp.|

### Attributes

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| distance | number | No| Yes| Scrolling distance of a smart gesture.<br>Value range: [0, +∞). A value less than 0 evaluates to the value **0**.<br>The unit is vp.|

**Example**

This example shows how to customize the smart gesture action as the scrolling action for handling in the smart gesture listening callback. For details, see [Example 1: Enabling Smart Gestures and Customizing Action Handling](#example-1-enabling-smart-gestures-and-customizing-action-handling).

```ts
import {
  BaseGestureHandlingProposal,
  GestureHandlingResolution,
  ScrollActionProposal,
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  private arrayList = [0, 1, 2, 3, 4, 5, 6];
  private smartGestureMonitor = (proposal: BaseGestureHandlingProposal) => {
    let result = new GestureHandlingResolution(true);
    let node = this.getUIContext().getFrameNodeById('target_list');
    if (node) {
      let scrollProposal = new ScrollActionProposal(node, 60);
      result.selectedProposal = scrollProposal;
    }
    return result;
  }

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
        List({ space: 8 }) {
          ForEach(this.arrayList, (item: number) => {
            ListItem() {
              Column({ space: 6 }) {
                Text(`inner list item ${item}`)
                  .id(`inner_list_item_${item}`)
                  .fontSize(14)
                  .padding(8)
                  .width('100%')
                  .borderRadius(10)
                  .borderWidth(1)
                  .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
              }
              .width('100%')
            }
          }, (item: number) => item.toString())
        }
        .id('target_list')
        .width('100%')
        .height(80)
        .borderRadius(12)
        .borderWidth(1)
      }.width('100%')
    }
    .layoutWeight(1)
    .width('100%')
    .height('100%')
    .padding(12)
  }
}
```
![smartgesture_05](figures/smartgesture_05.png)

## GestureHandlingResolution

Declaration class of the smart gesture handling resolution.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(isConsumed: boolean)

Constructor for the smart gesture handling resolution.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ---- | ---- | ---- |
| isConsumed | boolean | Yes| Whether to consume the current smart gesture.<br>The value **true** indicates to consume the current smart gesture. In this case, if [selectedProposal](#attributes-2) is not set, the default action handling is used; if [selectedProposal](#attributes-2) is set, the custom action handling is used.<br>The value **false** indicates not to consume the current smart gesture. In this case, the system considers the gesture as unhandled.|

### Attributes

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| isConsumed | boolean | No| No| Whether to consume the current smart gesture.<br>The value **true** indicates to consume the current smart gesture. In this case, if **selectedProposal** is not set, the default action handling is used; if **selectedProposal** is set, the custom action handling is used.<br>The value **false** indicates not to consume the current smart gesture. In this case, the system considers the gesture as unhandled.|
| selectedProposal | [BaseGestureHandlingProposal](#basegesturehandlingproposal) | No| Yes| User-defined smart gesture handling behavior.<br>When **isConsumed** is set to **true**, if **selectedProposal** is not set, the default action handling is used; if **selectedProposal** is set, the custom action handling is used.<br>When **isConsumed** is set to **false**, the **selectedProposal** setting does not take effect.|

## Example

### Example 1: Enabling Smart Gestures and Customizing Action Handling

This example shows how to enable and disable smart gestures using the [enableSmartTapAndSlideGestures](arkts-apis-uicontext-smartgesturecontroller.md#enablesmarttapandslidegestures) API, register, unregister, or clear monitors using the [registerMonitor](arkts-apis-uicontext-smartgesturecontroller.md#registermonitor), [unregisterMonitor](arkts-apis-uicontext-smartgesturecontroller.md#unregistermonitor), and [clearMonitors](arkts-apis-uicontext-smartgesturecontroller.md#clearmonitors) APIs for custom action handling, and select a component using the [requestSelected](arkts-apis-uicontext-smartgesturecontroller.md#requestselected) API.

Since API version 26.0.0, **enableSmartTapAndSlideGestures**, **registerMonitor**, **unregisterMonitor**, **clearMonitors**, and **requestSelected** are added.

```ts
import {
  BackPressActionProposal,
  BaseGestureHandlingProposal,
  ClickActionProposal,
  GestureHandlingResolution,
  NoneActionProposal,
  PageSwitchActionProposal,
  ScrollActionProposal,
  SelectActionProposal
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  @State clickCount: number = 0;
  @State hint: string = '';
  // Customize a callback function.
  private callback = (proposal: BaseGestureHandlingProposal): GestureHandlingResolution => {
    // proposal.operateIntention indicates the underlying operation intent. The value can be TAP, SLIDE_FORWARD, or BACK_PRESS.
    // proposal.action indicates the final action to be executed. The value can be NONE, SELECT, CLICK, PAGE_FORWARD, SCROLL_FORWARD, or BACK_PRESS.
    this.hint = `Intent=${proposal.operateIntention}, Action=${proposal.action}`;

    const resolution = new GestureHandlingResolution(true);

    // Override the action to click.
    if (proposal.action === SmartGestureAction.CLICK) {
      const node = this.getUIContext().getFrameNodeById('target_button');
      if (node) {
        resolution.selectedProposal = new ClickActionProposal(node);
      }
    }
    // Override the action to selection.
    else if (proposal.action === SmartGestureAction.SELECT) {
      const node = this.getUIContext().getFrameNodeById('target_text');
      if (node) {
        resolution.selectedProposal = new SelectActionProposal(node);
      }
    }
    // Override the action to page switching.
    else if (proposal.action === SmartGestureAction.PAGE_FORWARD) {
      const node = this.getUIContext().getFrameNodeById('scroll_area');
      if (node) {
        // pageCount: The value range is [0, +∞), in pages.
        resolution.selectedProposal = new PageSwitchActionProposal(node, 1);
      }
    }
    // Override the action to scrolling.
    else if (proposal.action === SmartGestureAction.SCROLL_FORWARD) {
      const node = this.getUIContext().getFrameNodeById('scroll_area');
      if (node) {
        // distance: The value range is [0, +∞), in vp.
        resolution.selectedProposal = new ScrollActionProposal(node, 180);
      }
    }
    // Override the action to none (no action is performed).
    else if (proposal.action === SmartGestureAction.NONE) {
      resolution.selectedProposal = new NoneActionProposal();
    }
    // Override the action to back.
    else if (proposal.action === SmartGestureAction.BACK_PRESS) {
      resolution.selectedProposal = new BackPressActionProposal();
    }

    return resolution;
  };

  build() {
    Scroll() {
      Column({ space: 12 }) {
        // Operation intent prompt.
        Text(this.hint).fontSize(13).fontColor('#666')

        // Target node: text
        Text('Text component')
          .id('target_text')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })

        // Target node: button
        Button(`Button Component/Click=${this.clickCount}`)
          .id('target_button').width('100%')
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            this.clickCount += 1;
          })

        // Target node: scrollable area
        Scroll() {
          Column({ space: 6 }) {
            ForEach([0, 1, 2, 3], (item: number) => {
              Text(`Scrollable content ${item}`).width('100%').padding(10).borderRadius(8)
                .backgroundColor(item % 2 === 0 ? '#f6f8fa' : '#ffffff')
            })
          }.width('100%')
        }
        .id('scroll_area').height(120)

        Divider()

        // requestSelected/clearSelected
        Text('Selection control').fontWeight(FontWeight.Bold).fontSize(16)
        Row({ space: 8 }) {
          Button('Select').layoutWeight(1)
            .onClick(() => this.controller.requestSelected('target_button'))
          Button('Select Text').layoutWeight(1)
            .onClick(() => this.controller.requestSelected('target_text'))
          Button('Clear Selection').layoutWeight(1)
            .onClick(() => this.controller.clearSelected())
        }.width('100%')

        // registerMonitor/unregisterMonitor/clearMonitors
        Text('Monitor control').fontWeight(FontWeight.Bold).fontSize(16)
        Row({ space: 8 }) {
          Button('Register').layoutWeight(1)
            .onClick(() => this.controller.registerMonitor(this.callback))
          Button('Unregister').layoutWeight(1)
            .onClick(() => this.controller.unregisterMonitor(this.callback))
          Button('Clear').layoutWeight(1)
            .onClick(() => this.controller.clearMonitors())
        }.width('100%')

        // enableSmartTapAndSlideGestures
        Row({ space: 8 }) {
          Button('Enable Gesture').layoutWeight(1)
            .onClick(() => this.controller.enableSmartTapAndSlideGestures(true))
          Button('Disable Gesture').layoutWeight(1)
            .onClick(() => this.controller.enableSmartTapAndSlideGestures(false))
        }.width('100%')
      }.width('100%')
    }
    .width('100%')
    .layoutWeight(1)
    .onAppear(() => {
      this.controller.enableSmartTapAndSlideGestures(true);
      this.controller.registerMonitor(this.callback);
    })
    .width('100%')
    .height('100%')
    .padding(12)
    .backgroundColor('#f1f3f5')
  }
}
```
![smartgesture_06](figures/smartgesture_06.png)

<!--no_check-->