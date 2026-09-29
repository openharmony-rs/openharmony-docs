# NodeContainer

**NodeContainer** is a basic component for mounting custom nodes (such as [FrameNode](../arkts-apis/arkts-arkui-typenode-n.md) or the root FrameNode obtained from [BuilderNode](../arkts-apis/arkts-arkui-buildernode-c.md)) and dynamically controlling the mounting and unmounting of nodes through [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md). It is suitable for scenarios where custom nodes need to be dynamically inserted into and removed from the component tree to implement on-demand UI loading and node reuse, which improves page rendering efficiency and reduces node creation overhead. The component does not support appending child nodes. It accepts a [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md) instance and must be used together with **NodeController**.

> **NOTE:** 
> 
> - This component supports mounting only custom nodes, that is, [FrameNodes](../arkts-apis/arkts-arkui-typenode-n.md) or the root FrameNode obtained from a [BuilderNode](../arkts-apis/arkts-arkui-buildernode-c.md).
> 
> - Mounting the proxy node of a system component obtained through a query is not supported. For details, see [isModifiable](../arkts-apis/arkts-arkui-framenode-c.md#ismodifiable).
> 
> - This component does not work with the [attribute modifier](arkts-arkui-common-comp-attributemodifier-i.md).
> 
> - When the node tree under this component is built, the UI instance [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) is used. When the instance is switched, the input parameter of the [makeNode](../arkts-apis/arkts-arkui-nodecontroller-c.md#makenode) callback of the bound [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md) may be **undefined** due to instance mismatch.Therefore, this component does not support cross-instance node reuse.
> 
> - When this component is not destroyed, it does not proactively trigger the unmounting of the mounted node.

## Child Components

Not supported

## NodeContainer

```TypeScript
NodeContainer(controller: import('../api/@ohos.arkui.node').NodeController)
```

Creates a **NodeContainer** component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeContainerInterface-(controller: import('../api/@ohos.arkui.node').NodeController): NodeContainerAttribute--><!--Device-NodeContainerInterface-(controller: import('../api/@ohos.arkui.node').NodeController): NodeContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | import('../api/@ohos.arkui.node').NodeController | Yes | **NodeController** instance used to control the mounting and unmounting of nodes in **NodeContainer**. It represents the lifecycle of the **NodeContainer**. |

## Summary

## Examples

This example demonstrates how to mount a BuilderNode through NodeController.

```TypeScript
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
