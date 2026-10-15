# BuilderNode

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BuilderNode](arkts-arkui-buildernode-c.md) | 提供能够挂载系统组件的自定义节点BuilderNode。BuilderNode仅可作为叶子节点使用，支持通过@Builder生成组件树、实现组件复用与回收、跨节点事件分发以及状态同步，适用于在应用内动态创建和管理自定义组件节点的场景。使用方式参考[BuilderNode开发指南](../../../ui/arkts-user-defined-arktsNode-builderNode.md)。 |
| [ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md) | ReactiveBuilderNode支持通过无状态的UI方法[@Builder](../../../ui/state-management/arkts-builder.md)生成组件树，并持有该组件树的根节点，不支持定义为状态变量。ReactiveBuilderNode中持有的[FrameNode](arkts-arkui-typenode-n.md)仅用于将此ReactiveBuilderNode作为子节点挂载到其他FrameNode上。对ReactiveBuilderNode持有的FrameNode进行属性设置与子节点操作可能会导致未定义行为，因此不建议通过ReactiveBuilderNode的[getFrameNode](arkts-arkui-buildernode-c.md#getframenode)方法和[FrameNode](arkts-arkui-typenode-n.md)节点的[getRenderNode](arkts-arkui-framenode-c.md#getrendernode)方法获取RenderNode，并通过[RenderNode](arkts-arkui-rendernode-c.md)的接口对其进行属性设置与子节点操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | build的可选参数。 |
| [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 创建BuilderNode时的可选参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InputEventType](arkts-arkui-inputeventtype-t.md) | [postInputEvent](arkts-arkui-buildernode-c.md#postinputevent)的参数，定义要发送的输入事件类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | 节点渲染类型枚举。 |

## 示例

### 示例1（BuilderNode中鼠标事件）

该示例演示了在自定义组件中截获鼠标事件并进行坐标转换的完整流程。组件通过[onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse)回调读取本地x/y，再结合FrameNode.getPositionToParent()得到的偏移量，调用vp2px将相对坐标转换为像素坐标，更新[MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)的windowX/windowY、displayX/displayY。最后通过rootNode.postInputEvent(event)将转换后的鼠标事件分发给子节点进行处理。



```TypeScript
import { NodeController, BuilderNode, FrameNode, PromptAction, UIContext, InputEventType } from '@kit.ArkUI';

// 自定义参数传递的类
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

// 继承NodeController实现自定义UI控制器
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
    // 读取本地x、y与buildNode相对于父组件的偏移量，转换为像素坐标
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let mouseEvent = event as MouseEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      mouseEvent.windowX = uiContext.vp2px(offsetX + mouseEvent.x);
      mouseEvent.windowY = uiContext.vp2px(offsetY + mouseEvent.y);
    }
    // 将鼠标事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
    let result = this.rootNode.postInputEvent(event);
    return result;
  }

  postTouchEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // 读取本地x、y与buildNode相对于父组件的偏移量，转换为像素坐标
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
    // 将触摸事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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

### 示例2（BuilderNode中触摸事件）

该示例演示了在自定义组件中截获触摸事件并对触点坐标进行转换的完整流程。在[onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch)回调中，遍历[TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent对象说明)的changedTouches和touches数组，对每个触点的x/y加上组件偏移量并调用vp2px转换为像素，更新各自的windowX/windowY、displayX/displayY。最后同样通过rootNode.postInputEvent(event)将转换后的触摸事件分发给子节点处理。



```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext, PromptAction, InputEventType } from '@kit.ArkUI';

// 自定义传递参数的类
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

// 继承NodeController实现自定义UI控制器
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
    // 读取本地x、y与buildNode相对于父组件的偏移量，转换为像素坐标
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    // 只转发原始事件，不转发鼠标模拟的触摸事件
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

    // 将触摸事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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

### 示例3（BuilderNode中轴事件）

该示例演示了在自定义组件中截获滚轮或触控板轴事件并进行坐标转换的完整流程。在[onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent)回调中，先获取事件的相对x/y，再加上组件偏移量后调用vp2px转换为像素，更新AxisEvent的windowX/windowY、displayX/displayY，最后通过rootNode.postInputEvent(event)将转换后的轴事件分发给子节点进行处理。



```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext, PromptAction, InputEventType } from '@kit.ArkUI';

// 自定义传递参数的类
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

// 继承NodeController实现自定义UI控制器
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
    // 读取本地x、y与buildNode相对于父组件的偏移量，转换为像素坐标
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let axisEvent = event as AxisEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      axisEvent.windowX = uiContext.vp2px(offsetX + axisEvent.x);
      axisEvent.windowY = uiContext.vp2px(offsetY + axisEvent.y);
    }
    // 将轴事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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

### 示例4（BuilderNode共享localStorage）

该示例演示了如何通过BuilderNode的build方法传入外部[localStorage](../arkui-ts/ts-state-management.md#localstorage9)，此时挂载在BuilderNode的所有自定义组件共享该localStorage。

```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

// 自定义传递参数的类
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

// 继承NodeController实现自定义textNode控制器
class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    if (globalBuilderNode === null) {
      globalBuilderNode = new BuilderNode(context);
      // 传入外部localStorage，共享给挂载在当前BuilderNode的所有自定义组件
      globalBuilderNode.build(wrapBuilder<[Params]>(buildText), new Params('builder node text'),
        { localStorage: localStorage1 });
    }
    this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    return this.rootNode;
  }
}

