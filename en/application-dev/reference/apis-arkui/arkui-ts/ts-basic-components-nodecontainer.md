# NodeContainer
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=af1c409994db2fe8f6b1e73fc3517a651a9626fe translatedAt=2026-09-03T04:19:21.272Z -->

A basic component used to mount custom nodes (such as [FrameNode](../js-apis-arkui-frameNode.md) or the root FrameNode obtained from [BuilderNode](../js-apis-arkui-builderNode.md)) and dynamically control the mounting and unmounting of nodes through [NodeController](../js-apis-arkui-nodeController.md). It is suitable for scenarios where custom nodes need to be dynamically inserted into and removed from the component tree to implement on-demand UI loading and node reuse, which improves page rendering efficiency and reduces node creation overhead. The component does not support appending child nodes. It accepts a [NodeController](../js-apis-arkui-nodeController.md) instance and must be used together with NodeController.

> **NOTE**
>
> - This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This component supports mounting only custom nodes, that is, [FrameNode](../js-apis-arkui-frameNode.md) or the root FrameNode obtained from [BuilderNode](../js-apis-arkui-builderNode.md).
>
> - Mounting the proxy node of a system component obtained through a query is not supported. For details, see [isModifiable](../js-apis-arkui-frameNode.md#ismodifiable12).
>
> - [Dynamic attribute setting](./ts-universal-attributes-attribute-modifier.md) is not supported.
>
> - When the node tree under this component is built, the UI instance [UIContext](../arkts-apis-uicontext-uicontext.md) is used. When the instance is switched, the input parameter of the [makeNode](../js-apis-arkui-nodeController.md#makenode) callback of the bound [NodeController](../js-apis-arkui-nodeController.md) may be undefined due to instance mismatch. Therefore, this component does not support cross-instance node reuse.
>
> - When this component is not destroyed, it does not proactively trigger the unmounting of the mounted node.

## Child Components

Not supported

## APIs

### NodeContainer

NodeContainer(controller: import('../api/@ohos.arkui.node').NodeController)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                                | Mandatory| Description                                                        |
| ---------- | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| controller | import('../api/@ohos.arkui.node').[NodeController](../js-apis-arkui-nodeController.md) | Yes | NodeController is used to control the attaching and detaching of nodes in NodeContainer, reflecting the lifecycle of the NodeContainer container. |
## Attributes

[Universal attributes](./ts-component-general-attributes.md) are supported, but [dynamic attribute setting](./ts-universal-attributes-attribute-modifier.md) is not supported.

## Events

[Universal events](./ts-component-general-events.md) are supported.

## Example

This example demonstrates how to mount a BuilderNode through **NodeController**.

```ts
import { NodeController, BuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

declare class Params {
  text: string
}

@Builder
function buttonBuilder(params: Params) {
  Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceEvenly }) {
    Text(params.text)
      .fontSize(12)
    Button(`This is a Button`, { type: ButtonType.Normal, stateEffect: true })
      .fontSize(12)
      .borderRadius(8)
      .backgroundColor(0x317aff)
  }
  .height(100)
  .width(200)
}

class MyNodeController extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(buttonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.rootNode === null) {
      this.rootNode = new BuilderNode(uiContext);
      this.rootNode.build(this.wrapBuilder, { text: 'This is a Text' })
    }
    return this.rootNode.getFrameNode();
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}


@Entry
@Component
struct Index {
  private baseNode: MyNodeController = new MyNodeController()

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start, justifyContent: FlexAlign.SpaceEvenly }) {
      Text('This is a NodeContainer contains a text and a button ')
        .fontSize(9)
        .fontColor(0xCCCCCC)
      NodeContainer(this.baseNode)
        .borderWidth(1)
        .onClick(() => {
          console.info('click event');
        })
    }
    .padding({ left: 35, right: 35, top: 35 })
    .height(200)
    .width(300)
  }
}
```
![NodeContainer example](figures/nodeContainer_sample.jpg)
