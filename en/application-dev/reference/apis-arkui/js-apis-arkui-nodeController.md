# NodeController
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=a5a9b13e76430cfff45e4873767cacc1b9c0082b translatedAt=2026-08-29T09:36:36.056Z pushedAt=2026-08-31T11:55:31.023Z -->

The **NodeController** module provides APIs for managing custom nodes, such as creating, showing, and updating custom nodes, and APIs for mounting custom nodes to a [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md). It is suitable for scenarios where custom nodes need to be dynamically created, updated, and reused on a page.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - NodeController objects do not support JSON serialization.

## Modules to Import

```ts
import { NodeController } from '@kit.ArkUI';
```

## NodeController

Creates a controller to manage the bound [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) component. This API is typically used together with [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md). One **NodeController** can be bound to only one [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) component. For best practices, see Dynamic Component Creation: [Dynamically Adding, Updating, and Deleting Components](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/arkts-ui-component-dynamic-creation#dynamically-adding-updating-and-deleting-components).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### makeNode

abstract makeNode(uiContext : UIContext): FrameNode | null

Called when the [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) component bound to this **NodeController** is created. This callback returns a node, which will be mounted to the [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md).

Alternatively, the callback can be triggered through the **rebuild()** API of **NodeController**.

> **NOTE**
>
> [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) does not support cross-instance reuse. If [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) is reused across instances and [NodeController](#nodecontroller-1) passed to [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) triggers the [makeNode](#makenode) callback, the [UIContext](./arkts-apis-uicontext-uicontext.md) object in the input parameter may be **undefined**. In this case, you need to check whether the object is **undefined** to prevent [invalid UIContext](../../ui/arkts-wrong-uicontext-debug.md#identifying-uicontext-errors) when the input parameter is used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                                                                                                         |
| --------- | ----------------------------------------- | ---- | ------------------------------------------------------------------------------------------------------------- |
| uiContext | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes | UI context bound to [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) when this API is called back. When [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) is reused across instances, this parameter may be undefined, and you need to determine this yourselves. |

**Return value**

| Type            | Description                                                                                                                                                                                                                                                       |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FrameNode](./js-apis-arkui-frameNode.md) \| null | **FrameNode** object. The returned node will be mounted to the placeholder node of [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md). If **null** is returned, the child nodes of the corresponding [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) will be cleared. |

### aboutToAppear

aboutToAppear?(): void

Called when the [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) bound to this **NodeController** instance is attached to the main node tree. This callback is asynchronous, and its actual execution time is later than the attachment.

> **NOTE**
>
> For details about the callback timing, see [onAppear](arkui-ts/ts-universal-events-show-hide.md#onappear).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### aboutToDisappear

aboutToDisappear?(): void

Called when the [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) bound to this **NodeController** instance is detached from the main node tree. This callback is synchronous.

> **NOTE**
>
> For details about the callback timing, see [onDisAppear](arkui-ts/ts-universal-events-show-hide.md#ondisappear).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### onAttach<sup>18+</sup>

onAttach?(): void

Called when the [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) bound to this **NodeController** instance is attached to the main node tree. It is triggered at the same time as [aboutToAppear](#abouttoappear) (both when the **NodeContainer** is attached to the main node tree). The difference is that **onAttach** is a synchronous callback while **aboutToAppear** is an asynchronous callback, so **onAttach** is executed before **aboutToAppear**.

> **NOTE**
>
> For details about the callback timing, see [onAttach](arkui-ts/ts-universal-events-show-hide.md#onattach12).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### onDetach<sup>18+</sup>

onDetach?(): void

Called when the [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) bound to this **NodeController** instance is detached from the main node tree. It is triggered at the same time as [aboutToDisappear](#abouttodisappear) (both when the **NodeContainer** is detached from the main node tree). Both are synchronous callbacks. During the detachment process, the framework triggers **onDetach** first and then **aboutToDisappear**, so **onDetach** is executed before **aboutToDisappear**.

> **NOTE**
>
> For details about the callback timing, see [onDetach](arkui-ts/ts-universal-events-show-hide.md#ondetach12).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### onWillBind<sup>18+</sup>

onWillBind?(containerId: number): void

Called when **NodeController** is about to be bound to [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md). This callback is triggered before [onBind](#onbind18). Both are optional callbacks, and the corresponding logic can be executed before or after binding as needed.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                                                                                                         |
| ----------- | ------ |----- |---------------------------------------------------------------------------------------------------------------------------------- |
| containerId | number | Yes   | Identifier of [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) that is about to be bound with **NodeController** when this API is called back.|

### onWillUnbind<sup>18+</sup>

onWillUnbind?(containerId: number): void

Called when **NodeController** is about to be unbound from [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md). This callback is triggered before [onUnbind](#onunbind18). Both are optional callbacks, and the corresponding logic can be executed before or after unbinding as needed.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                                                                                                         |
| ----------- | ------ |----- |---------------------------------------------------------------------------------------------------------------------------------- |
| containerId | number | Yes  | Identifier of  [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) that is about to be unbound from **NodeController** when this API is called back.|

### onBind<sup>18+</sup>

onBind?(containerId: number): void

Called after **NodeController** is bound to [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md). This callback is triggered after [onWillBind](#onwillbind18). Both are optional callbacks, and the corresponding logic can be executed before or after binding as needed.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                                                                                                         |
| ----------- | ------ |----- |---------------------------------------------------------------------------------------------------------------------------------- |
| containerId | number | Yes  | Identifier of [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) that has been bound to **NodeController** when this API is called back.|

### onUnbind<sup>18+</sup>

onUnbind?(containerId: number): void

Called after **NodeController** is unbound from [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md). This callback is triggered after [onWillUnbind](#onwillunbind18). Both are optional callbacks, and the corresponding logic can be executed before or after unbinding as needed.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                     | Mandatory| Description                                                                                                         |
| ----------- | ------ |----- |---------------------------------------------------------------------------------------------------------------------------------- |
| containerId | number | Yes | Identifier of [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) that has been unbound from **NodeController** when this API is called back. |

### aboutToResize

aboutToResize?(size: Size): void

Called when [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) bound to **NodeController** is laid out.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                    | Mandatory| Description                                    |
| ------ | ---------------------------------------- | ---- | ---------------------------------------- |
| size   | [Size](./js-apis-arkui-graphics.md#size) | Yes   | Width and height of the component layout size, in vp. |

### onTouchEvent

onTouchEvent?(event: TouchEvent): void

Called when [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) bound to **NodeController** receives a touch event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                                     | Mandatory| Description      |
| ------ | ------------------------------------------------------------------------- | ---- | ---------- |
| event  | [TouchEvent](arkui-ts/ts-universal-events-touch.md#touchevent) | Yes   | Touch event, which contains information such as the coordinates of the touch point and the touch action type. For details, see **TouchEvent**. |

### rebuild

rebuild(): void

Notifies the [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) component to call the [makeNode](#makenode) API again to change the child node. For example, when the content data displayed by **NodeContainer** changes and the displayed child node needs to be updated, this API can be called to trigger a rebuild.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

> **NOTE**
>
> Since the **rebuild** API is proactively called by the application and the operation is UI-related, you must ensure that the UI context is valid when calling this API, that is, the UI context must be consistent with that of the bound **NodeContainer**.
>
> In cases where the [UI context is unclear](../../ui/arkts-global-interface.md#ambiguous-ui-context), for example, during event callbacks, you can use the [runScopedTask](./arkts-apis-uicontext-uicontext.md#runscopedtask) API of [UIContext](./arkts-apis-uicontext-uicontext.md) to explicitly define the UI context at the time of the call.

## Example

### Example 1: Adding Lifecycle Callbacks for Node Layout, Touch, Attachment, and Detachment Events

This example demonstrates how to implement lifecycle callbacks of the **NodeContainer** component using **aboutToResize** and **onTouchEvent** for node layout and touch event receiving.

It implements lifecycle callbacks for the **NodeContainer** node attachment to the main node tree and detachment from the main node tree through **aboutToAppear** and **aboutToDisappear**.

It also shows how to mount a BuilderNode using **NodeController**.

```ts
import { NodeController, BuilderNode, Size, FrameNode, UIContext } from '@kit.ArkUI';

class Params {
  text: string = 'this is a text';
}

@Builder
function buttonBuilder(params: Params) {
  Column() {
    Button(params.text)
      .fontSize(12)
      .borderRadius(8)
      .borderWidth(2)
      .backgroundColor(Color.Orange)
  }
}

class MyNodeController extends NodeController {
  private buttonNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(buttonBuilder);

  makeNode(uiContext: UIContext): FrameNode {
    if (this.buttonNode == null) {
      this.buttonNode = new BuilderNode(uiContext);
      this.buttonNode.build(this.wrapBuilder, { text: 'This is a Button' });
    }
    return this.buttonNode!.getFrameNode()!;
  }

  aboutToResize(size: Size) {
    console.info(`aboutToResize width : ${size.width} height : ${size.height}`);
  }

  aboutToAppear() {
    console.info('aboutToAppear');
  }

  aboutToDisappear() {
    this.buttonNode?.dispose();
    console.info('aboutToDisappear');
  }

  onTouchEvent(event: TouchEvent) {
    console.info('onTouchEvent');
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
    }
    .padding({ left: 35, right: 35, top: 35 })
    .width('100%')
    .height('100%')
  }
}
```
![nodecontroller](figures/node_controller.jpg)

### Example 2: Implementing Lifecycle Callbacks for Node Binding/Unbinding and Tree Attachment/Detachment

This example demonstrates how to implement lifecycle of callbacks of the **NodeContainer** component using **onAttach** and **onDetach** when it is attached to or detached from the main node tree.

It implements lifecycle callbacks using **onWillBind**, **onWillUnbind**, **onBind**, and **onUnbind** when it is bound or unbound.

```ts
import { NodeController, BuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

class Params {
  text: string = 'this is a text';
}

@Builder
function buttonBuilder(params: Params) {
  Column() {
    Button(params.text)
      .fontSize(20)
      .borderRadius(8)
      .borderWidth(2)
      .backgroundColor(Color.Grey)
  }
}

class MyNodeController extends NodeController {
  private buttonNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(buttonBuilder);

  makeNode(uiContext: UIContext): FrameNode {
    if (this.buttonNode == null) {
      this.buttonNode = new BuilderNode(uiContext);
      this.buttonNode.build(this.wrapBuilder, { text: 'This is a Button' });
    }
    return this.buttonNode!.getFrameNode()!;
  }

  onAttach(): void {
    console.info('myButton on attach');
  }

  onDetach(): void {
    console.info('myButton on detach');
  }

  onWillBind(containerId: number): void {
    console.info(`myButton on WillBind${containerId}`);
  }

  onWillUnbind(containerId: number): void {
    console.info(`myButton on WillUnbind${containerId}`);
  }

  onBind(containerId: number): void {
    console.info(`myButton on bind: ${containerId}`);
  }

  onUnbind(containerId: number): void {
    console.info(`myButton on unbind: ${containerId}`);
  }

  aboutToDisappear() {
    this.buttonNode?.dispose();
  }
}

@Entry
@Component
struct Index {
  @State buttonShow: boolean = true;
  @State buttonIndex: number = 0;
  private buttonController: MyNodeController = new MyNodeController();
  private buttonNull: null = null;
  private buttonControllerArray: Array<MyNodeController | null> = [this.buttonController, this.buttonNull];

  build() {
    Column() {
      Row() {
        Button('Bind/Unbind')
          .onClick(() => {
            this.buttonIndex++;
          }).margin(5)
        Button('onAttach/onDetach')
          .onClick(() => {
            this.buttonShow = !this.buttonShow;
          }).margin(5)
      }

      if (this.buttonShow) {
        NodeContainer(this.buttonControllerArray[this.buttonIndex % this.buttonControllerArray.length])
      }
    }
    .padding({ left: 35, right: 35 })
    .width('100%')
    .height('100%')
  }
}
```

![nodecontroller2](figures/node_controller2.jpg)
