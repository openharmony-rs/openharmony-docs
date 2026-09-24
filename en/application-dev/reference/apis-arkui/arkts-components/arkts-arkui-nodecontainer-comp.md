# NodeContainer

**NodeContainer** is a basic component for mounting custom nodes (such as [FrameNode](../arkts-apis/arkts-arkui-typenode-n.md) or [BuilderNode](../arkts-apis/arkts-arkui-buildernode-c.md)) and dynamically managing node attachment and detachment through [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md). This component does not support adding trailing child components and requires a [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md) instance for operation. It must be used in combination with **NodeController**.

> **NOTE** > > Only custom [FrameNodes](../arkts-apis/arkts-arkui-typenode-n.md) or the root FrameNode obtained from a > [BuilderNode](../arkts-apis/arkts-arkui-buildernode-c.md) can be attached to this component. > > [Proxy nodes](../arkts-apis/arkts-arkui-framenode-c.md#ismodifiable) of built-in system components obtained through > querying cannot be attached to this component. > > This component does not work with the [attribute modifier](arkts-arkui-common-comp.md#common). > > A [UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) instance is used to construct the node tree for this component. During > instance switching, the input parameter of the > [makeNode](../arkts-apis/arkts-arkui-nodecontroller-c.md#makenode) callback method of the bound > [NodeController](../arkts-apis/arkts-arkui-nodecontroller-c.md) may be **undefined** due to instance mismatch. > Therefore, this component does not support cross-instance node reuse. > > When this component is not destroyed, the unmounting of its mounted child nodes will not be triggered.

## NodeContainer

```TypeScript
NodeContainer(controller: import('../api/@ohos.arkui.node').NodeController)
```

Creates a **NodeContainer** component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | import('../api/@ohos.arkui.node').NodeController | Yes | **NodeController** instance used to control the upper and lower tree nodes in the **NodeContainer**. It represents the lifecycle of the **NodeContainer**. |

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