// 创建LocalStorage并设置初始值
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

### 示例5（BuilderNode支持内部@Consume接收外部的@Provide数据）

设置BuilderNode的[BuildOptions](arkts-arkui-buildernode-buildoptions-i.md)中enableProvideConsumeCrossing为true，以实现BuilderNode内部自定义组件的@Consume与所在自定义组件的@Provide双向同步。



```TypeScript
import { BuilderNode, NodeContent } from '@kit.ArkUI';

// 自定义组件
@Component
struct ConsumeChild {
  // 与外部的@Provide装饰的状态变量双向同步
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
          // 修改Consume的变量
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
  // 与内部的@Consume装饰的状态变量双向同步
  @Provide message: string = 'Hello World';
  private content: NodeContent = new NodeContent();
  private builderNode: BuilderNode<[string]> = new BuilderNode<[string]>(this.getUIContext());

  aboutToAppear(): void {
    // 设置enableProvideConsumeCrossing为true，支持BuilderNode内部自定义组件ConsumeChild的@Consume变量与其所在页面中的@Provide变量双向同步
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

### 示例6（BuilderNode支持内部@Consumer接收外部的@Provider数据）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

设置BuilderNode的[BuildOptions](arkts-arkui-buildernode-buildoptions-i.md)中enableProvideConsumeCrossing为true，以实现BuilderNode内部自定义组件的@Consumer变量与所在自定义组件的@Provider装饰的状态变量双向同步。



```TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';

@Builder
function buildText() {
  // @Consumer挂载在BuilderNode下
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
    // 构建builderNode，enableProvideConsumeCrossing设置为true
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
          // 修改@Consumer的变量
          this.content += ' Consumer';
        })
    }
  }
}

@Entry
@ComponentV2
struct AddChild {
  // 与@Consumer装饰的状态变量双向同步
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
          // 修改@Provider的变量
          this.content += ' Provider';
        })
      // 通过NodeContainer连接BuilderNode节点
      NodeContainer(this.controllerIndex);
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例7（BuilderNode上下树时的同步关系变化）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了BuilderNode挂载到组件树和从组件树卸载时，@Consumer与@Provider的同步关系变化。

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
          // 修改@Provider的变量
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
          // 修改@Consumer的变量
          this.content += 'content';
        })
    }
  }
}
```

### 示例8（BuilderNode上树后再上另一棵树时的同步关系变化）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了BuilderNode挂载到组件树后，再挂载到另一个组件树时，@Consumer与@Provider的同步关系变化。

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
          // 修改@Provider的变量
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
          // 修改@Provider的变量
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
          // 修改@Consumer的变量
          this.content += 'content';
        })
    }
  }
}
```

