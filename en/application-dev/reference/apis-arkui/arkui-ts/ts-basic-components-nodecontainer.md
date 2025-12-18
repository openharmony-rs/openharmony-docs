# NodeContainer
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

**NodeContainer** is a basic component for mounting custom nodes (such as [FrameNode](../js-apis-arkui-frameNode.md) or [BuilderNode](../js-apis-arkui-builderNode.md)) and dynamically managing node attachment and detachment through [NodeController](../js-apis-arkui-nodeController.md). This component does not support adding trailing child components and requires a [NodeController](../js-apis-arkui-nodeController.md) instance for operation. It must be used in combination with **NodeController**.

> **NOTE**
>
> This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> Only custom [FrameNodes](../js-apis-arkui-frameNode.md) or the root FrameNode obtained from a [BuilderNode](../js-apis-arkui-builderNode.md) can be attached to this component.
> [Proxy nodes](../js-apis-arkui-frameNode.md#ismodifiable12) of built-in system components obtained through querying cannot be attached to this component.
>
> This component does not work with the [attribute modifier](./ts-universal-attributes-attribute-modifier.md).
>
> During the construction of the node tree under this component, the UI instance [UIContext](../arkts-apis-uicontext-uicontext.md) is used. Switching between different UI instances might cause issues due to instance mismatches. As a result, this component currently does not support reusing nodes across multiple instances.
>
> When this component is not destroyed, the unmounting of mounted nodes is not triggered.

## Child Components

Not supported

## APIs

### NodeContainer

NodeContainer(controller: NodeController)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                                | Mandatory| Description                                                        |
| ---------- | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| controller | [NodeController](../js-apis-arkui-nodeController.md) | Yes  | **NodeController** instance used to control the upper and lower tree nodes in the **NodeContainer**. It represents the lifecycle of the **NodeContainer**.|
## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## Events

The [universal events](ts-component-general-events.md) are supported.

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
      this.rootNode.build(this.wrapBuilder, { text: "This is a Text" })
    }
    return this.rootNode.getFrameNode();
  }
}


@Entry
@Component
struct Index {
  private baseNode: MyNodeController = new MyNodeController()

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start, justifyContent: FlexAlign.SpaceEvenly }) {
      Text("This is a NodeContainer contains a text and a button ")
        .fontSize(9)
        .fontColor(0xCCCCCC)
      NodeContainer(this.baseNode)
        .borderWidth(1)
        .onClick(() => {
          console.info("click event");
        })
    }
    .padding({ left: 35, right: 35, top: 35 })
    .height(200)
    .width(300)
  }
}
```
![patternlock](figures/nodeContainer_sample.jpg)
