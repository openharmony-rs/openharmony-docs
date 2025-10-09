# BuilderNode.static

提供能够挂载系统组件的自定义节点BuilderNode。BuilderNode只能用作没有子节点的叶节点。

> **说明：**
>
> 从API version 20开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 本模块仅适用于ArkTS1.2。

## 导入模块

```ts
import { BuilderNode } from '@ohos.arkui.node';
```

## BuilderNode

BuilderNode支持通过无状态的UI方法[@Builder（ArkTS1.2）](../../ui/state-management/arkts-v1.2-builder.md)生成组件树，并持有组件树的根节点。不支持将其定义为状态变量。BuilderNode中持有的FrameNode仅用于将该BuilderNode作为子节点挂载到其他FrameNode上。对BuilderNode持有的FrameNode进行属性设置与子节点操作可能会引发不可预期的行为，因此不建议通过BuilderNode的[getFrameNode](#getframenode)方法和[FrameNode](js-apis-arkui-frameNode.md)的[getRenderNode](js-apis-arkui-frameNode.md#getrendernode)方法获取RenderNode，并通过[RenderNode](js-apis-arkui-renderNode.md)的接口对其进行属性设置与子节点操作。

> **说明：**
>
> BuilderNode下的自定义组件可以使用[@Prop](../../ui/state-management/arkts-prop.md)装饰器。
>
> 其余装饰器的行为未定义。不建议使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

### constructor

constructor(uiContext: UIContext, options?: RenderOptions)

当将BuilderNode挂载到其他RenderNode中显示时，需要显式指定RenderOptions中的selfIdealSize。否则，Builder内的节点将使用父组件的默认布局约束[0,0]。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名    | 类型                                    | 必填 | 说明                                                              |
| --------- | --------------------------------------- | ---- | ----------------------------------------------------------------- |
| uiContext | [UIContext](js-apis-arkui-UIContext.md) | 是   | UI上下文，获取方式可参考[UIContext获取方法](./js-apis-arkui-node.md#uicontext获取方法)。 |
| options   | [RenderOptions](./js-apis-arkui-builderNode.md#renderoptions)         | 否   | BuilderNode的构造可选参数。<br/>默认值：undefined   |

> **说明：**
>
> uiContext的入参必须是有效的UI上下文。传入非法值或未设置将导致创建失败。

### build

build(builder: WrappedBuilder\<CustomBuilderT\<T>, arg: T): void

依照传入的带参数的[CustomBuilderT\<T>](./arkui-ts/ts-types.md#custombuildertt20)创建组件树，并持有组件树的根节点。无状态的UI方法[@Builder（ArkTS1.2）](../../ui/state-management/arkts-v1.2-builder.md)最多拥有一个根节点。
支持自定义组件。

> **说明：**
>
> @Builder嵌套使用时，需要保证内外的@Builder方法的入参对象一致。
>
> 最外层的@Builder只支持一个入参。
>
操作BuilderNode中的对象时，确保其引用不被回收。一旦BuilderNode对象被虚拟机回收，其FrameNode、RenderNode对象将与后端节点解除引用关系，导致从BuilderNode中获取的FrameNode对象不再对应任何节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名  | 类型                                                            | 必填 | 说明                                                                                   |
| ------- | --------------------------------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
| builder | WrappedBuilder\<[CustomBuilderT\<T>](./arkui-ts/ts-types.md#custombuildertt20)> | 是   | 在构建节点树时所需的无状态UI方法[@Builder（ArkTS1.2）](../../ui/state-management/arkts-v1.2-builder.md)封装的[WrappedBuilder对象](../../ui/state-management/arkts-v1.2-wrapBuilder.md)。 |
| arg     |T                                                  |  是    | builder的入参。当前仅支持一个入参，且入参对象类型与@Builder定义的入参类型保持一致。                                          |

### build

build(builder: WrappedBuilder\<CustomBuilderT\<T>, arg: T , options: BuildOptions): void

依照传入的带参数的[CustomBuilderT\<T>](./arkui-ts/ts-types.md#custombuildertt20)创建组件树，并持有组件树的根节点。同时，支持设置build相关的配置项。无状态的UI方法@Builder最多拥有一个根节点。
支持自定义组件。

> **说明：**
>
> @Builder进行创建和更新的规格参考[@Builder](../../ui/state-management/arkts-v1.2-builder.md)。
>
> 最外层的@Builder只支持一个入参。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名  | 类型                                                            | 必填 | 说明                                                                                    |
| ------- | --------------------------------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
| builder | WrappedBuilder\<[CustomBuilderT\<T>](./arkui-ts/ts-types.md#custombuildertt20)> | 是   | 用于构建对应节点树的无状态UI方法[@Builder（ArkTS1.2）](../../ui/state-management/arkts-v1.2-builder.md)封装的[WrappedBuilder对象](../../ui/state-management/arkts-v1.2-wrapBuilder.md)。   |
| arg     |T                                           | 是   | builder的入参。                                                            |
| options | [BuildOptions](./js-apis-arkui-builderNode.md#buildoptions12)  | 是   | 该值无效，默认支持@Builder参数不一致，且行为与@Builder的行为保持一致。                                        |

**示例：**

请参考[示例1（使用带参数的build方法创建BuilderNode）](#示例1使用带参数的build方法创建buildernode)。

### build

 build(builder: WrappedBuilder\<CustomBuilder>): void

依照传入的无参数[CustomBuilder](./arkui-ts/ts-types.md#custombuilder20)创建组件树，并持有组件树的根节点。

> **说明：**
>
> @Builder进行创建和更新的规格参考@Builder。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名  | 类型                                                            | 必填 | 说明                                                                                    |
| ------- | --------------------------------------------------------------- | ---- | -------------------------------------------------------------------------------------- |
| builder | WrappedBuilder\<[CustomBuilder](./arkui-ts/ts-types.md#custombuilder20)>  | 是   | 创建对应节点树的时候所需的无状态UI方法[@Builder（ArkTS1.2）](../../ui/state-management/arkts-v1.2-builder.md)封装的[WrappedBuilder对象](../../ui/state-management/arkts-v1.2-wrapBuilder.md)。   |

**示例：**

请参考[示例2（使用无参的build方法创建BuilderNode）](#示例2使用无参的build方法创建buildernode)。

### getFrameNode

getFrameNode(): FrameNode | null

获取BuilderNode中的FrameNode。在BuilderNode执行build操作之后，才会生成FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**返回值：**

| 类型                                                      | 说明                                                                  |
| --------------------------------------------------------- | --------------------------------------------------------------------- |
| [FrameNode](js-apis-arkui-frameNode.md) \| null | 一个FrameNode对象。若该BuilderNode不包含FrameNode，则返回空对象null。 |

**示例：**

BuilderNode作为NodeContainer的根节点返回。请参考[示例3（buildernode作为nodecontainer的根节点返回）](#示例3buildernode作为nodecontainer的根节点返回)。

BuilderNode的FrameNode挂到其它FrameNode下。请参考[示例4（buildernode的framenode挂到其它framenode下）](#示例4buildernode的framenode挂到其它framenode下)。

BuilderNode的RenderNode挂到其他RenderNode下。由于RenderNode不会传递布局约束信息，建议避免通过该方式挂载节点。请参考[示例5（buildernode的rendernode挂到其他rendernode下）](#示例5buildernode的rendernode挂到其他rendernode下)。

### update

update(arg: T): void

根据提供的参数更新BuilderNode，该参数为[build](#build)方法调用时传入的参数类型相同。对自定义组件进行update的时候需要在自定义组件中使用的变量定义为@Prop类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                                     |
| ------ | ------ | ---- | ------------------------------------------------------------------------ |
| arg    |  T | 是   | 用于更新BuilderNode的参数，和[build](#build)调用时传入的参数类型一致。 |

**示例：**

请参考[示例6（buildernode更新）](#示例6buildernode更新)。

### dispose

dispose(): void

立即释放当前BuilderNode对象对[基本概念：实体节点](../../ui/arkts-user-defined-node.md#基本概念)的引用关系。关于BuilderNode的解绑场景请参见[解除实体节点引用关系](../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。

> **说明：**
>
> 当BuilderNode对象调用dispose之后，会与后端实体节点解除引用关系。若前端对象BuilderNode无法释放，容易导致内存泄漏。建议在不再需要对该BuilderNode对象进行操作时，开发者主动调用dispose释放后端节点，以减少引用关系的复杂性，降低内存泄漏的风险。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**示例：**

请参考[示例7（buildernode与后端节点解除引用关系）](#示例7buildernode与后端节点解除引用关系)。

### updateConfiguration

updateConfiguration(): void

传递[系统环境变化](../apis-ability-kit/js-apis-app-ability-configuration.md)事件，触发节点的全量更新。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

> **说明：**
>
> updateConfiguration接口用于通知对象当前系统环境变量发生变化。

**示例：**

请参考[示例8（使用updateconfiguration通知buildernode环境变量变化）](#示例8使用updateconfiguration通知buildernode环境变量变化)。

## 示例

### 示例1（使用带参数的build方法创建BuilderNode）

该示例展示了如何使用包含参数的@Builder方法创建BuilderNode。

```ts
import {
  Text,
  Column,
  Component,
  Button,
  ClickEvent,
  UIContext,
  Builder,
  Entry,
  ContentSlot,
  Row,
  wrapBuilder
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeContent, BuilderNode, FrameNode } from '@ohos.arkui.node';

class ParamsInterface {
  text?: string;
}

@Builder
function buildText(params: ParamsInterface) {
  Column() {
    Text(params.text)
      .fontSize(50)
  }
}

@Entry
@Component
struct Index {
  @State message: string = "HELLO"
  private content: NodeContent = new NodeContent();

  build() {
    Row() {
      Column() {
        Button('addBuilderNode')
          .onClick((clickEvent: ClickEvent) => {
            let buildNode = new BuilderNode<ParamsInterface>(this.getUIContext());
            buildNode.build(wrapBuilder(buildText), { text: this.message } as ParamsInterface);
            this.content.addFrameNode(buildNode.getFrameNode()!);
          })
        ContentSlot(this.content)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例2（使用无参的build方法创建BuilderNode）

该示例展示了如何使用无参的@Builder创建BuilderNode。

```ts
import {
  Text,
  Column,
  Component,
  Button,
  ClickEvent,
  UIContext,
  Builder,
  Entry,
  ContentSlot,
  Row,
  wrapBuilder
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeContent, BuilderNode, FrameNode } from '@ohos.arkui.node';

@Builder
function buildText() {
  Column() {
    Text("buildText")
      .fontSize(50)
  }
}

@Entry
@Component
struct Index {
  @State message: string = "HELLO"
  private content: NodeContent = new NodeContent();

  build() {
    Row() {
      Column() {
        Button('addBuilderNode')
          .onClick((clickEvent: ClickEvent) => {
            let buildNode = new BuilderNode(this.getUIContext());
            buildNode.build(wrapBuilder(buildText));
            this.content.addFrameNode(buildNode.getFrameNode()!);
          })
        ContentSlot(this.content)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例3（BuilderNode作为NodeContainer的根节点返回）

该示例展示了如何使用getFrameNode接口将BuilderNode的根节点挂载在NodeContainer上。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}

class TextNodeController extends NodeController {
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "DEFAULT";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    this.textNode = new BuilderNode<Params>(context);
    this.textNode!.build(wrapBuilder(buildText), new Params(this.message));
    return this.textNode!.getFrameNode();
  }
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        NodeContainer(new TextNodeController(this.message))
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### 示例4（BuilderNode的FrameNode挂到其它FrameNode下）

该示例展示了如何将BuilderNode挂载在允许修改的FrameNode下。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight,
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "DEFAULT";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.textNode = new BuilderNode<Params>(context, { selfIdealSize: { width: 150, height: 150 } });
    this.textNode!.build(wrapBuilder(buildText), new Params(this.message));
    if (this.rootNode !== null) {
      this.rootNode!.appendChild(this.textNode!.getFrameNode()!);
    }
    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        NodeContainer(new TextNodeController(this.message))
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### 示例5（BuilderNode的RenderNode挂到其他RenderNode下）

该示例展示了如何将BuilderNode挂载在RenderNode下面。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode, RenderNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "DEFAULT";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    let renderNode = new RenderNode();
    renderNode.clipToFrame = false;
    this.textNode = new BuilderNode<Params>(context, { selfIdealSize: { width: 150, height: 150 } });
    this.textNode?.build(wrapBuilder(buildText), new Params(this.message));
    const textRenderNode = this.textNode?.getFrameNode()?.getRenderNode();
    const rootRenderNode = this.rootNode?.getRenderNode();
    if (rootRenderNode !== null && textRenderNode) {
      rootRenderNode!.appendChild(renderNode);
      renderNode.appendChild(textRenderNode!);
    }
    return this.rootNode!;
  }
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        NodeContainer(new TextNodeController(this.message))
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### 示例6（BuilderNode更新）

该示例展示了如何对有参数的BuilderNode进行参数的更新。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight,
  ClickEvent,
  Button,
  Color
} from '@ohos.arkui.component';
import { State, Prop } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode, RenderNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

// 自定义组件
@Component
struct TextBuilder {
  @Prop message: string = "TextBuilder";

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .backgroundColor(Color.Gray)
      }
    }
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
    TextBuilder({ message: params.text }) // 自定义组件
  }
}

class TextNodeController extends NodeController {
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    this.textNode = new BuilderNode<Params>(context);
    this.textNode!.build(wrapBuilder(buildText), new Params(this.message));
    return this.textNode!.getFrameNode()!;
  }

  update(message: string) {
    if (this.textNode !== null) {
      this.textNode!.update(new Params(message));
    }
  }
}

@Entry
@Component
struct Index {
  @State message: string = "hello";
  private textNodeController: TextNodeController = new TextNodeController(this.message);
  private count: number = 0;

  build() {
    Row() {
      Column() {
        NodeContainer(this.textNodeController)
          .width('100%')
          .height(200)
          .backgroundColor('#FFF0F0F0')
        Button('Update')
          .onClick((event: ClickEvent) => {
            this.count += 1;
            const message = "Update " + this.count.toString();
            this.textNodeController.update(message);
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### 示例7（BuilderNode与后端节点解除引用关系）

该示例展示了如何使用dispose接口解除BuilderNode与后端的节点引用关系。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight,
  ClickEvent,
  Button,
  Color,
} from '@ohos.arkui.component';
import { State, Prop } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode, RenderNode } from '@ohos.arkui.node';

@Component
struct TestComponent {
  build() {
    Column() {
      Text('This is a BuilderNode.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.error('aboutToAppear');
  }

  aboutToDisappear() {
    console.error('aboutToDisappear');
  }
}

@Builder
function buildComponent() {
  TestComponent()
}

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private builderNode: BuilderNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.builderNode = new BuilderNode(uiContext, { selfIdealSize: { width: 200, height: 100 } });
    this.builderNode!.build(wrapBuilder(buildComponent));
    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode!.size = { width: 200, height: 200 };
      rootRenderNode!.backgroundColor = 0xff00ff00;
      rootRenderNode!.appendChild(this.builderNode!.getFrameNode()!.getRenderNode()!);
    }
    return this.rootNode!;
  }

  dispose() {
    if (this.builderNode !== null) {
      this.builderNode?.dispose();
    }
  }

  removeBuilderNode() {
    const rootRenderNode: RenderNode | null | undefined = this.rootNode?.getRenderNode();
    if (rootRenderNode && this.builderNode?.getFrameNode() !== null) {
      rootRenderNode?.removeChild(this.builderNode!.getFrameNode()!.getRenderNode()!);
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
      Button('BuilderNode dispose')
        .onClick((event: ClickEvent) => {
          this.myNodeController.removeBuilderNode();
          this.myNodeController.dispose();
        })
        .width('100%')
    }
  }
}
```

### 示例8（使用updateConfiguration通知BuilderNode环境变量变化）

该示例展示了如何使用updateConfiguration接口通知BuilderNode环境变量变化，从而触发组件的更新。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight,
  ClickEvent,
  Button,
  Color,
  $r
} from '@ohos.arkui.component';
import { State, Prop } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode, RenderNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

// 自定义组件
@Component
struct TextBuilder {
  // 作为自定义组件中需要更新的属性，数据类型为基础属性，定义为@Prop
  @Prop message: string = "TextBuilder";

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
    }
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
    TextBuilder({ message: params.text }) // 自定义组件
  }.backgroundColor($r('sys.color.ohos_id_color_background'))
}

class TextNodeController extends NodeController {
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    return this.textNode?.getFrameNode() ? this.textNode!.getFrameNode()! : null;
  }

  createNode(context: UIContext): void {
    this.textNode = new BuilderNode<Params>(context);
    this.textNode!.build(wrapBuilder(buildText), new Params(this.message));
    builderNodeMap.push(this.textNode!);
  }

  deleteNode(): void {
    let node = builderNodeMap.pop();
    node?.dispose();
  }

  update(message: string): void {
    if (this.textNode !== null) {
      // 调用update进行更新。
      this.textNode!.update(new Params(message));
    }
  }
}

// 记录创建的自定义节点对象
const builderNodeMap: Array<BuilderNode<Params>> = new Array<BuilderNode<Params>>();

function updateColorMode() {
  builderNodeMap.forEach((value, index) => {
    // 通知BuilderNode环境变量改变，触发深浅色切换
    value.updateConfiguration();
  })
}

@Entry
@Component
struct Index {
  @State message: string = "hello";
  private textNodeController: TextNodeController = new TextNodeController(this.message);
  private count: number = 0;

  aboutToAppear(): void {
    //创建自定义节点并添加至map
    this.textNodeController.createNode(this.getUIContext());
  }

  aboutToDisappear(): void {
    //移除map中的引用，并将自定义节点释放
    this.textNodeController.deleteNode();
  }

  build() {
    Row() {
      Column() {
        NodeContainer(this.textNodeController)
          .width('100%')
          .height(200)
          .backgroundColor('#FFF0F0F0')
        Button('Update')
          .onClick((event: ClickEvent) => {
            this.count += 1;
            const message = "Update " + this.count.toString();
            this.textNodeController.update(message);
          })
        Button('通知切换环境变量')
          .onClick((event: ClickEvent) => {
            updateColorMode()
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}

```