### 示例9（BuilderNode互相嵌套的场景下的同步关系变化）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了BuilderNode互相嵌套场景下@Consumer和@Provider的同步关系变化。

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
    // 仅返回FrameNode，未执行build
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
      // builderNode嵌套builderNode
      Button('add to NodeContent')
        .onClick(() => {
          globalBuilderNode2 = new BuilderNode(this.getUIContext());
          globalBuilderNode2.build(wrapBuilder<[]>(buildText2), undefined, { enableProvideConsumeCrossing: true });
          content.addFrameNode(globalBuilderNode2.getFrameNode());
        })
      Button('change Provider')
        .onClick(() => {
          // 修改@Provider的变量
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
  // 在未上树的时候，Test组件无View的父亲，该节点为离屏节点。@Consumer找不到对应@Provider，使用默认值
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
          // 修改@Consumer的变量
          this.content += 'content';
        })
    }
  }
}
```

### 示例10（BuilderNode下的@Consumer所在组件还有其他子组件时的同步关系）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了当@Consumer所在的自定义组件在BuilderNode下且该自定义组件存在子组件时，@Consumer和@Provider之间的同步关系。

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
          // 修改@Provider的变量
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
          // 修改@Consumer的变量
          this.content += 'content';
        })
      NestedComponentChildChild({ content: this.content, addContent: () => this.content += 'content' });
    }
  }
}

@ComponentV2
struct NestedComponentChildChild {
  // 在未上树的时候，Test组件无View的父亲，该节点为离屏节点。@Consumer找不到对应@Provider，使用默认值
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

### 示例11（组件树为@Provider-@Consumer-BuilderNode-@Consumer时的同步关系）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了组件树为@Provider-@Consumer-BuilderNode-@Consumer的情况时，@Consumer和@Provider之间的同步关系。

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
  // 与@Consumer装饰的状态变量双向同步
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

// 组件树为@Provider-@Consumer-BuilderNode-@Consumer结构
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

### 示例12（组件树为@Provider-BuilderNode-@Provider-@Consumer时的同步关系）

> 说明：
> 
> 从API version 23开始，支持跨BuilderNode配对@Provider和@Consumer。

该示例演示了组件树为@Provider-BuilderNode-@Provider-@Consumer的情况时，@Consumer和@Provider之间的同步关系。

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

// 组件树为@Provider-BuilderNode-@Provider-@Consumer结构
@Entry
@ComponentV2
struct Provider1 {
  // 与@Consumer装饰的状态变量双向同步
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

### 示例13（ReactiveBuilderNode中鼠标事件）

从API version 22版本开始支持。

该示例演示了在自定义组件中截获鼠标事件并进行坐标转换的完整流程。组件通过[onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse)回调读取本地x/y坐标，再结合FrameNode.getPositionToParent()得到的偏移量，调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)将相对坐标转换为像素坐标，更新[MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)的windowX/windowY、displayX/displayY。最后通过rootNode.postInputEvent将转换后的鼠标事件分发给子节点进行处理。



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
      // 鼠标事件处理
      .onMouse((event) => {
        let promptAction: PromptAction = uiContext!.getPromptAction();
        promptAction.showToast({
          message: 'onMouse',
          duration: 3000
        });
        console.info('onMouse');
      })
      // 触摸事件处理
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

// 继承NodeController实现自定义UI控制器
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
    // 获取节点相对于父组件的偏移量
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let mouseEvent = event as MouseEvent;
    // 坐标转换：将事件坐标转换为节点坐标系
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      mouseEvent.windowX = uiContext.vp2px(offsetX + mouseEvent.x);
      mouseEvent.windowY = uiContext.vp2px(offsetY + mouseEvent.y);
    }
    // 调用postInputEvent将转换后的事件传递给ReactiveBuilderNode
    let result = this.rootNode.postInputEvent(event);
    return result;
  }

  // 处理触摸事件的方法
  postTouchEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    let node: FrameNode | null = this.rootNode.getFrameNode();
    // 获取节点相对于父组件的偏移量
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let touchEvent = event as TouchEvent;
    // 转换changedTouches数组中的所有触摸点坐标
    let changedTouchLen = touchEvent.changedTouches.length;
    for (let i = 0; i < changedTouchLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
        touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
      }
    }
    // 转换touches数组中的所有触摸点坐标
    let touchesLen = touchEvent.touches.length;
    for (let i = 0; i < touchesLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
        touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
      }
    }
    // 调用postInputEvent将转换后的事件传递给ReactiveBuilderNode
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
        // 捕获鼠标事件并传递给自定义节点
        .onMouse((event) => {
          if (event != undefined) {
            this.nodeController.postMouseEvent(event, this.getUIContext());
          }
        })
        // 捕获触摸事件并传递给自定义节点
        .onTouch((event) => {
          if (event != undefined) {
            this.nodeController.postTouchEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 180 })
  }
}
```

