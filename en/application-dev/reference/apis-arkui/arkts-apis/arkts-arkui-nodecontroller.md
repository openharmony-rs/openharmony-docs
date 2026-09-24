# NodeController

## Summary

### Classes

| Name | Description |
| --- | --- |
| [NodeController](arkts-arkui-nodecontroller-c.md) | The **NodeController** module provides APIs for managing custom nodes, such as creating, showing, and updating custom nodes, and APIs for mounting custom nodes to a [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) component. |

## Examples

### Example 1: Adding Lifecycle Callbacks for Node Layout, Touch, Attachment, and Detachment Events

This example demonstrates how to implement lifecycle callbacks of the NodeContainer component using aboutToResize and onTouchEvent for node layout and touch event receiving.

It implements lifecycle callbacks for the NodeContainer node attachment to the main node tree and detachment from the main node tree through aboutToAppear and aboutToDisappear.

It also shows how to mount a BuilderNode using NodeController.



```TypeScript
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

### Example 2: Implementing Lifecycle Callbacks for Node Binding/Unbinding and Tree Attachment/Detachment

This example demonstrates how to implement lifecycle of callbacks of the NodeContainer component using onAttach and onDetach when it is attached to or detached from the main node tree.

It implements lifecycle callbacks using onWillBind, onWillUnbind, onBind, and onUnbind when it is bound or unbound.

```TypeScript
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
