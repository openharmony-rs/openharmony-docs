# BuilderNode

## Summary

### Classes

| Name | Description |
| --- | --- |
| [BuilderNode](arkts-arkui-buildernode-c.md) | The **BuilderNode** module provides APIs for a BuilderNode – a custom node that can be used to mount built-in components. A BuilderNode can be used only as a leaf node. For details, see [BuilderNode Development](../../../ui/arkts-user-defined-arktsNode-builderNode.md). For best practices, see [Dynamic Component Creation: Dynamically Adding, Updating, and Deleting Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-ui-dynamic-operations#section153921947151012). |
| [ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md) | **ReactiveBuilderNode** uses the stateless UI method [@Builder](../../../ui/state-management/arkts-builder.md) to generate a component tree and holds the root node of the component tree. A ReactiveBuilderNode cannot be defined as a state variable. [FrameNode](arkts-arkui-typenode-n.md) held in **ReactiveBuilderNode** is used only to mount the ReactiveBuilderNode as a child node to another FrameNode. Undefined behavior may occur if you set attributes or perform operations on subnodes of the FrameNode held by the ReactiveBuilderNode. Therefore, after you have obtained a RenderNode through the [getFrameNode](arkts-arkui-buildernode-c.md#getframenode) method of the ReactiveBuilderNode and the [getRenderNode](arkts-arkui-framenode-c.md#getrendernode) method of the [FrameNode](arkts-arkui-typenode-n.md), avoid setting the attributes or operating the subnodes through APIs of [RenderNode](arkts-arkui-rendernode-c.md). |

### Interfaces

| Name | Description |
| --- | --- |
| [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | Defines the optional build options. |
| [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | Provides optional parameters for creating a BuilderNode. |

### Enums

| Name | Description |
| --- | --- |
| [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | Enumerates the node rendering types. |

### Types

| Name | Description |
| --- | --- |
| [InputEventType](arkts-arkui-inputeventtype-t.md) | Defines the type of input event to be dispatched. For details, see [postInputEvent](arkts-arkui-buildernode-c.md#postinputevent). |

## Examples

### Example 1: Handling Mouse Events in BuilderNode

This example demonstrates the end-to-end process for intercepting mouse events in a custom component and performing coordinate conversion. The component reads local x- and y-coordinates through the [onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse) callback, then uses vp2px to convert relative coordinates to pixel coordinates based on the offset obtained from FrameNode.getPositionToParent(). The windowX, windowY, displayX, and displayY values in [MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent) are updated accordingly. Finally, the converted mouse event is posted to child nodes through rootNode.postInputEvent(event).



```TypeScript
import { NodeController, BuilderNode, FrameNode, PromptAction, UIContext, InputEventType } from '@kit.ArkUI';

// Define the class for passing parameters.
class Params {
  text: string = 'this is a text';
  uiContext: UIContext | null = null;
}

@Builder
function ButtonBuilder(params: Params) {
  Column() {
    Button(params.text)
      .borderWidth(2)
      .align(Alignment.Center)
      .backgroundColor(Color.Orange)
      .fontSize(20)
      .width('45%')
      .height('30%')
      .offset({ x: 60, y: 100 })
      .borderRadius('50%')
      .onMouse((event) => {
        let promptAction: PromptAction = params.uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onMouse',
          duration: 3000
        });
        console.info('onMouse');
      })
      .onTouch((event) => {
        let promptAction: PromptAction = params.uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onTouch',
          duration: 3000
        });
        console.info('onTouch');
      })
  }
  .width(500)
  .height(300)
  .backgroundColor(Color.Gray)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postMouseEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of buildNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let mouseEvent = event as MouseEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      mouseEvent.windowX = uiContext.vp2px(offsetX + mouseEvent.x);
      mouseEvent.windowY = uiContext.vp2px(offsetY + mouseEvent.y);
    }
    // Post the mouse event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEvent(event);
    return result;
  }

  postTouchEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of buildNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let touchEvent = event as TouchEvent;
    let changedTouchLen = touchEvent.changedTouches.length;
    for (let i = 0; i < changedTouchLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
        touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
      }
    }
    let touchesLen = touchEvent.touches.length;
    for (let i = 0; i < touchesLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
        touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
      }
    }
    // Post the touch event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEvent(event);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Stack() {
      NodeContainer(this.nodeController)
        .height(300)
        .width(500)
      Column()
        .width(500)
        .height(300)
        .backgroundColor(Color.Transparent)
        .onMouse((event) => {
          if (event != undefined) {
            this.nodeController.postMouseEvent(event, this.getUIContext());
          }
        })
        .onTouch((event) => {
          if (event != undefined) {
            this.nodeController.postTouchEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 100 })
  }
}
```

### Example 2: Handling Touch Events in BuilderNode

This example demonstrates the end-to-end process for intercepting touch events in a custom component and transforming touch point coordinates. The implementation: 1. iterates through changedTouches and touches arrays of [TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent) in the [onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch) callback; 2. for each touch point, adds the component offset to the X and Y coordinates and converts the result to pixels using vp2px; 3. updates the windowX, windowY, displayX, and displayY values of each touch point; 4. posts the processed touch event to child nodes using rootNode.postInputEvent(event).



```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext, PromptAction, InputEventType } from '@kit.ArkUI';

// Define the class for passing parameters.
class Params {
  text: string = 'this is a text';
  uiContext: UIContext | null = null;
}

@Builder
function ButtonBuilder(params: Params) {
  Column() {
    Button(params.text)
      .borderWidth(2)
      .align(Alignment.Center)
      .backgroundColor(Color.Orange)
      .fontSize(20)
      .width('45%')
      .height('30%')
      .offset({ x: 60, y: 100 })
      .borderRadius('50%')
      .onTouch((event) => {
        let promptAction: PromptAction = params.uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onTouch',
          duration: 3000
        });
        console.info('onTouch');
      })
  }
  .width(500)
  .height(300)
  .backgroundColor(Color.Gray)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postInputEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of buildNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    // Forward only original touch events, not mouse-simulated touch events.
    if (event.source == SourceType.TouchScreen) {
      let touchEvent = event as TouchEvent;
      let changedTouchLen = touchEvent.changedTouches.length;
      for (let i = 0; i < changedTouchLen; i++) {
        if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
          touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
          touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
        }
      }
      let touchesLen = touchEvent.touches.length;
      for (let i = 0; i < touchesLen; i++) {
        if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
          touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
          touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
        }
      }
    }

    // Post the touch event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEvent(event);
    return result;
  }
  
  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Stack() {
      NodeContainer(this.nodeController)
        .height(300)
        .width(500)
      Column()
        .width(500)
        .height(300)
        .backgroundColor(Color.Transparent)
        .onTouch((event) => {
          if (event != undefined) {
            this.nodeController.postInputEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 100 })
  }
}
```

### Example 3: Handling Axis Events in BuilderNode

This example demonstrates the end-to-end process for intercepting wheel or trackpad axis events in a custom component and performing coordinate conversion. The implementation: 1. obtains relative X and Y coordinates from the [onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent) callback; 2. adds the component offset and converts the result to pixels using vp2px; 3. updates the windowX, windowY, displayX, and displayY values in AxisEvent; 4. posts the transformed axis event to child nodes using rootNode.postInputEvent(event).



```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext, PromptAction, InputEventType } from '@kit.ArkUI';

// Define the class for passing parameters.
class Params {
  text: string = 'this is a text';
  uiContext: UIContext | null = null;
}

@Builder
function ButtonBuilder(params: Params) {
  Column() {
    Button(params.text)
      .borderWidth(2)
      .align(Alignment.Center)
      .backgroundColor(Color.Orange)
      .fontSize(20)
      .width('45%')
      .height('30%')
      .offset({ x: 60, y: 100 })
      .borderRadius('50%')
      .onAxisEvent((event) => {
        let promptAction: PromptAction = params.uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onAxisEvent',
          duration: 3000
        });
        console.info('onAxisEvent');
      })
  }
  .width(500)
  .height(300)
  .backgroundColor(Color.Gray)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postInputEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of buildNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let axisEvent = event as AxisEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      axisEvent.windowX = uiContext.vp2px(offsetX + axisEvent.x);
      axisEvent.windowY = uiContext.vp2px(offsetY + axisEvent.y);
    }
    // Post the axis event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEvent(event);
    return result;
  }
  
  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Stack() {
      NodeContainer(this.nodeController)
        .height(300)
        .width(500)
      Column()
        .width(500)
        .height(300)
        .backgroundColor(Color.Transparent)
        .onAxisEvent((event) => {
          if (event != undefined) {
            this.nodeController.postInputEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 100 })
  }
}
```

### Example 4: Passing a BuilderNode Shared localStorage Instance

This example demonstrates how to pass an external [localStorage](../arkui-ts/ts-state-management.md#localstorage9) instance to a BuilderNode through the build method. In this case, all custom components mounted on the BuilderNode share this localStorage.

```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

// Define the class for passing parameters.
class Params {
  text: string = ''

  constructor(text: string) {
    this.text = text;
  }
}

let globalBuilderNode: BuilderNode<[Params]> | null = null;

@Builder
function buildText(params: Params) {
  Column() {
    Text('BuildNodeContentArea')
      .fontSize(25)
    CustomComp()
  }
}

// Implement a custom textNode controller by extending NodeController.
class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    if (globalBuilderNode === null) {
      globalBuilderNode = new BuilderNode(context);
      // Pass the external LocalStorage to be shared by all custom components mounted to the current BuilderNode.
      globalBuilderNode.build(wrapBuilder<[Params]>(buildText), new Params('builder node text'),
        { localStorage: localStorage1 });
    }
    this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    return this.rootNode;
  }
}

// Create LocalStorage and set initial values.
let localStorage1: LocalStorage = new LocalStorage();
localStorage1.setOrCreate('PropA', 'PropA');

@Entry(localStorage1)
@Component
struct Index {
  private controller: TextNodeController = new TextNodeController();
  @LocalStorageLink('PropA') PropA: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.PropA)
        NodeContainer(this.controller)
        Button('changeLocalstorage').onClick(() => {
          localStorage1.set('PropA', 'AfterChange')
        })
      }
    }
  }
}

@Component
struct CustomComp {
  @LocalStorageLink('PropA') PropA: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.PropA)
      }
    }
  }
}
```

### Example 5: Configuring the BuilderNode for Cross-Boundary @Provide-@Consume Communication

Set enableProvideConsumeCrossing in [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) of the BuilderNode to true to implement two-way synchronization between the @Consume decorated variable of the custom component inside the BuilderNode and the @Provide decorated variable outside the BuilderNode.



```TypeScript
import { BuilderNode, NodeContent } from '@kit.ArkUI';

// Custom component
@Component
struct ConsumeChild {
  // Two-way synchronization with the state variable decorated with the @Provider outside the BuilderNode.
  @Consume @Watch('ChangeData') message: string = ''

  ChangeData() {
    console.info(`ChangeData ${this.message}`);
  }

  build() {
    Column() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .fontSize(20)
      Button('Click to change message to append C')
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          // Modify the @Consume decorated variable.
          this.message = this.message + 'C';
        })
    }
  }
}

@Builder
function CreateText(textMessage: string) {
  Column() {
    Text(textMessage)
      .fontWeight(FontWeight.Bold)
      .fontSize(20)
    ConsumeChild()
  }
}

@Entry
@Component
struct Index {
  // Two-way synchronization with the state variable decorated with the @Consumer inside the BuilderNode.
  @Provide message: string = 'Hello World';
  private content: NodeContent = new NodeContent();
  private builderNode: BuilderNode<[string]> = new BuilderNode<[string]>(this.getUIContext());

  aboutToAppear(): void {
    // Set enableProvideConsumeCrossing to true to support two-way synchronization between the @Consume decorated variable of the custom component ConsumeChild inside the BuilderNode and the @Provide decorated variable on the page where the ConsumeChild component is located.
    this.builderNode.build(wrapBuilder(CreateText), 'Test Consume', { enableProvideConsumeCrossing: true });
    this.content.addFrameNode(this.builderNode.getFrameNode());
  }

  aboutToDisappear() {
    this.builderNode?.dispose();
  }

  build() {
    Column() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .fontSize(20)
      Button('Click to change message to append I')
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.message = this.message + 'I';
        })
      Column() {
        ContentSlot(this.content)
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 6: Configuring the BuilderNode for Cross-Boundary @Provider-@Consumer Communication

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

Set enableProvideConsumeCrossing in [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) of the BuilderNode to true to support two-way synchronization between the @Consumer decorated state variable of the custom component inside the BuilderNode and the @Provider decorated state variable outside the BuilderNode.



```TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';

@Builder
function buildText() {
  // @Consumer is mounted under the BuilderNode.
  AddChildChild();
}

class TextNodeControllerAdd extends NodeController {
  builderNode: BuilderNode<[]> | null = null;
  private uiContext: UIContext | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    console.info('TextNodeControllerAdd makeNode');
    this.builderNode = new BuilderNode(context);
    // Build the builderNode and set enableProvideConsumeCrossing to true.
    this.builderNode.build(wrapBuilder<[]>(buildText), undefined, { enableProvideConsumeCrossing: true });
    return this.builderNode.getFrameNode();
  }

  aboutToDisappear() {
    this.builderNode?.dispose();
  }
}

@ComponentV2
struct AddChildChild {
  @Consumer() content: string = 'default value';

  @Monitor('content')
  consumeWatch() {
    console.info(`Consumer change ${this.content}`);
  }

  build() {
    Column() {
      Text(`Test: ${this.content}`);
      Button('change consumer')
        .onClick(() => {
          // Modify the @Consumer decorated variable.
          this.content += ' Consumer';
        })
    }
  }
}

@Entry
@ComponentV2
struct AddChild {
  // Two-way synchronization with the state variable decorated with the @Consumer.
  @Provider() content: string = 'Index: hello world';

  @Monitor('content')
  providerWatch() {
    console.info(`Provider change ${this.content}`);
  }

  controllerIndex: TextNodeControllerAdd = new TextNodeControllerAdd();

  build() {
    Column() {
      Text(`Provider: ${this.content}`)
      Button('change Provider')
        .onClick(() => {
          // Modify the @Provider decorated variable.
          this.content += ' Provider';
        })
      // Connect to the BuilderNode through NodeContainer.
      NodeContainer(this.controllerIndex);
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 7: Synchronization Relationship Changes During BuilderNode Mounting and Unmounting

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates how the synchronization relationship between @Consumer and @Provider changes when a BuilderNode is mounted to or unmounted from the component tree.

```TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';

@Builder
function buildText() {
  TestRemove();
}

let globalBuilderNode: BuilderNode<[]> | null = null;

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.uiContext = context;
    return this.rootNode;
  }

  addBuilderNode(): void {
    if (globalBuilderNode === null && this.uiContext) {
      globalBuilderNode = new BuilderNode(this.uiContext);
      globalBuilderNode.build(wrapBuilder<[]>(buildText), undefined, { enableProvideConsumeCrossing: true });
    }
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    }
  }

  removeBuilderNode(): void {
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.removeChild(globalBuilderNode.getFrameNode());
    }
  }

  disposeNode(): void {
    if (this.rootNode && globalBuilderNode) {
      globalBuilderNode.dispose();
    }
  }
}

@Entry
@ComponentV2
struct RemoChildDisconnectProvider {
  @Provider() content: string = 'Index: hello world';

  @Monitor('content')
  providerWatch() {
    console.info(`Provider change ${this.content}`);
  }

  controllerIndex: TextNodeController = new TextNodeController();

  build() {
    Column({ space: 8 }) {
      Text(`Provider: ${this.content}`)
      Button('add child')
        .onClick(() => {
          this.controllerIndex.addBuilderNode();
        })

      Button('remove child')
        .onClick(() => {
          this.controllerIndex.removeBuilderNode();
        })

      Button('dispose child')
        .onClick(() => {
          this.controllerIndex.disposeNode();
        })

      Button('change Provider')
        .onClick(() => {
          // Modify the @Provider decorated variable.
          this.content += 'Pro';
        })
      NodeContainer(this.controllerIndex);
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct TestRemove {
  @Consumer() content: string = 'default value';

  @Monitor('content')
  consumerWatch() {
    console.info(`Consumer change ${this.content}`);
  }

  aboutToDisappear() {
    console.info(`TestRemove aboutToDisappear`);
  }

  build() {
    Column() {
      Text(`Consumer ${this.content}`)

      Button('change content')
        .onClick(() => {
          // Modify the @Consumer decorated variable.
          this.content += 'content';
        })
    }
  }
}
```

### Example 8: Implementing Synchronization Relationship Changes When BuilderNode Is Mounted to Another Component Tree

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates how the synchronization relationship between @Consumer and @Provider changes when a BuilderNode is mounted to a different component tree.

```TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';

@Builder
function buildText() {
  ConsumerChild();
}

let globalBuilderNode: BuilderNode<[]> | null = null;

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.uiContext = context;
    return this.rootNode;
  }

  addBuilderNode(): void {
    if (globalBuilderNode === null && this.uiContext) {
      globalBuilderNode = new BuilderNode(this.uiContext);
      globalBuilderNode.build(wrapBuilder<[]>(buildText), undefined, { enableProvideConsumeCrossing: true });
    }
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    }
  }

  removeBuilderNode(): void {
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.removeChild(globalBuilderNode.getFrameNode());
    }
  }
}

@Entry
@ComponentV2
struct AddRemoveAddToAnother {
  @Provider() content: string = 'Index: hello world';

  @Monitor('content')
  providerWatch() {
    console.info(`Provider change ${this.content}`);
  }

  aboutToDisappear() {
    globalBuilderNode?.dispose();
  }

  controllerIndex: TextNodeController = new TextNodeController();

  build() {
    Column({ space: 8 }) {
      Text(`Index Provider: ${this.content}`)

      Button('add child')
        .onClick(() => {
          this.controllerIndex.addBuilderNode();
        })

      Button('change Index Provide')
        .onClick(() => {
          // Modify the @Provider decorated variable.
          this.content += 'Pro';
        })

      NodeContainer(this.controllerIndex);
      ChildHasProvide({ controllerIndex: this.controllerIndex });
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct ChildHasProvide {
  @Provider('content') content: string = 'Child: hello world';

  @Monitor('content')
  providerWatch() {
    console.info(`Provider change ${this.content}`);
  }

  @Param private controllerIndex: TextNodeController | undefined = undefined;
  controllerIndexChild: TextNodeController = new TextNodeController();

  build() {
    Column({ space: 8 }) {
      Text(`Child Provider: ${this.content}`)

      Button('change Child Provide')
        .onClick(() => {
          // Modify the @Provider decorated variable.
          this.content += 'Pro';
        })

      Button('change View')
        .onClick(() => {
          this.controllerIndex?.removeBuilderNode();
          this.controllerIndexChild.addBuilderNode();
        })
      NodeContainer(this.controllerIndexChild);
    }
  }
}

@ComponentV2
struct ConsumerChild {
  @Consumer() content: string = 'default value';

  @Monitor('content')
  consumerWatch() {
    console.info(`Consumer change ${this.content}`);
  }

  build() {
    Column() {
      Text(`Consumer: ${this.content}`)

      Button('change content')
        .onClick(() => {
          // Modify the @Consumer decorated variable.
          this.content += 'content';
        })
    }
  }
}
```

### Example 9: Implementing Synchronization Relationship Changes in Nested BuilderNode Scenarios

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates how the synchronization relationship between @Consumer and @Provider changes when BuilderNodes are nested.

```TypeScript
import { BuilderNode, FrameNode, NodeContent, NodeController } from '@kit.ArkUI';

let content: NodeContent = new NodeContent();

@Builder
function buildText() {
  Column() {
    BuildNodeToBuildNodeChild().border({ width: 2, color: Color.Pink, radius: 5 });
    ContentSlot(content);
  }
}

@Builder
function buildText2() {
  Column() {
    BuildNodeToBuildNodeChild().border({ width: 2, color: Color.Pink, radius: 5 });
  }
}

let globalBuilderNode: BuilderNode<[]> | null = null;
let globalBuilderNode2: BuilderNode<[]> | null = null;

class TextNodeControllerAdd extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.uiContext = context;
    // Only FrameNode is returned, and build is not executed.
    return this.rootNode;
  }

  addBuilderNode(): void {
    if (globalBuilderNode === null && this.uiContext) {
      globalBuilderNode = new BuilderNode(this.uiContext);
      globalBuilderNode.build(wrapBuilder<[]>(buildText), undefined, { enableProvideConsumeCrossing: true });
    }
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    }
  }

  removeBuilderNode(): void {
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.removeChild(globalBuilderNode.getFrameNode());
    }
  }
}

@Entry
@ComponentV2
struct BuildNodeToBuildNode {
  @Provider() content: string = 'Index: hello world';

  @Monitor('content')
  providerWatch() {
    console.info(`Provider change ${this.content}`);
  }

  aboutToDisappear() {
    globalBuilderNode?.dispose();
    globalBuilderNode2?.dispose();
  }

  controllerIndex: TextNodeControllerAdd = new TextNodeControllerAdd();

  build() {
    Column({ space: 8 }) {
      Text(`Provider: ${this.content}`)
      Button('add child')
        .onClick(() => {
          this.controllerIndex.addBuilderNode();
        })
      // builderNode is nested in builderNode.
      Button('add to NodeContent')
        .onClick(() => {
          globalBuilderNode2 = new BuilderNode(this.getUIContext());
          globalBuilderNode2.build(wrapBuilder<[]>(buildText2), undefined, { enableProvideConsumeCrossing: true });
          content.addFrameNode(globalBuilderNode2.getFrameNode());
        })
      Button('change Provider')
        .onClick(() => {
          // Modify the @Provider decorated variable.
          this.content += 'Pro';
        })
      NodeContainer(this.controllerIndex);
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct BuildNodeToBuildNodeChild {
  // When not mounted in the tree, the Test component has no parent view, and this node is off-screen. @Consumer cannot find the corresponding @Provider and uses the default value.
  @Consumer() content: string = 'default value';

  @Monitor('content')
  consumerWatch() {
    console.info(`Consumer change ${this.content}`);
  }

  build() {
    Column() {
      Text(`Test: ${this.content}`)

      Button('change content')
        .onClick(() => {
          // Modify the @Consumer decorated variable.
          this.content += 'content';
        })
    }
  }
}
```

### Example 10: Understanding the Synchronization Relationship When @Consumer Components Have Child Components Under BuilderNode

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates the synchronization relationship between @Consumer and @Provider when the custom component containing @Consumer is located under BuilderNode and has child components.

```TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';

@Builder
function buildText() {
  NestedComponentChild();
}

let globalBuilderNode: BuilderNode<[]> | null = null;

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.uiContext = context;
    return this.rootNode;
  }

  addBuilderNode(): void {
    if (globalBuilderNode === null && this.uiContext) {
      globalBuilderNode = new BuilderNode(this.uiContext);
      globalBuilderNode.build(wrapBuilder<[]>(buildText), undefined, { enableProvideConsumeCrossing: true });
    }
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    }
  }

  removeBuilderNode(): void {
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.removeChild(globalBuilderNode.getFrameNode());
    }
  }

  disposeNode(): void {
    if (this.rootNode && globalBuilderNode) {
      globalBuilderNode.dispose();
    }
  }
}

@Entry
@ComponentV2
struct NestedComponent {
  @Provider() content: string = 'Index: hello world';

  @Monitor('content')
  providerWatch() {
    console.info(`Provider change ${this.content}`);
  }

  controllerIndex: TextNodeController = new TextNodeController();

  build() {
    Column({ space: 8 }) {
      Text(`Provider: ${this.content}`)

      Button('add child')
        .onClick(() => {
          this.controllerIndex.addBuilderNode();
        })

      Button('remove child')
        .onClick(() => {
          this.controllerIndex.removeBuilderNode();
        })

      Button('dispose child')
        .onClick(() => {
          this.controllerIndex.disposeNode();
        })

      Button('change Provider')
        .onClick(() => {
          // Modify the @Provider decorated variable.
          this.content += 'Pro';
        })
      NodeContainer(this.controllerIndex);
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct NestedComponentChild {
  @Consumer() content: string = 'default value';

  @Monitor('content')
  consumerWatch() {
    console.info(`Consumer change ${this.content}`);
  }

  aboutToDisappear() {
    console.info(`TestRemove aboutToDisappear`);
  }

  build() {
    Column() {
      Text(`Consumer: ${this.content}`)

      Button('change content')
        .onClick(() => {
          // Modify the @Consumer decorated variable.
          this.content += 'content';
        })
      NestedComponentChildChild({ content: this.content, addContent: () => this.content += 'content' });
    }
  }
}

@ComponentV2
struct NestedComponentChildChild {
  // When not mounted in the tree, the Test component has no parent view, and this node is off-screen. @Consumer cannot find the corresponding @Provider and uses the default value.
  @Param @Require content: string;
  @Event addContent: () => void;

  @Monitor('content')
  paramEventWatch() {
    console.info(`ParamEvent change ${this.content}`);
  }

  build() {
    Column() {
      Text(`Param: ${this.content}`)

      Button('change content')
        .onClick(() => {
          this.addContent();
        })
    }
  }
}
```

### Example 11: Understanding the Synchronization Relationship in the @Provider-@Consumer-BuilderNode-@Consumer Component Tree

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates the synchronization relationship between @Consumer and @Provider in a component tree structured as @Provider-@Consumer-BuilderNode-@Consumer.

```TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';

@ObservedV2
class Ob {
  @Trace a: number = 0;
}

@Builder
function buildText() {
  NestedComponentChild();
}

let globalBuilderNode: BuilderNode<[]> | null = null;

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.uiContext = context;
    return this.rootNode;
  }

  addBuilderNode(): void {
    if (globalBuilderNode === null && this.uiContext) {
      globalBuilderNode = new BuilderNode(this.uiContext);
      globalBuilderNode.build(wrapBuilder<[]>(buildText), undefined, { enableProvideConsumeCrossing: true });
    }
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    }
  }

  removeBuilderNode(): void {
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.removeChild(globalBuilderNode.getFrameNode());
    }
  }

  disposeNode(): void {
    if (this.rootNode && globalBuilderNode) {
      globalBuilderNode.dispose();
    }
  }
}

@Entry
@ComponentV2
  // Two-way synchronization with the state variable decorated with the @Consumer.
struct ProvideConsumeBuilderNodeConsume {
  @Provider() content: Ob = new Ob();

  @Monitor('content')
  providerWatch() {
    console.info(`Provider change ${this.content.a}`);
  }

  build() {
    Column({ space: 8 }) {
      Text(`Provide: ${this.content.a}`)

      Button('Change Provider a')
        .onClick(() => {
          this.content.a++;
        })
      Button('Change Provider Whole')
        .onClick(() => {
          this.content.a = 0;
        })
      ProvideConsumeBuilderNodeConsumeChild();
    }
    .width('100%')
    .height('100%')
  }
}

// The component tree is in the @Provider-@Consumer-BuilderNode-@Consumer structure.
@ComponentV2
struct ProvideConsumeBuilderNodeConsumeChild {
  @Consumer() content: Ob = new Ob();

  @Monitor('content')
  consumerWatch() {
    console.info(`ProvideConsumeBuilderNodeConsumeChild change ${this.content.a}`);
  }

  controllerIndex: TextNodeController = new TextNodeController();

  build() {
    Column({ space: 8 }) {
      Text(`Consumer: ${this.content.a}`)
      Button('add child')
        .onClick(() => {
          this.controllerIndex.addBuilderNode();
        })

      Button('remove child')
        .onClick(() => {
          this.controllerIndex.removeBuilderNode();
        })

      Button('dispose child')
        .onClick(() => {
          this.controllerIndex.disposeNode();
        })

      Button('change consumer a')
        .onClick(() => {
          this.content.a++;
        })
      Button('change consumer whole')
        .onClick(() => {
          this.content.a = 0;
        })
      NodeContainer(this.controllerIndex);
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct NestedComponentChild {
  @Consumer() content: Ob = new Ob();

  @Monitor('content')
  consumer1Watch() {
    console.info(`Consumer change ${this.content.a}`);
  }

  aboutToDisappear() {
    console.info(`TestRemove aboutToDisappear`);
  }

  build() {
    Column({ space: 8 }) {
      Text(`Consumer under builder node: ${this.content.a}`)

      Button('Consumer change content')
        .onClick(() => {
          this.content.a++;
        })
    }
  }
}
```

### Example 12: Understanding the Synchronization Relationship in the @Provider-BuilderNode-@Provider-@Consumer Component Tree

> NOTE
> 
> Since API version 23, cross-BuilderNode pairing of @Provider and @Consumer is supported.

This example demonstrates the synchronization relationship between @Consumer and @Provider in a component tree structured as @Provider-BuilderNode-@Provider-@Consumer.

```TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';

@ObservedV2
class Ob {
  @Trace a: number = 0;
}

@Builder
function buildText() {
  Provider2();
}

let globalBuilderNode: BuilderNode<[]> | null = null;

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.uiContext = context;
    return this.rootNode;
  }

  addBuilderNode(): void {
    if (globalBuilderNode === null && this.uiContext) {
      globalBuilderNode = new BuilderNode(this.uiContext);
      globalBuilderNode.build(wrapBuilder<[]>(buildText), undefined, { enableProvideConsumeCrossing: true });
    }
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    }
  }

  removeBuilderNode(): void {
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.removeChild(globalBuilderNode.getFrameNode());
    }
  }

  disposeNode(): void {
    if (this.rootNode && globalBuilderNode) {
      globalBuilderNode.dispose();
    }
  }
}

// The component tree is in the @Provider-BuilderNode-@Provider-@Consumer structure.
@Entry
@ComponentV2
struct Provider1 {
  // Two-way synchronization with the state variable decorated with the @Consumer.
  @Provider() content: Ob = new Ob();

  @Monitor('content')
  providerWatch() {
    console.info(`Provider change ${this.content.a}`);
  }

  controllerIndex: TextNodeController = new TextNodeController();

  build() {
    Column({ space: 8 }) {
      Text(`Provider1: ${this.content.a}`)

      Button('Change Provider1 a')
        .onClick(() => {
          this.content.a++;
        })
      Button('Change Provider1 Whole')
        .onClick(() => {
          this.content.a = 0;
        })
      Button('add child')
        .onClick(() => {
          this.controllerIndex.addBuilderNode();
        })

      Button('remove child')
        .onClick(() => {
          this.controllerIndex.removeBuilderNode();
        })

      Button('dispose child')
        .onClick(() => {
          this.controllerIndex.disposeNode();
        })
      NodeContainer(this.controllerIndex);
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct Provider2 {
  @Provider() content: Ob = new Ob();

  @Monitor('content')
  consumerWatch() {
    console.info(`Provider2 change ${this.content.a}`);
  }

  controllerIndex: TextNodeController = new TextNodeController();

  build() {
    Column() {
      Text(`Provider2: ${this.content.a}`)

      Button('change Provider2 a')
        .onClick(() => {
          this.content.a++;
        })
      Button('change Provider2 whole')
        .onClick(() => {
          this.content.a = 0;
        })
      DefaultConsumer();
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct DefaultConsumer {
  @Consumer() content: Ob = new Ob();

  @Monitor('content')
  consumer1Watch() {
    console.info(`Consumer change ${this.content.a}`);
  }

  aboutToDisappear() {
    console.info(`TestRemove aboutToDisappear`);
  }

  build() {
    Column() {
      Text(`Consumer under builder node:: ${this.content.a}`)

      Button('Consumer change ++')
        .onClick(() => {
          this.content.a++;
        })
    }
  }
}
```

### Example 13: Handling Mouse Events in ReactiveBuilderNode

The functionality demonstrated in this example is supported starting from API version 22.

This example demonstrates the end-to-end process for intercepting mouse events in a custom component and performing coordinate conversion. The component reads the local X and Y coordinates through the [onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse) callback, calls [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the relative coordinates to pixel coordinates based on the offset obtained by FrameNode.getPositionToParent(), and updates windowX, windowY, displayX, and displayY of [MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent). Finally, the component uses rootNode.postInputEvent to post the converted mouse event to the child node for handling.



```TypeScript
import { NodeController, ReactiveBuilderNode, FrameNode, PromptAction, UIContext, InputEventType } from '@kit.ArkUI';

@Builder
function ButtonBuilder(text: string, uiContext: UIContext) {
  Column() {
    Button(text)
      .borderWidth(2)
      .align(Alignment.Center)
      .backgroundColor(Color.Orange)
      .fontSize(15)
      .width('45%')
      .height('30%')
      .offset({ y: 70 })
      // Handle the mouse event.
      .onMouse((event) => {
        let promptAction: PromptAction = uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onMouse',
          duration: 3000
        });
        console.info('onMouse');
      })
      // Handle the touch event.
      .onTouch((event) => {
        let promptAction: PromptAction = uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onTouch',
          duration: 3000
        });
        console.info('onTouch');
      })
  }
  .width(500)
  .height(200)
  .backgroundColor(Color.Gray)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: ReactiveBuilderNode<[text: string, uiContext: UIContext]> | null = null;
  private wrapBuilder: WrappedBuilder<[text: string, uiContext: UIContext]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new ReactiveBuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, {}, 'onMouse', uiContext);
    return this.rootNode.getFrameNode();
  }

  postMouseEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    let node: FrameNode | null = this.rootNode.getFrameNode();
    // Obtain the offset of the node relative to the parent component.
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let mouseEvent = event as MouseEvent;
    // Coordinate conversion: Convert the event coordinates to the node coordinates.
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      mouseEvent.windowX = uiContext.vp2px(offsetX + mouseEvent.x);
      mouseEvent.windowY = uiContext.vp2px(offsetY + mouseEvent.y);
    }
    // Call postInputEvent to post the converted event to the ReactiveBuilderNode.
    let result = this.rootNode.postInputEvent(event);
    return result;
  }

  // Handle the touch event.
  postTouchEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    let node: FrameNode | null = this.rootNode.getFrameNode();
    // Obtain the offset of the node relative to the parent component.
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let touchEvent = event as TouchEvent;
    // Convert the coordinates of all touch points in the changedTouches array.
    let changedTouchLen = touchEvent.changedTouches.length;
    for (let i = 0; i < changedTouchLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
        touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
      }
    }
    // Convert the coordinates of all touch points in the touches array.
    let touchesLen = touchEvent.touches.length;
    for (let i = 0; i < touchesLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
        touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
      }
    }
    // Call postInputEvent to post the converted event to the ReactiveBuilderNode.
    let result = this.rootNode.postInputEvent(event);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Stack() {
      NodeContainer(this.nodeController)
        .height(300)
        .width(500)
      Column()
        .width(500)
        .height(300)
        .margin({ top: 500 })
        .backgroundColor(Color.Transparent)
        // Capture the mouse event and post it to the custom node.
        .onMouse((event) => {
          if (event != undefined) {
            this.nodeController.postMouseEvent(event, this.getUIContext());
          }
        })
        // Capture the touch event and post it to the custom node.
        .onTouch((event) => {
          if (event != undefined) {
            this.nodeController.postTouchEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 180 })
  }
}
```

### Example 14: Handling Touch Events in ReactiveBuilderNode

The functionality demonstrated in this example is supported starting from API version 22.

This example demonstrates the end-to-end process for intercepting touch events in a custom component and transforming touch point coordinates. In the [onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch) callback, iterate through the changedTouches and touches arrays of [TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent), add the component offset to the X and Y coordinates of each touch point, call [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the coordinates to pixels, and update windowX/windowY and displayX/displayY. Finally, rootNode.postInputEvent is used to post the converted touch event to the child node for handling.



```TypeScript
import { NodeController, ReactiveBuilderNode, FrameNode, UIContext, PromptAction, InputEventType } from '@kit.ArkUI';

@Builder
function ButtonBuilder(text: string, uiContext: UIContext) {
  Column() {
    Button(text)
      .borderWidth(2)
      .align(Alignment.Center)
      .backgroundColor(Color.Orange)
      .fontSize(15)
      .width('45%')
      .height('30%')
      .offset({ y: 70 })
      // Handle the touch event.
      .onTouch((event) => {
        let promptAction: PromptAction = uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onTouch',
          duration: 3000
        });
        console.info('onTouch');
      })
  }
  .width(500)
  .height(200)
  .backgroundColor(Color.Gray)
}

class MyNodeController extends NodeController {
  private rootNode: ReactiveBuilderNode<[text: string, uiContext: UIContext]> | null = null;
  private wrapBuilder: WrappedBuilder<[text: string, uiContext: UIContext]> =
    wrapBuilder<[text: string, uiContext: UIContext]>(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new ReactiveBuilderNode(uiContext);
    // Build the ReactiveBuilderNode and transfer the button text and UI context.
    this.rootNode.build(this.wrapBuilder, {}, 'onTouch', uiContext);
    return this.rootNode.getFrameNode();
  }

  postInputEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    let node: FrameNode | null = this.rootNode.getFrameNode();
    // Obtain the offset of the node relative to the parent component.
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    if (event.source == SourceType.TouchScreen) {
      let touchEvent = event as TouchEvent;
      // Convert the coordinates of all touch points in the changedTouches array.
      let changedTouchLen = touchEvent.changedTouches.length;
      for (let i = 0; i < changedTouchLen; i++) {
        if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
          touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
          touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
        }
      }
      // Convert the coordinates of all touch points in the touches array.
      let touchesLen = touchEvent.touches.length;
      for (let i = 0; i < touchesLen; i++) {
        if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
          touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
          touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
        }
      }
    }

    // Call postInputEvent to post the converted event to the ReactiveBuilderNode.
    let result = this.rootNode.postInputEvent(event);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Stack() {
      NodeContainer(this.nodeController)
        .height(300)
        .width(500)
      Column()
        .width(500)
        .height(300)
        .margin({ top: 600 })
        .backgroundColor(Color.Transparent)
        // Capture the touch event and post it to the custom node.
        .onTouch((event) => {
          if (event != undefined) {
            this.nodeController.postInputEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 180 })
  }
}
```

### Example 15: Handling Axis Events in ReactiveBuilderNode

The functionality demonstrated in this example is supported starting from API version 22.

This example demonstrates the end-to-end process for intercepting wheel or trackpad axis events in a custom component and performing coordinate conversion. In the [onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent) callback, obtain the relative X and Y coordinates of the axis event, add the component offset, call [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the coordinates to pixels, update the windowX/windowY and displayX/displayY of the axis event, and use rootNode.postInputEvent to post the converted axis event to the child node for handling.



```TypeScript
import { NodeController, ReactiveBuilderNode, FrameNode, UIContext, PromptAction, InputEventType } from '@kit.ArkUI';

@Builder
function ButtonBuilder(text: string, uiContext: UIContext) {
  Column() {
    Button(text)
      .borderWidth(2)
      .align(Alignment.Center)
      .backgroundColor(Color.Orange)
      .fontSize(15)
      .width('45%')
      .height('30%')
      .offset({ y: 80 })
      .onAxisEvent((event) => {
        let promptAction: PromptAction = uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onAxisEvent', // Display the message when the axis event is triggered.
          duration: 3000
        });
        console.info('onAxisEvent');
      })
  }
  .width(500)
  .height(200)
  .backgroundColor(Color.Gray)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: ReactiveBuilderNode<[text: string, uiContext: UIContext]> | null = null;
  private wrapBuilder: WrappedBuilder<[text: string, uiContext: UIContext]> =
    wrapBuilder<[text: string, uiContext: UIContext]>(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new ReactiveBuilderNode(uiContext);
    // Build the ReactiveBuilderNode and transfer the button text and UI context.
    this.rootNode.build(this.wrapBuilder, {}, 'onAxisEvent', uiContext);
    return this.rootNode.getFrameNode();
  }

  // Handle the axis event.
  postInputEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of buildNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let axisEvent = event as AxisEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      axisEvent.windowX = uiContext.vp2px(offsetX + axisEvent.x);
      axisEvent.windowY = uiContext.vp2px(offsetY + axisEvent.y);
    }
    // Call postInputEvent to post the converted event to the ReactiveBuilderNode.
    let result = this.rootNode.postInputEvent(event);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Stack() {
      NodeContainer(this.nodeController)
        .height(300)
        .width(500)
      Column()
        .width(500)
        .height(300)
        .margin({ top: 600 })
        .backgroundColor(Color.Transparent)
        // Capture the axis event and post it to the custom node.
        .onAxisEvent((event) => {
          if (event != undefined) {
            // Call the axis event handling method.
            this.nodeController.postInputEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 180 })
  }
}
```

### Example 16: Handling Mouse Events with Competition Strategies in BuilderNode

The postInputEventWithStrategy API is added since API version 24.

This example demonstrates the end-to-end process for intercepting mouse events in a custom component and performing coordinate conversion. The component reads the current touch point coordinates (x/y) through the [onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse) callback, and calls [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the relative coordinates to pixel coordinates based on the offset obtained from FrameNode.getPositionToParent. It then updates windowX, windowY, displayX, and displayY of [MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent). The component selects a [gesture competition strategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24), and posts the converted mouse event to child nodes through rootNode.postInputEventWithStrategy for processing.

```TypeScript
import { NodeController, BuilderNode, FrameNode, PromptAction, UIContext, InputEventType } from '@kit.ArkUI';

// Define the class for passing parameters.
class Params {
  text: string = 'this is a text';
  uiContext: UIContext | null = null;
}

@Component
struct NodeLayer22 {
  private nodeController2: MyNodeController2 = new MyNodeController2();
  build() {
    Row() {
      Stack() {
        NodeContainer(this.nodeController2)
          .height(400)
          .width(500)
        Column()
          .width(500)
          .height(400)
          .backgroundColor(Color.Transparent)
          .onMouse((event) => {
            if (event != undefined) {
              this.nodeController2.postMouseEvent(event, this.getUIContext(), CompetitionStrategy.COMPETITION);
            }
          })
      }.offset({ top: 100 })
    }
  }
}

@Component
struct NodeLayer33 {
  private nodeController3: MyNodeController3 = new MyNodeController3();
  build() {
    Row() {
      Stack() {
        NodeContainer(this.nodeController3)
          .height(200)
          .width(500)
        Column()
          .width(500)
          .height(200)
          .backgroundColor(Color.Transparent)
          .onMouse((event) => {
            if (event != undefined) {
              this.nodeController3.postMouseEvent(event, this.getUIContext(), CompetitionStrategy.COMPETITION);
            }
          })
      }.offset({ top: 100 })
    }
  }
}

@Builder
function ButtonBuilder(params: Params) {
  Column() {
    Button('Layer1')
      .width('100%')
      .height(100)
    NodeLayer22()

  }
  .width(500)
  .height(600)
  .backgroundColor(Color.Gray)
}

@Builder
function ButtonBuilder2(params: Params) {
  Column() {
    Button('Layer2')
      .width('100%')
      .height(100)
    NodeLayer33()
  }
  .width(500)
  .height(400)
  .backgroundColor(Color.Gray)
}

@Builder
function ButtonBuilder3(params: Params) {
  Column() {
    Button('Layer3')
      .width('100%')
      .height(50)
      .gesture(
        TapGesture()
          .tag('TapGesture')
          .onAction((event:GestureEvent) => {
            params.uiContext?.showAlertDialog(
              {
                title: 'onTapGestureLayer3',
                message: ''
              }
            );
          })
      )
  }
  .width(500)
  .height(200)
  .backgroundColor(Color.Gray)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postMouseEvent(event: InputEventType, uiContext: UIContext, competitionStrategy:CompetitionStrategy|undefined|null): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of BuilderNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let mouseEvent = event as MouseEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      mouseEvent.windowX = uiContext.vp2px(offsetX + mouseEvent.x);
      mouseEvent.windowY = uiContext.vp2px(offsetY + mouseEvent.y);
      mouseEvent.rawDeltaX = uiContext.vp2px(mouseEvent.rawDeltaX);
      mouseEvent.rawDeltaY = uiContext.vp2px(mouseEvent.rawDeltaY);
    }
    // Post the mouse event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEventWithStrategy(event, competitionStrategy);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

class MyNodeController2 extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder2);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postMouseEvent(event: InputEventType, uiContext: UIContext, competitionStrategy:CompetitionStrategy|undefined|null): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of BuilderNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let mouseEvent = event as MouseEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      mouseEvent.windowX = uiContext.vp2px(offsetX + mouseEvent.x);
      mouseEvent.windowY = uiContext.vp2px(offsetY + mouseEvent.y);
      mouseEvent.rawDeltaX = uiContext.vp2px(mouseEvent.rawDeltaX);
      mouseEvent.rawDeltaY = uiContext.vp2px(mouseEvent.rawDeltaY);
    }
    // Post the mouse event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEventWithStrategy(event, competitionStrategy);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

class MyNodeController3 extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder3);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postMouseEvent(event: InputEventType, uiContext: UIContext, competitionStrategy:CompetitionStrategy|undefined|null): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of BuilderNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;
    let mouseEvent = event as MouseEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      mouseEvent.windowX = uiContext.vp2px(offsetX + mouseEvent.x);
      mouseEvent.windowY = uiContext.vp2px(offsetY + mouseEvent.y);
      mouseEvent.rawDeltaX = uiContext.vp2px(mouseEvent.rawDeltaX);
      mouseEvent.rawDeltaY = uiContext.vp2px(mouseEvent.rawDeltaY);
    }
    // Post the mouse event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEventWithStrategy(event, competitionStrategy);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();
  build() {
    Row() {
      Stack() {
        NodeContainer(this.nodeController)
          .height(600)
          .width(500)
        Column()
          .width(500)
          .height(600)
          .backgroundColor(Color.Transparent)
          .onMouse((event) => {
            if (event != undefined) {
              this.nodeController.postMouseEvent(event, this.getUIContext(), CompetitionStrategy.COMPETITION);
            }
          })
          .gesture(
            TapGesture()
              .tag('TapGesture')
              .onAction((event:GestureEvent) => {
                let promptAction: PromptAction = this.getUIContext()!.getPromptAction();
                promptAction.showToast({
                  message: 'onTapGestureOut',
                  duration: 10000
                });
              })
          )
      }.offset({ top: 100 })
    }
  }
}
```

### Example 17: Handling Touch Events with Competition Strategies in BuilderNode

The postInputEventWithStrategy API is added since API version 24.

This example demonstrates the end-to-end process for intercepting touch events in a custom component and transforming touch point coordinates. In the [onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch) callback, traverse the changedTouches and touches arrays of [TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent), add the component offset to the X and Y coordinates of each touch point, call [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the coordinates to pixels, and update windowX, windowY, displayX, and displayY of each touch point. Select a [gesture competition strategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24), and post the converted touch event to child nodes through rootNode.postInputEventWithStrategy for processing.

```TypeScript
import { NodeController, BuilderNode, FrameNode, PromptAction, UIContext, InputEventType } from '@kit.ArkUI';

// Define the class for passing parameters.
class Params {
  text: string = 'this is a text';
  uiContext: UIContext | null = null;
}

@Component
struct NodeLayer22 {
  private nodeController2: MyNodeController2 = new MyNodeController2();
  build() {
    Row() {
      Stack() {
        NodeContainer(this.nodeController2)
          .height(400)
          .width(500)
        Column()
          .width(500)
          .height(400)
          .backgroundColor(Color.Transparent)
          .onTouch((event) => {
            if (event != undefined) {
              if (event.sourceTool != SourceTool.MOUSE) {
                this.nodeController2.postTouchEvent(event, this.getUIContext(), CompetitionStrategy.DEFAULT);
              }
            }
          })
      }.offset({ top: 100 })
    }
  }
}

@Component
struct NodeLayer33 {
  private nodeController3: MyNodeController3 = new MyNodeController3();
  build() {
    Row() {
      Stack() {
        NodeContainer(this.nodeController3)
          .height(200)
          .width(500)
        Column()
          .width(500)
          .height(200)
          .backgroundColor(Color.Transparent)
          .onTouch((event) => {
            if (event != undefined) {
              if (event.sourceTool != SourceTool.MOUSE) {
                this.nodeController3.postTouchEvent(event, this.getUIContext(), CompetitionStrategy.DEFAULT);
              }
            }
          })
      }.offset({ top: 100 })
    }
  }
}

@Builder
function ButtonBuilder(params: Params) {
  Column() {
    Button('Layer1')
      .width('100%')
      .height(100)
    NodeLayer22()

  }
  .width(500)
  .height(600)
  .backgroundColor(Color.Gray)
}

@Builder
function ButtonBuilder2(params: Params) {
  Column() {
    Button('Layer2')
      .width('100%')
      .height(100)
    NodeLayer33()
  }
  .width(500)
  .height(400)
  .backgroundColor(Color.Gray)
}

@Builder
function ButtonBuilder3(params: Params) {
  Column() {
    Button('Layer3')
      .width('100%')
      .height(50)
      .gesture(
        TapGesture()
          .tag('TapGesture')
          .onAction((event:GestureEvent) => {
            params.uiContext?.showAlertDialog(
              {
                title: 'onTapGestureLayer3',
                message: ''
              }
            );
          })
      )
  }
  .width(500)
  .height(200)
  .backgroundColor(Color.Gray)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postTouchEvent(event: InputEventType, uiContext: UIContext, competitionStrategy:CompetitionStrategy|undefined|null): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of BuilderNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let touchEvent = event as TouchEvent;
    let changedTouchLen = touchEvent.changedTouches.length;
    for (let i = 0; i < changedTouchLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
        touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
      }
    }
    let touchesLen = touchEvent.touches.length;
    for (let i = 0; i < touchesLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
        touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
      }
    }
    // Post the touch event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEventWithStrategy(event, competitionStrategy);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

class MyNodeController2 extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder2);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postTouchEvent(event: InputEventType, uiContext: UIContext, competitionStrategy:CompetitionStrategy|undefined|null): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of BuilderNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let touchEvent = event as TouchEvent;
    let changedTouchLen = touchEvent.changedTouches.length;
    for (let i = 0; i < changedTouchLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
        touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
      }
    }
    let touchesLen = touchEvent.touches.length;
    for (let i = 0; i < touchesLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
        touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
      }
    }
    // Post the touch event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEventWithStrategy(event, competitionStrategy);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

class MyNodeController3 extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder3);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postTouchEvent(event: InputEventType, uiContext: UIContext, competitionStrategy:CompetitionStrategy|undefined|null): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of BuilderNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let touchEvent = event as TouchEvent;
    let changedTouchLen = touchEvent.changedTouches.length;
    for (let i = 0; i < changedTouchLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
        touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
      }
    }
    let touchesLen = touchEvent.touches.length;
    for (let i = 0; i < touchesLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
        touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
      }
    }
    // Post the touch event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEventWithStrategy(event, competitionStrategy);
    return result;
  }
  
  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();
  build() {
    Row() {
      Stack() {
        NodeContainer(this.nodeController)
          .height(600)
          .width(500)
        Column()
          .width(500)
          .height(600)
          .backgroundColor(Color.Transparent)
          .onTouch((event) => {
            if (event != undefined) {
              if (event.sourceTool != SourceTool.MOUSE) {
                this.nodeController.postTouchEvent(event, this.getUIContext(), CompetitionStrategy.DEFAULT);
              }
            }
          })
          .gesture(
            TapGesture()
              .tag('TapGesture')
              .onAction((event:GestureEvent) => {
                let promptAction: PromptAction = this.getUIContext()!.getPromptAction();
                promptAction.showToast({
                  message: 'onTapGestureOut',
                  duration: 1000
                });
              })
          )
      }.offset({ top: 100 })
    }
  }
}
```

### Example 18: Handling Axis Events with Competition Strategies in BuilderNode

The postInputEventWithStrategy API is added since API version 24.

This example demonstrates the end-to-end process for intercepting wheel or trackpad axis events in a custom component and performing coordinate conversion. In the [onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent) callback, obtain the relative X and Y coordinates of the event, add the component offset to the coordinates, call [vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12) to convert the coordinates to pixel coordinates, update windowX, windowY, displayX, and displayY of AxisEvent, select [a gesture competition strategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24), and use rootNode.postInputEventWithStrategy to post the converted axis event to child nodes for processing.

```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext, PromptAction, InputEventType } from '@kit.ArkUI';

// Define the class for passing parameters.
class Params {
  text: string = 'this is a text';
  uiContext: UIContext | null = null;
}

@Builder
function ButtonBuilder(params: Params) {
  Column() {
    Button(params.text)
      .borderWidth(2)
      .align(Alignment.Center)
      .backgroundColor(Color.Orange)
      .fontSize(20)
      .width('45%')
      .height('30%')
      .offset({ x: 60, y: 100 })
      .borderRadius('50%')
      .onAxisEvent((event) => {
        let promptAction: PromptAction = params.uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onAxisEvent',
          duration: 3000
        });
        console.info('onAxisEvent');
      })
  }
  .width(500)
  .height(300)
  .backgroundColor(Color.Gray)
}

// Implement a custom UI controller by extending NodeController.
class MyNodeController extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'This is a string', uiContext });
    return this.rootNode.getFrameNode();
  }

  postInputEvent(event: InputEventType, uiContext: UIContext, competitionStrategy: CompetitionStrategy): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // Read the x and y offsets of BuilderNode relative to its parent component and convert them to pixel coordinates.
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let axisEvent = event as AxisEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      axisEvent.windowX = uiContext.vp2px(offsetX + axisEvent.x);
      axisEvent.windowY = uiContext.vp2px(offsetY + axisEvent.y);
    }
    // Post the axis event to the FrameNode created by BuilderNode. result indicates whether the post is successful.
    let result = this.rootNode.postInputEventWithStrategy(event, competitionStrategy);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Stack() {
      NodeContainer(this.nodeController)
        .height(300)
        .width(500)
      Column()
        .width(500)
        .height(300)
        .backgroundColor(Color.Transparent)
        .onAxisEvent((event) => {
          if (event != undefined) {
            this.nodeController.postInputEvent(event, this.getUIContext(), CompetitionStrategy.DEFAULT);
          }
        })
    }.offset({ top: 100 })
  }
}
```