### 示例14（ReactiveBuilderNode中触摸事件）

从API version 22版本开始支持。

该示例演示了在自定义组件中截获触摸事件并对触点坐标进行转换的完整流程。在[onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch)回调中，遍历[TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent对象说明)的changedTouches和touches数组，对每个触点的x/y坐标加上组件偏移量并调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)转换为像素，更新各自的windowX/windowY、displayX/displayY。最后同样通过rootNode.postInputEvent将转换后的触摸事件分发给子节点处理。



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
      // 触摸事件处理
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
    // 构建ReactiveBuilderNode，传递按钮文本和UI上下文
    this.rootNode.build(this.wrapBuilder, {}, 'onTouch', uiContext);
    return this.rootNode.getFrameNode();
  }

  postInputEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    let node: FrameNode | null = this.rootNode.getFrameNode();
    // 获取节点相对于父组件的偏移量
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    if (event.source == SourceType.TouchScreen) {
      let touchEvent = event as TouchEvent;
      // 转换changedTouches数组中的所有触摸点坐标
      let changedTouchLen = touchEvent.changedTouches.length;
      for (let i = 0; i < changedTouchLen; i++) {
        if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
          touchEvent.changedTouches[i].windowX = uiContext.vp2px(offsetX + touchEvent.changedTouches[i].x);
          touchEvent.changedTouches[i].windowY = uiContext.vp2px(offsetY + touchEvent.changedTouches[i].y);
        }
      }
      // 转换touches数组中的所有触摸点坐标
      let touchesLen = touchEvent.touches.length;
      for (let i = 0; i < touchesLen; i++) {
        if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
          touchEvent.touches[i].windowX = uiContext.vp2px(offsetX + touchEvent.touches[i].x);
          touchEvent.touches[i].windowY = uiContext.vp2px(offsetY + touchEvent.touches[i].y);
        }
      }
    }

    // 调用postInputEvent将转换后的事件传递给ReactiveBuilderNode
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
        // 捕获触摸事件并传递给自定义节点
        .onTouch((event) => {
          if (event != undefined) {
            this.nodeController.postInputEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 180 })
  }
}
```

### 示例15（ReactiveBuilderNode中轴事件）

从API version 22版本开始支持。

该示例演示了在自定义组件中截获滚轮或触控板轴事件并进行坐标转换的完整流程。在[onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent)回调中，先获取事件的相对x/y坐标，再加上组件偏移量后调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)转换为像素，更新AxisEvent的windowX/windowY、displayX/displayY，最后通过rootNode.postInputEvent将转换后的轴事件分发给子节点进行处理。



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
          message: 'onAxisEvent', // 显示轴事件触发提示
          duration: 3000
        });
        console.info('onAxisEvent');
      })
  }
  .width(500)
  .height(200)
  .backgroundColor(Color.Gray)
}

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: ReactiveBuilderNode<[text: string, uiContext: UIContext]> | null = null;
  private wrapBuilder: WrappedBuilder<[text: string, uiContext: UIContext]> =
    wrapBuilder<[text: string, uiContext: UIContext]>(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new ReactiveBuilderNode(uiContext);
    // 构建ReactiveBuilderNode，传递按钮文本和UI上下文
    this.rootNode.build(this.wrapBuilder, {}, 'onAxisEvent', uiContext);
    return this.rootNode.getFrameNode();
  }

  // 轴事件处理方法
  postInputEvent(event: InputEventType, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    // 读取本地x、y与buildNode相对于父组件的偏移量，转换为像素坐标
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let axisEvent = event as AxisEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      axisEvent.windowX = uiContext.vp2px(offsetX + axisEvent.x);
      axisEvent.windowY = uiContext.vp2px(offsetY + axisEvent.y);
    }
    // 调用postInputEvent将转换后的事件传递给ReactiveBuilderNode
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
        // 捕获轴事件并传递给自定义节点
        .onAxisEvent((event) => {
          if (event != undefined) {
            // 调用轴事件处理方法
            this.nodeController.postInputEvent(event, this.getUIContext());
          }
        })
    }.offset({ top: 180 })
  }
}
```

### 示例16（BuilderNode中带竞争策略的鼠标事件）

从API version 24开始，新增postInputEventWithStrategy接口。

该示例演示了在自定义组件中截获鼠标事件并进行坐标转换的完整流程。组件通过[onMouse](../arkui-ts/ts-universal-mouse-key.md#onmouse)回调读取当前触点坐标x/y，再结合FrameNode.getPositionToParent得到的偏移量，调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)将相对坐标转换为像素坐标，更新[MouseEvent](../arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)的windowX/windowY、displayX/displayY。选择不同的手势竞争策略[CompetitionStrategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24)，最后通过rootNode.postInputEventWithStrategy将转换后的鼠标事件分发给子节点进行处理。

```TypeScript
import { NodeController, BuilderNode, FrameNode, PromptAction, UIContext, InputEventType } from '@kit.ArkUI';

// 自定义参数传递的类
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

// 继承NodeController实现自定义UI控制器
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
    // 读取本地x、y与BuilderNode相对于父组件的偏移量，转换为像素坐标
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
    // 将鼠标事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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
    // 读取本地x、y与BuilderNode相对于父组件的偏移量，转换为像素坐标
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
    // 将鼠标事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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
    // 读取本地x、y与BuilderNode相对于父组件的偏移量，转换为像素坐标
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
    // 将鼠标事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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

### 示例17（BuilderNode中带竞争策略的触摸事件）

从API version 24开始，新增postInputEventWithStrategy接口。

该示例演示了在自定义组件中截获触摸事件并对触点坐标进行转换的完整流程。在[onTouch](../arkui-ts/ts-universal-events-touch.md#ontouch)回调中，遍历[TouchEvent](../arkui-ts/ts-universal-events-touch.md#touchevent对象说明)的changedTouches和touches数组，对每个触点的x/y加上组件偏移量并调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)转换为像素，更新每个触点的windowX/windowY、displayX/displayY。选择不同的手势竞争策略[CompetitionStrategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24)，最后同样通过rootNode.postInputEventWithStrategy将转换后的触摸事件分发给子节点处理。

```TypeScript
import { NodeController, BuilderNode, FrameNode, PromptAction, UIContext, InputEventType } from '@kit.ArkUI';

// 自定义参数传递的类
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

// 继承NodeController实现自定义UI控制器
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
    // 读取本地x、y与BuilderNode相对于父组件的偏移量，转换为像素坐标
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
    // 将触摸事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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
    // 读取本地x、y与BuilderNode相对于父组件的偏移量，转换为像素坐标
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
    // 将触摸事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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
    // 读取本地x、y与BuilderNode相对于父组件的偏移量，转换为像素坐标
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
    // 将触摸事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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

### 示例18（BuilderNode中带竞争策略的轴事件）

从API version 24开始，新增postInputEventWithStrategy接口。

该示例演示了在自定义组件中截获滚轮或触控板轴事件并进行坐标转换的完整流程。在[onAxisEvent](../arkui-ts/ts-universal-events-axis.md#onaxisevent)回调中，先获取事件的相对x/y，再加上组件偏移量后调用[vp2px](./arkts-apis-uicontext-uicontext.md#vp2px12)转换为像素，更新AxisEvent的windowX/windowY、displayX/displayY，选择不同的手势竞争策略[CompetitionStrategy](../arkui-ts/ts-appendix-enums.md#competitionstrategy24)，最后通过rootNode.postInputEventWithStrategy将转换后的轴事件分发给子节点进行处理。

```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext, PromptAction, InputEventType } from '@kit.ArkUI';

// 自定义传递参数的类
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

// 继承NodeController实现自定义UI控制器
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
    // 读取本地x、y与BuilderNode相对于父组件的偏移量，转换为像素坐标
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;

    let axisEvent = event as AxisEvent;
    if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
      axisEvent.windowX = uiContext.vp2px(offsetX + axisEvent.x);
      axisEvent.windowY = uiContext.vp2px(offsetY + axisEvent.y);
    }
    // 将轴事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
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
