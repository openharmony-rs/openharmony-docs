# typeNode
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sunbees-->
<!--Designer: @sunbees-->
<!--Tester: @khq-->
<!--Adviser: @Brilliantry_Rui-->

typeNode提供创建具体类型的FrameNode能力，可通过FrameNode的基础接口进行自定义的挂载，使用占位容器进行显示。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前不支持在预览器中使用typeNode节点。
>
> - typeNode节点暂不支持拖拽。
>
> - typeNode对象不支持使用JSON序列化。
>
> - 在[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的场景中调用typeNode对象的接口时，建议使用[UIContext](./arkts-apis-uicontext-uicontext.md)的[runScopedTask](./arkts-apis-uicontext-uicontext.md#runscopedtask)接口明确UI上下文，参考[执行绑定UI实例的闭包](../../ui/arkts-global-interface.md#执行绑定ui实例的闭包)示例。
>
> - 使用typeNode创建[Text](./arkui-ts/ts-basic-components-text.md)、[Image](./arkui-ts/ts-basic-components-image.md)、[Select](./arkui-ts/ts-basic-components-select.md)、[Toggle](./arkui-ts/ts-basic-components-toggle.md)节点时，当传入的[UIContext](./arkts-apis-uicontext-uicontext.md)对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。

**示例：**

请参考[自定义具体类型节点示例](#自定义具体类型节点示例)。

## Text

type Text = TypedFrameNode&lt;TextInterface, TextAttribute&gt;

Text类型的FrameNode节点类型。不允许添加子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Text](#text23)。

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;TextInterface, TextAttribute&gt; | 提供Text类型FrameNode节点。<br/> TextInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Text组件的构造函数类型。 <br/> TextAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Text组件的属性设置对象。<br/> TextInterface表示Text的[接口](./arkui-ts/ts-basic-components-text.md#接口)，TextAttribute表示Text的[属性](./arkui-ts/ts-basic-components-text.md#属性)。 |

## Text<sup>23+</sup>

type Text = TextFrameNode

Text类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Text](#text)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [TextFrameNode](#textframenode23) | Text类型FrameNode节点。 |

## TextFrameNode<sup>23+</sup>

TextFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Text](./arkui-ts/ts-basic-components-text.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(content?: string | Resource, value?: TextOptions): TextAttribute

初始化Text组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| content | string&nbsp;\|&nbsp;[Resource](./arkui-ts/ts-types.md#resource) | 否   | 文本内容。<br/>默认值：''。 |
| value | [TextOptions](./arkui-ts/ts-basic-components-text.md#textoptions11) | 否   | Text组件的初始化选项。默认值为空。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextAttribute | 返回Text组件的属性设置对象。 |

### createNode('Text')

createNode(context: UIContext, nodeType: 'Text'): Text

创建Text类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createTextNode](#createtextnode23)。

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Text' | 是 | 创建Text类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Text](#text) | Text类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建Text
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize("Hello").fontColor(Color.Blue).fontSize(14);
    typeNode.getAttribute(text, 'Text')?.fontWeight(FontWeight.Bold);
    col.appendChild(text);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Text sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### createTextNode<sup>23+</sup>

createTextNode(context: UIContext, options?: FrameNodeOptions): Text

创建Text类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Text')](#createnodetext)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否   | 创建节点的额外选项。默认值继承[FrameNodeOptions](#framenodeoptions24)。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Text](#text23) | Text类型的FrameNode节点。 |

### getAttribute('Text')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Text'): TextAttribute | undefined

获取Text节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[getTextAttribute](#gettextattribute24)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Text' | 是 | 获取Text节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextAttribute&nbsp;\|&nbsp;undefined | Text节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建Text
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize("Hello");
    // 获取Text的属性
    typeNode.getAttribute(text, 'Text')?.fontColor(Color.Red)
    col.appendChild(text);
    // 创建另一个Text用于对比
    let text2 = typeNode.createNode(uiContext, 'Text');
    text2.initialize("world");
    col.appendChild(text2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Text sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### getTextAttribute<sup>24+</sup>

export function getTextAttribute(node: FrameNode): TextAttribute | undefined

获取Text类型的FrameNode的文本属性TextAttribute。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[getAttribute('Text')](#getattributetext20)。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextAttribute&nbsp;\|&nbsp;undefined | Text节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { Entry, Component, Column, NodeContainer, Text, FrameNode, Color, ColumnOptions, UIContext } from '@kit.ArkUI';
import { NodeController } from 'arkui.NodeController';
import { typeNode } from 'arkui.FrameNode';

class TextNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);

    let col = typeNode.createColumnNode(uiContext);
    col.initialize({ space: 5 } as ColumnOptions);
    node.appendChild(col);

    let text = typeNode.createTextNode(uiContext);
    text.initialize("Hello");
    typeNode.getTextAttribute(text)?.fontColor(Color.Red)
    col.appendChild(text);

    let text2 = typeNode.createTextNode(uiContext);
    text2.initialize("world");
    col.appendChild(text2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private textNodeController: TextNodeController = new TextNodeController();

  build() {
    Column(undefined) {
      NodeContainer(this.textNodeController);
    }
    .height("100%")
    .width("100%")
  }
}
```

![image](figures/getTextAttribute_static.jpg)

### bindController('Text')<sup>20+</sup>

bindController(node: FrameNode, controller: TextController, nodeType: 'Text'): void

将文本控制器[TextController](arkui-ts/ts-basic-components-text.md#textcontroller11)绑定到[Text](#text)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[bindTextController](#bindtextcontroller24)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定文本控制器的目标节点。 |
| controller | [TextController](arkui-ts/ts-basic-components-text.md#textcontroller11) | 是   | 文本控制器。 |
| nodeType | 'Text' | 是 | 绑定输入框控制器的目标节点的节点类型为Text。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  // 设置TextController，可以在外部获取
  controller: TextController = new TextController()

  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建Text
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize("Hello").fontColor(Color.Blue).fontSize(14);
    typeNode.getAttribute(text, 'Text')?.fontWeight(FontWeight.Bold)
    // 绑定TextController
    typeNode.bindController(text, this.controller, 'Text');
    col.appendChild(text);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  @State line: number = 0
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Text bindController Sample')
      NodeContainer(this.myNodeController)
      Text(`Text的行数, ${this.line}`)
      Button(`点击获取行数`)
        .onClick(() => {
          this.line = this.myNodeController.controller.getLayoutManager().getLineCount()
        })
    }
  }
}
```

### bindTextController<sup>24+</sup>

bindTextController(node: FrameNode, controller: TextController): void

将文本控制器[TextController](arkui-ts/ts-basic-components-text.md#textcontroller11)绑定到[Text](#text)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[bindController('Text')](#bindcontrollertext20)。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定文本控制器的目标节点。 |
| controller | [TextController](arkui-ts/ts-basic-components-text.md#textcontroller11) | 是   | 文本控制器。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. |

**示例：**

```ts
import { Entry, Component, Column, NodeContainer, Text, TextController, FrameNode, ColumnOptions, UIContext } from '@kit.ArkUI';
import { NodeController } from 'arkui.NodeController';
import { typeNode } from 'arkui.FrameNode';

class TextNodeController extends NodeController {
  controller: TextController = new TextController();

  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);

    let col = typeNode.createColumnNode(uiContext);
    col.initialize({ space: 5 } as ColumnOptions);
    node.appendChild(col);

    let text = typeNode.createTextNode(uiContext);
    text.initialize("Hello world!");
    col.appendChild(text);
    typeNode.bindTextController(text, this.controller);

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private textNodeController: TextNodeController = new TextNodeController();

  build() {
    Column(undefined) {
      NodeContainer(this.textNodeController);
    }
    .height("100%")
    .width("100%")
  }
}
```

![image](figures/bindTextController_static.jpg)

## Column

type Column = TypedFrameNode&lt;ColumnInterface, ColumnAttribute&gt;

Column类型的FrameNode节点类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[Column](#column23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                   | 说明                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;ColumnInterface, ColumnAttribute&gt; | 提供Column类型FrameNode节点。<br/> ColumnInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Column组件的构造函数类型。 <br/> ColumnAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Column组件的属性设置对象。<br/> ColumnInterface表示Column的[接口](./arkui-ts/ts-container-column.md#接口)，ColumnAttribute表示Column的[属性](./arkui-ts/ts-container-column.md#属性)。 |

## Column<sup>23+</sup>
type Column = ColumnFrameNode

Column类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[Column](#column)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [ColumnFrameNode](#columnframenode23) | Column类型FrameNode节点。 |

## ColumnFrameNode<sup>23+</sup>

ColumnFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Column](./arkui-ts/ts-container-column.md)类型的FrameNode

### createNode('Column')

createNode(context: UIContext, nodeType: 'Column'): Column

创建Column类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createColumnNode](#createcolumnnode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Column' | 是 | 创建Column类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Column](#column) | Column类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Column控制器
class MyColumnController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    // 创建Column
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('50%')
      .height('50%')
      .backgroundColor(Color.Gray)
    node.appendChild(col)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myColumnController: MyColumnController = new MyColumnController();

  build() {
    Column({ space: 5 }) {
      Text('ColumnSample')
      NodeContainer(this.myColumnController);
    }.width('100%')
  }
}
```

### createColumnNode<sup>23+</sup>

createColumnNode(context: UIContext, options?: FrameNodeOptions): Column

创建Column类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('Column')](#createnodecolumn)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建Column类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Column](#column) | Column类型的FrameNode节点。 |

### getAttribute('Column')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Column'): ColumnAttribute | undefined

获取Column节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[getColumnAttribute](#getcolumnattribute23)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Column' | 是 | 获取Column节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ColumnAttribute&nbsp;\|&nbsp;undefined | Column节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建Column
    let col1 = typeNode.createNode(uiContext, 'Column');
    col1.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    // 获取Column的属性
    typeNode.getAttribute(col1, 'Column')?.backgroundColor(Color.Blue).width("100%")
    col.appendChild(col1);
    // 创建另一个Column用于对比
    let col2 = typeNode.createNode(uiContext, 'Column');
    col2.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    col.appendChild(col2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Column sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### getColumnAttribute<sup>23+</sup>

getColumnAttribute(node: FrameNode): ColumnAttribute | undefined

获取Column节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[getAttribute('Column')](#getattributecolumn20)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ColumnAttribute&nbsp;\|&nbsp;undefined | Column节点类型的属性，若获取失败，则返回undefined。 |

## Row

type Row = TypedFrameNode&lt;RowInterface, RowAttribute&gt;

Row类型的FrameNode节点类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[Row](#row23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                             | 说明                                                         |
| ------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;RowInterface, RowAttribute&gt; | 提供Row类型FrameNode节点。<br/> RowInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Row组件的构造函数类型。 <br/> RowAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Row组件的属性设置对象。<br/> RowInterface表示Row的[接口](./arkui-ts/ts-container-row.md#接口)，RowAttribute表示Row的[属性](./arkui-ts/ts-container-row.md#属性)。 |

## Row<sup>23+</sup>
type Row = RowFrameNode

Row类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[Row](#row)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [RowFrameNode](#rowframenode23) | Row类型FrameNode节点。 |

## RowFrameNode<sup>23+</sup>

RowFrameNode[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Row](./arkui-ts/ts-container-row.md)类型的FrameNode

### initialize<sup>23+</sup>

abstract initialize(options?: RowOptions | RowOptionsV2): RowAttribute

初始化Row组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [RowOptions](../apis-arkui/arkui-ts/ts-container-row.md#rowoptions18对象说明)&nbsp;\|&nbsp;[RowOptionsV2](../apis-arkui/arkui-ts/ts-container-row.md#rowoptionsv218对象说明) | 否   | 横向布局元素间距。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RowAttribute | 返回Row组件的属性设置对象。 |

### createNode('Row')

createNode(context: UIContext, nodeType: 'Row'): Row

创建Row类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createRowNode](#createrownode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Row' | 是 | 创建Row类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Row](#row) | Row类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Row控制器
class MyRowController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    // 创建row
    let row = typeNode.createNode(uiContext, 'Row')
    row.initialize({ space: 5 })
      .width('50%')
      .height('50%')
      .backgroundColor(Color.Gray)
    node.appendChild(row)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myRowController: MyRowController = new MyRowController();

  build() {
    Column({ space: 5 }) {
      Text('RowSample')
      NodeContainer(this.myRowController);
    }.width('100%')
  }
}
```

### createRowNode<sup>23+</sup>

createRowNode(context: UIContext, options?: FrameNodeOptions): Row

创建Row类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('Row')](#createnoderow)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建Row类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Row](#row) | Row类型的FrameNode节点。 |

### getAttribute('Row')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Row'): RowAttribute | undefined

获取Row节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[getRowAttribute](#getrowattribute23)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Row' | 是 | 获取Row节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RowAttribute&nbsp;\|&nbsp;undefined | Row节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建Row
    let row1 = typeNode.createNode(uiContext, 'Row');
    row1.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    // 获取Row的属性
    typeNode.getAttribute(row1, 'Row')?.backgroundColor(Color.Blue).width("100%")
    col.appendChild(row1);
    // 创建另一个Row用于对比
    let row2 = typeNode.createNode(uiContext, 'Row');
    row2.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    col.appendChild(row2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Row sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### getRowAttribute<sup>23+</sup>

getRowAttribute(node: FrameNode): RowAttribute | undefined

获取Row节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[getAttribute('Row')](#getattributerow20)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RowAttribute&nbsp;\|&nbsp;undefined | Row节点类型的属性，若获取失败，则返回undefined。 |

## Stack

type Stack = TypedFrameNode&lt;StackInterface, StackAttribute&gt;

Stack类型的FrameNode节点类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**相关接口：** 该接口对应的ArkTS-Sta的接口是[Stack](#stack23)。

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;StackInterface, StackAttribute&gt; | 提供Stack类型FrameNode节点。<br/> StackInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Stack组件的构造函数类型。 <br/> StackAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Stack组件的属性设置对象。<br/> StackInterface表示Stack的[接口](./arkui-ts/ts-container-stack.md#接口)，StackAttribute表示Stack的[属性](./arkui-ts/ts-container-stack.md#属性)。 |

## Stack<sup>23+</sup>
type Stack = StackFrameNode

Stack类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[Stack](#stack)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [StackFrameNode](#stackframenode23) | Stack类型FrameNode节点。 |

## StackFrameNode<sup>23+</sup>

StackFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Stack](./arkui-ts/ts-container-stack.md)类型的FrameNode

### initialize<sup>23+</sup>

abstract initialize(options?: StackOptions): StackAttribute

初始化Stack组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [StackOptions](../apis-arkui/arkui-ts/ts-container-stack.md#stackoptions18对象说明) | 否   | 设置子组件在容器内的对齐方式。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| StackAttribute | 返回Stack组件的属性设置对象。 |

### createNode('Stack')

createNode(context: UIContext, nodeType: 'Stack'): Stack

创建Stack类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createStackNode](#createstacknode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Stack' | 是 | 创建Stack类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Stack](#stack) | Stack类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Stack控制器
class MyStackController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    // 创建Stack
    let stack = typeNode.createNode(uiContext, 'Stack')
    stack.initialize({ alignContent: Alignment.Top })
      .width('50%')
      .height('50%')
      .backgroundColor(Color.Gray)
    node.appendChild(stack)
    let text = typeNode.createNode(uiContext, 'Text')
    text.initialize("This is Text")
    // 向stack添加text
    stack.appendChild(text)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myStackController: MyStackController = new MyStackController();

  build() {
    Column({ space: 5 }) {
      Text('StackSample')
      NodeContainer(this.myStackController);
    }.width('100%')
  }
}
```

### createStackNode<sup>23+</sup>

createStackNode(context: UIContext, options?: FrameNodeOptions): Stack

创建Stack类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('Stack')](#createnodestack)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建Stack类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Stack](#stack) | Stack类型的FrameNode节点。 |

### getAttribute('Stack')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Stack'): StackAttribute | undefined

获取Stack节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[getStackAttribute](#getstackattribute23)。

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Stack' | 是 | 获取Stack节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| StackAttribute&nbsp;\|&nbsp;undefined | Stack节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建Stack
    let stack1 = typeNode.createNode(uiContext, 'Stack');
    stack1.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    // 获取Stack的属性
    typeNode.getAttribute(stack1, 'Stack')?.backgroundColor(Color.Blue).width("100%")
    col.appendChild(stack1);
    // 创建另一个Stack用于对比
    let stack2 = typeNode.createNode(uiContext, 'Stack');
    stack2.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    col.appendChild(stack2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Row sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### getStackAttribute<sup>23+</sup>

getStackAttribute(node: FrameNode): StackAttribute | undefined

获取Stack节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[getAttribute('Stack')](#getattributestack20)

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| StackAttribute&nbsp;\|&nbsp;undefined | Stack节点类型的属性，若获取失败，则返回undefined。 |

## GridRow

type GridRow = TypedFrameNode&lt;GridRowInterface, GridRowAttribute&gt;

GridRow类型的FrameNode节点类型。只允许添加GridCol类型子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[GridRow](#gridrow23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                     | 说明                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;GridRowInterface, GridRowAttribute&gt; | 提供GridRow类型FrameNode节点。<br/> GridRowInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为GridRow组件的构造函数类型。 <br/> GridRowAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回GridRow组件的属性设置对象。<br/> GridRowInterface表示GridRow的[接口](./arkui-ts/ts-container-gridrow.md#接口)，GridRowAttribute表示GridRow的[属性](./arkui-ts/ts-container-gridrow.md#属性)。 |

## GridRow<sup>23+</sup>
type GridRow = GridRowFrameNode

GridRow类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[GridRow](#gridrow)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [GridRowFrameNode](#gridrowframenode23) | GridRow类型FrameNode节点。 |

## GridRowFrameNode<sup>23+</sup>

GridRowFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[GridRow](./arkui-ts/ts-container-gridrow.md)类型的FrameNode

### initialize<sup>23+</sup>

abstract initialize(options?: GridRowOptions): GridRowAttribute

初始化GridRow组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [GridRowOptions](../apis-arkui/arkui-ts/ts-container-gridrow.md#gridrowoptions对象说明) | 否   | 栅栏布局子组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| GridRowAttribute | 返回GridRow组件的属性设置对象。 |

### createNode('GridRow')

createNode(context: UIContext, nodeType: 'GridRow'): GridRow

创建GridRow类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createGridRowNode](#creategridrownode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'GridRow' | 是 | 创建GridRow类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [GridRow](#gridrow) | GridRow类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义GridRow控制器
class MyGridRowController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    // 创建GridRow
    let gridRow = typeNode.createNode(uiContext, 'GridRow')
    gridRow.initialize({ columns: 12 })
      .width('50%')
      .height('50%')
      .backgroundColor(Color.Gray)
    node.appendChild(gridRow)
    // 创建GridCol
    let gridCol = typeNode.createNode(uiContext, 'GridCol')
    gridCol.initialize({ span: 2, offset: 4 })
      .height("100%")
      .backgroundColor(Color.Red)
    // 向gridRow添加gridCol
    gridRow.appendChild(gridCol)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myGridRowController: MyGridRowController = new MyGridRowController();

  build() {
    Column({ space: 5 }) {
      Text('GridRowSample')
      NodeContainer(this.myGridRowController);
    }.width('100%')
  }
}
```

### createGridRowNode<sup>23+</sup>

createGridRowNode(context: UIContext, options?: FrameNodeOptions): GridRow

创建GridRow类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('GridRow')](#createnodegridrow)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建GridRow类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [GridRow](#gridrow) | GridRow类型的FrameNode节点。 |

## GridCol

type GridCol = TypedFrameNode&lt;GridColInterface, GridColAttribute&gt;

GridCol类型的FrameNode节点类型。不允许添加子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[GridCol](#gridcol23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                     | 说明                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;GridColInterface, GridColAttribute&gt; | 提供GridCol类型FrameNode节点。<br/> GridColInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为GridCol组件的构造函数类型。 <br/> GridColAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回GridCol组件的属性设置对象。<br/> GridColInterface表示GridCol的[接口](./arkui-ts/ts-container-gridcol.md#接口)，GridColAttribute表示GridCol的[属性](./arkui-ts/ts-container-gridcol.md#属性)。 |

## GridCol<sup>23+</sup>
type GridCol = GridColFrameNode

GridCol类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[GridCol](#gridcol)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [GridColFrameNode](#gridcolframenode23) | GridCol类型FrameNode节点。 |

## GridColFrameNode<sup>23+</sup>

ColumnFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[GridCol](./arkui-ts/ts-container-gridcol.md)类型的FrameNode

### initialize<sup>23+</sup>

abstract initialize(options?: GridColOptions): GridColAttribute

初始化GridCol组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | GridColOptions | 否   | 栅栏布局子组件参数。<br/> GridColOptions请参考[GridColOptions对象说明](../apis-arkui/arkui-ts/ts-container-gridcol.md#gridcoloptions对象说明) |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| GridColAttribute | 返回GridCol组件的属性设置对象。 |

### createNode('GridCol')

createNode(context: UIContext, nodeType: 'GridCol'): GridCol

创建GridCol类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createGridColNode](#creategridcolnode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'GridCol' | 是 | 创建GridCol类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [GridCol](#gridcol) | GridCol类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义GridRow控制器
class MyGridRowController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    // 创建GridRow
    let gridRow = typeNode.createNode(uiContext, 'GridRow')
    gridRow.initialize({ columns: 12 })
      .width('50%')
      .height('50%')
      .backgroundColor(Color.Gray)
    node.appendChild(gridRow)
    // 创建GridCol
    let gridCol = typeNode.createNode(uiContext, 'GridCol')
    gridCol.initialize({ span: 2, offset: 4 })
      .height("100%")
      .backgroundColor(Color.Red)
    // 向gridRow添加gridCol
    gridRow.appendChild(gridCol)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myGridRowController: MyGridRowController = new MyGridRowController();

  build() {
    Column({ space: 5 }) {
      Text('GridColSample')
      NodeContainer(this.myGridRowController);
    }.width('100%')
  }
}
```

### createGridColNode<sup>23+</sup>

createGridColNode(context: UIContext, options?: FrameNodeOptions): GridCol

创建GridCol类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('GridCol')](#createnodegridcol)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建GridCol类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [GridCol](#gridcol) | GridCol类型的FrameNode节点。 |

## Flex

type Flex = TypedFrameNode&lt;FlexInterface, FlexAttribute&gt;

Flex类型的FrameNode节点类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[Flex](#flex23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;FlexInterface, FlexAttribute&gt; | 提供Flex类型FrameNode节点。<br/> FlexInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Flex组件的构造函数类型。 <br/> FlexAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Flex组件的属性设置对象。<br/> FlexInterface表示Flex的[接口](./arkui-ts/ts-container-flex.md#接口)，FlexAttribute表示Flex的[属性](./arkui-ts/ts-container-flex.md#属性)。 |

## Flex<sup>23+</sup>
type Flex = FlexFrameNode

Flex类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[Flex](#flex)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [FlexFrameNode](#flexframenode23) | Flex类型FrameNode节点。 |

## FlexFrameNode<sup>23+</sup>

FlexFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Flex](./arkui-ts/ts-container-flex.md)类型的FrameNode

### initialize<sup>23+</sup>

abstract initialize(options?: FlexOptions): FlexAttribute

初始化Flex组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [FlexOptions](../apis-arkui/arkui-ts/ts-container-flex.md#flexoptions对象说明) | 否   | 设置子组件在容器内的对齐方式。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| FlexAttribute | 返回Flex组件的属性设置对象。 |

### createNode('Flex')

createNode(context: UIContext, nodeType: 'Flex'): Flex

创建Flex类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createFlexNode](#createflexnode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Flex' | 是 | 创建Flex类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Flex](#flex) | Flex类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Flex控制器
class MyFlexController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    // 创建Flex
    let flex = typeNode.createNode(uiContext, 'Flex')
    flex.initialize()
      .width('50%')
      .height('50%')
      .backgroundColor(Color.Gray)
    node.appendChild(flex)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myFlexController: MyFlexController = new MyFlexController();

  build() {
    Column({ space: 5 }) {
      Text('FlexSample')
      NodeContainer(this.myFlexController);
    }.width('100%')
  }
}
```

### createFlexNode<sup>23+</sup>

createFlexNode(context: UIContext, options?: FrameNodeOptions): Flex

创建Flex类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('Flex')](#createnodeflex)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建Flex类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Flex](#flex) | Flex类型的FrameNode节点。 |


### getAttribute('Flex')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Flex'): FlexAttribute | undefined

获取Flex节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[getFlexAttribute](#getflexattribute23)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Flex' | 是 | 获取Flex节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| FlexAttribute&nbsp;\|&nbsp;undefined | Flex节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建Flex
    let flex1 = typeNode.createNode(uiContext, 'Flex');
    flex1.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    // 获取Flex的属性
    typeNode.getAttribute(flex1, 'Flex')?.backgroundColor(Color.Blue).width("100%")
    col.appendChild(flex1);
    // 创建另一个Flex用于对比
    let flex2 = typeNode.createNode(uiContext, 'Flex');
    flex2.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    col.appendChild(flex2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Flex sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### getFlexAttribute<sup>23+</sup>

getFlexAttribute(node: FrameNode): FlexAttribute | undefined

获取Flex节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[getAttribute('Flex')](#getattributeflex20)

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| FlexAttribute&nbsp;\|&nbsp;undefined | Flex节点类型的属性，若获取失败，则返回undefined。 |

## Swiper<sup>23+</sup>

type Swiper = SwiperFrameNode

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[Swiper](#swiper)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [SwiperFrameNode](#swiperframenode23) | Swiper类型的FrameNode节点。 |

## SwiperFrameNode<sup>23+</sup>

SwiperFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Swiper](./arkui-ts/ts-container-swiper.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(controller?: SwiperController): SwiperAttribute

初始化Swiper组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| controller | [SwiperController](../apis-arkui/arkui-ts/ts-container-swiper.md#swipercontroller) | 否   | 给组件绑定一个控制器。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| SwiperAttribute | 返回Swiper组件的属性设置对象。 |

## Swiper

type Swiper = TypedFrameNode&lt;SwiperInterface, SwiperAttribute&gt;

Swiper类型的FrameNode节点类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[SwiperFrameNode](#swiperframenode23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                   | 说明                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;SwiperInterface, SwiperAttribute&gt; | 提供Swiper类型FrameNode节点。<br/> SwiperInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Swiper组件的构造函数类型。 <br/> SwiperAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Swiper组件的属性设置对象。<br/> SwiperInterface表示Swiper的[接口](./arkui-ts/ts-container-swiper.md#接口)，SwiperAttribute表示Swiper的[属性](./arkui-ts/ts-container-swiper.md#属性)。 |

### createNode('Swiper')

createNode(context: UIContext, nodeType: 'Swiper'): Swiper

创建Swiper类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createSwiperNode](#createswipernode24)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Swiper' | 是 | 创建Swiper类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Swiper](#swiper) | Swiper类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Swiper控制器
class MySwiperController extends NodeController {
  swiperController: SwiperController = new SwiperController()

  makeNode(uiContext: UIContext): FrameNode | null {
    // 创建Swiper
    let swiperNode = typeNode.createNode(uiContext, 'Swiper')

    // 创建Text
    let text0 = typeNode.createNode(uiContext, 'Text')
    text0.initialize("0")
      .width('100%')
      .height('100%')
      .textAlign(TextAlign.Center)
    // 向swiper添加text0
    swiperNode.appendChild(text0)
    // 创建另一个Text用于切换
    let text1 = typeNode.createNode(uiContext, 'Text')
    text1.initialize("1")
      .width('100%')
      .height('100%')
      .textAlign(TextAlign.Center)
    // 向swiper添加text1
    swiperNode.appendChild(text1)
    swiperNode.commonAttribute.width('100%')
      .height('20%')
      .backgroundColor(0xAFEEEE)
    // 向swiper绑定控制器
    typeNode.bindController(swiperNode, this.swiperController, 'Swiper')
    typeNode.getAttribute(swiperNode, 'Swiper')?.loop(false)
    return swiperNode;

  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private mySwiperController: MySwiperController = new MySwiperController();

  build() {
    Column({ space: 5 }) {
      Text('SwiperSample')
      NodeContainer(this.mySwiperController);
    }.width('100%')
  }
}
```

### createSwiperNode<sup>24+</sup>

createSwiperNode(context: UIContext, options?: FrameNodeOptions): Swiper

创建Swiper类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('Swiper')](#createnodeswiper)。

**ArkTS-Dyn起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建Swiper类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Swiper](#swiper) | Swiper类型的FrameNode节点。 |

### getAttribute('Swiper')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Swiper'): SwiperAttribute | undefined

获取Swiper节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[getSwiperAttribute](#getswiperattribute24)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Swiper' | 是 | 获取Swiper节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| SwiperAttribute&nbsp;\|&nbsp;undefined | Swiper节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

请参考[createNode('Swiper')示例](#createnodeswiper)。

### getSwiperAttribute<sup>24+</sup>

getSwiperAttribute(node: FrameNode): SwiperAttribute | undefined

获取Swiper节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[getAttribute('Swiper')](#getattributeswiper20)。

**ArkTS-Dyn起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| SwiperAttribute&nbsp;\|&nbsp;undefined | Swiper节点类型的属性，若获取失败，则返回undefined。 |


### bindController('Swiper')<sup>20+</sup>

bindController(node: FrameNode, controller: SwiperController, nodeType: 'Swiper'): void

将控制器[SwiperController](arkui-ts/ts-container-swiper.md#swipercontroller)绑定到[Swiper](#swiper)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[bindSwiperController<sup>24+</sup>](#bindswipercontroller24)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定控制器的目标节点。 |
| controller | [SwiperController](arkui-ts/ts-container-swiper.md#swipercontroller) | 是   | Swiper容器组件的控制器。 |
| nodeType | 'Swiper' | 是 | 绑定控制器的目标节点的节点类型为Swiper。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. |

**示例：**

请参考[createNode('Swiper')示例](#createnodeswiper)。

### bindSwiperController<sup>24+</sup>

bindSwiperController(node: FrameNode, controller: SwiperController): void

将控制器[SwiperController](arkui-ts/ts-container-swiper.md#swipercontroller)绑定到[Swiper](#swiper)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[bindController('Swiper')<sup>20+</sup>](#bindcontrollerswiper20)。

**ArkTS-Dyn起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定控制器的目标节点。 |
| controller | [SwiperController](arkui-ts/ts-container-swiper.md#swipercontroller) | 是   | Swiper容器组件的控制器。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. |

**示例：**

请参考[createNode('Swiper')示例](#createnodeswiper)。

## Progress

type Progress = TypedFrameNode&lt;ProgressInterface, ProgressAttribute&gt;

Progress类型的FrameNode节点类型。不允许添加子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[ProgressFrameNode](#progressframenode23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                       | 说明                                                         |
| ---------------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;ProgressInterface, ProgressAttribute&gt; | 提供Progress类型FrameNode节点。<br/> ProgressInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Progress组件的构造函数类型。 <br/> ProgressAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Progress组件的属性设置对象。<br/> ProgressInterface表示Progress的[接口](./arkui-ts/ts-basic-components-progress.md#接口)，ProgressAttribute表示Progress的[属性](./arkui-ts/ts-basic-components-progress.md#属性)。 |

## Progress<sup>23+</sup>

type Progress = ProgressFrameNode

Progress类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Progress](#progress)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [ProgressFrameNode](#progressframenode23) | Text类型FrameNode节点。 |

## ProgressFrameNode<sup>23+</sup>

ProgressFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Progress](./arkui-ts/ts-basic-components-progress.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value: ProgressOptions): ProgressAttribute

初始化Progress组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [ProgressOptions](./arkui-ts/ts-basic-components-progress.md#progressoptions对象说明) | 否   | 进度条选项。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ProgressAttribute | 返回Progress组件的属性设置对象。 |

### createNode('Progress')

createNode(context: UIContext, nodeType: 'Progress'): Progress

创建Progress类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createProgressNode](#createprogressnode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Progress' | 是 | 创建Progress类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Progress](#progress) | Progress类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Progress控制器
class MyProgressNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    // 创建Progress
    let node = typeNode.createNode(uiContext, 'Progress');
    node.initialize({
      value: 15,
      total: 200,
      type: ProgressType.ScaleRing
    }).width(100)
      .height(100)
    this!.rootNode!.appendChild(node);
    return this.rootNode;
  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyProgressNodeController()).margin(5)
    }.width('100%').height('100%')

  }
}
```

### createProgressNode<sup>23+</sup>

createProgressNode(context: UIContext, options?: FrameNodeOptions): Progress

创建Progress类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Progress')](#createnodeprogress)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否   | 创建节点的额外选项。默认值继承[FrameNodeOptions](#framenodeoptions24)。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Progress](#progress23) | Progress类型的FrameNode节点。 |

### getAttribute('Progress')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Progress'): ProgressAttribute | undefined

获取Progress节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[getProgressAttribute](#getprogressattribute23)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Progress' | 是 | 获取Progress节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ProgressAttribute&nbsp;\|&nbsp;undefined | Progress节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Progress控制器
class MyProgressNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    let node = typeNode.createNode(uiContext, 'Progress');
    node.initialize({
      value: 15,
      total: 200,
      type: ProgressType.ScaleRing
    }).width(100)
      .height(100)
    // 获取Progress的属性
    typeNode.getAttribute(node, 'Progress');
    this!.rootNode!.appendChild(node);
    return this.rootNode;
  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyProgressNodeController()).margin(5)
    }.width('100%').height('100%')

  }
}
```

### getProgressAttribute<sup>23+</sup>

export function getProgressAttribute(node: FrameNode): ProgressAttribute | undefined

获取Progress类型FrameNode的属性ProgressAttribute。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[getAttribute('Progress')](#getattributeprogress20)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ProgressAttribute&nbsp;\|&nbsp;undefined | Progress节点类型的属性，若获取失败，则返回undefined。 |

## Scroll

type Scroll = TypedFrameNode&lt;ScrollInterface, ScrollAttribute&gt;

Scroll类型的FrameNode节点类型。允许添加一个子组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

| 类型                                                   | 说明                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;ScrollInterface, ScrollAttribute&gt; | 提供Scroll类型FrameNode节点。<br/> ScrollInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Scroll组件的构造函数类型。 <br/> ScrollAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Scroll组件的属性设置对象。<br/> ScrollInterface表示Scroll的[接口](./arkui-ts/ts-container-scroll.md#接口)，ScrollAttribute表示Scroll的[属性](./arkui-ts/ts-container-scroll.md#属性)。 |

### createNode('Scroll')

createNode(context: UIContext, nodeType: 'Scroll'): Scroll

创建Scroll类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Scroll' | 是 | 创建Scroll类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Scroll](#scroll) | Scroll类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Scroll控制器
class MyScrollController extends NodeController {
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    // 创建Scroll
    let scroller: Scroller = new Scroller();
    // 创建Scroll并设置属性
    let scrollNode = typeNode.createNode(uiContext, 'Scroll');
    scrollNode.initialize(scroller).size({ width: '100%', height: 500 });
    typeNode.getAttribute(scrollNode, "Scroll")?.friction(0.6);

    let colNode = typeNode.createNode(uiContext, 'Column');
    // 向scroll添加column
    scrollNode.appendChild(colNode);

    for (let i = 0; i < 10; i++) {
      let text = typeNode.createNode(uiContext, 'Text');
      text.initialize('item' + i)
        .size({ width: '90%', height: 100 })
        .textAlign(TextAlign.Center)
        .backgroundColor(0xF9CF93);
      colNode.appendChild(text);
    }

    this!.rootNode!.appendChild(scrollNode);
    return this.rootNode;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myScrollController: MyScrollController = new MyScrollController();

  build() {
    Column({ space: 5 }) {
      Text('ScrollSample')
      NodeContainer(this.myScrollController)

    }.width('100%')
  }
}
```

## ScrollFrameNode<sup>23+</sup>

ScrollFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Scroll类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(scroller?: Scroller): ScrollAttribute

该接口用于创建Scroll类型组件的构造参数，用于设置或更新组件的初始值。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| scroller | [Scroller](./arkui-ts/ts-container-scroll.md#scroller) | 否   | 滚动控制器。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ScrollAttribute | 返回Scroll组件的属性设置对象。<br/> ScrollAttribute表示Scroll的[属性](./arkui-ts/ts-container-scroll.md#属性)。 |

## Scroll<sup>23+</sup>

type Scroll = ScrollFrameNode

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [ScrollFrameNode](#scrollframenode23) | 提供Scroll类型的FrameNode节点。 |

### getAttribute('Scroll')<sup>15+</sup>

getAttribute(node: FrameNode, nodeType: 'Scroll'): ScrollAttribute | undefined

获取Scroll节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 15

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Scroll' | 是 | 获取Scroll节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ScrollAttribute&nbsp;\|&nbsp;undefined | Scroll节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

完整示例请参考[createNode('Scroll')](#createnodescroll)的示例。

### getScrollAttribute<sup>24+</sup>

getScrollAttribute(node: FrameNode): ScrollAttribute | undefined

获取Scroll节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ScrollAttribute&nbsp;\|&nbsp;undefined | Scroll节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.getScrollAttribute(node);
```

### getEvent('Scroll')<sup>19+</sup>

getEvent(node: FrameNode, nodeType: 'Scroll'): UIScrollEvent | undefined

获取Scroll节点中持有的UIScrollEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 19

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取事件时所需的目标节点。 |
| nodeType | 'Scroll' | 是 | 获取Scroll节点类型的滚动事件。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [UIScrollEvent](./arkui-ts/ts-container-scroll.md#uiscrollevent19)&nbsp;\|&nbsp;undefined | Scroll节点类型的滚动事件，若获取失败，则返回undefined。 |

**示例：**

完整示例请参考[滚动事件示例](#滚动事件示例)。

### getScrollEvent<sup>24+</sup>

getScrollEvent(node: FrameNode): UIScrollEvent | undefined

获取Scroll节点中持有的UIScrollEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取事件时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [UIScrollEvent](./arkui-ts/ts-container-scroll.md#uiscrollevent19)&nbsp;\|&nbsp;undefined | List节点类型的滚动事件，若获取失败，则返回undefined。 |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.getScrollEvent(node);
```

### bindController('Scroll')<sup>15+</sup>

bindController(node: FrameNode, controller: Scroller, nodeType: 'Scroll'): void

将滚动控制器[Scroller](arkui-ts/ts-container-scroll.md#scroller)绑定到[Scroll](#scroll)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 15

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定滚动控制器的目标节点。 |
| controller | [Scroller](arkui-ts/ts-container-scroll.md#scroller) | 是   | 滚动控制器。 |
| nodeType | 'Scroll' | 是 | 绑定滚动控制器的目标节点的节点类型为Scroll。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. the type of the node is error. 2. the node is null or undefined. |
| 100021   | The FrameNode is not modifiable. Introduced in API 15 and will not be threw above API 24. [since 15 - 24] |

**示例：**

<!--code_no_check-->

```ts
typeNode.bindController(node, scroller, 'Scroll');
```

### bindScrollController<sup>24+</sup>

bindScrollController(node: FrameNode, controller: Scroller): void

将滚动控制器Scroller绑定到Scroll节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定滚动控制器的目标节点。 |
| controller | [Scroller](arkui-ts/ts-container-scroll.md#scroller) | 是   | 滚动控制器。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.bindScrollController(node, scroller);
```

## RelativeContainer

type RelativeContainer = TypedFrameNode&lt;RelativeContainerInterface, RelativeContainerAttribute&gt;

RelativeContainer类型的FrameNode节点类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[RelativeContainer](#relativecontainer23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;RelativeContainerInterface, RelativeContainerAttribute&gt; | 提供RelativeContainer类型FrameNode节点。<br/> RelativeContainerInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为RelativeContainer组件的构造函数类型。 <br/> RelativeContainerAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回RelativeContainer组件的属性设置对象。<br/> RelativeContainerInterface表示RelativeContainer的[接口](./arkui-ts/ts-container-relativecontainer.md#接口)，RelativeContainerAttribute表示RelativeContainer的[属性](./arkui-ts/ts-container-relativecontainer.md#属性)。 |

## RelativeContainer<sup>23+</sup>
type RelativeContainer = RelativeContainerFrameNode

RelativeContainer类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[RelativeContainer](#relativecontainer)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [RelativeContainerFrameNode](#relativecontainerframenode23) | RelativeContainer类型FrameNode节点。 |

## RelativeContainerFrameNode<sup>23+</sup>

RelativeContainerFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[RelativeContainer](./arkui-ts/ts-container-relativecontainer.md)类型的FrameNode

### initialize<sup>23+</sup>

abstract initialize(): RelativeContainerAttribute

初始化RelativeContainer组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RelativeContainerAttribute | 返回RelativeContainer组件的属性设置对象。 |


### createNode('RelativeContainer')

createNode(context: UIContext, nodeType: 'RelativeContainer'): RelativeContainer

创建RelativeContainer类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createRelativeContainerNode](#createrelativecontainernode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'RelativeContainer' | 是 | 创建RelativeContainer类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [RelativeContainer](#relativecontainer) | RelativeContainer类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Relative控制器
class MyRelativeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    // 创建RelativeContainer
    let relative = typeNode.createNode(uiContext, 'RelativeContainer')
    relative.initialize()
      .width('50%')
      .height('50%')
      .backgroundColor(Color.Gray)
    node.appendChild(relative)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myRelativeController: MyRelativeController = new MyRelativeController();

  build() {
    Column({ space: 5 }) {
      Text('RelativeContainerSample')
      NodeContainer(this.myRelativeController);
    }.width('100%')
  }
}
```

### createRelativeContainerNode<sup>23+</sup>

createRelativeContainerNode(context: UIContext, options?: FrameNodeOptions): RelativeContainer

创建RelativeContainer类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('RelativeContainer')](#createnoderelativecontainer)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建RelativeContainer类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [RelativeContainer](#relativecontainer) | RelativeContainer类型的FrameNode节点。 |

### getAttribute('RelativeContainer')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'RelativeContainer'): RelativeContainerAttribute | undefined

获取RelativeContainer节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[getRelativeContainerAttribute](#getrelativecontainerattribute23)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'RelativeContainer' | 是 | 获取RelativeContainer节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RelativeContainerAttribute&nbsp;\|&nbsp;undefined | RelativeContainer节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建RelativeContainer
    let relative1 = typeNode.createNode(uiContext, 'RelativeContainer');
    relative1.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    // 获取RelativeContainer的属性
    typeNode.getAttribute(relative1, 'RelativeContainer')?.backgroundColor(Color.Blue).width("100%")
    col.appendChild(relative1);
    // 创建另一个RelativeContainer用于对比
    let relative2 = typeNode.createNode(uiContext, 'RelativeContainer');
    relative2.initialize().width("50%").height("20%").backgroundColor(Color.Pink);
    col.appendChild(relative2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('RelativeContainer sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### getRelativeContainerAttribute<sup>23+</sup>

getRelativeContainerAttribute(node: FrameNode): RelativeContainerAttribute | undefined

获取RelativeContainer节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[getAttribute('RelativeContainer')](#getattributerelativecontainer20)

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RelativeContainerAttribute&nbsp;\|&nbsp;undefined | RelativeContainer节点类型的属性，若获取失败，则返回undefined。 |

## Divider

type Divider = TypedFrameNode&lt;DividerInterface, DividerAttribute&gt;

Divider类型的FrameNode节点类型。不允许添加子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[Divider](#divider23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                     | 说明                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;DividerInterface, DividerAttribute&gt; | 提供Divider类型FrameNode节点。<br/> DividerInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为RelativeContainer组件的构造函数类型。 <br/> DividerAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Divider组件的属性设置对象。<br/> DividerInterface表示Divider的[接口](./arkui-ts/ts-basic-components-divider.md#接口)，DividerAttribute表示Divider的[属性](./arkui-ts/ts-basic-components-divider.md#属性)。 |

## Divider<sup>23+</sup>
type Divider = DividerFrameNode

Divider类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[Divider](#divider)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [DividerFrameNode](#dividerframenode23) | Divider类型FrameNode节点。 |

## DividerFrameNode<sup>23+</sup>

DividerFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Divider](./arkui-ts/ts-basic-components-divider.md)类型的FrameNode

### initialize<sup>23+</sup>

abstract initialize(): DividerAttribute

初始化Divider组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| DividerAttribute | 返回Divider组件的属性设置对象。 |

### createNode('Divider')

createNode(context: UIContext, nodeType: 'Divider'): Divider

创建Divider类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createDividerNode](#createdividernode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Divider' | 是 | 创建Divider类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Divider](#divider) | Divider类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Divider控制器
class MyDividerController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建divider
    let divider = typeNode.createNode(uiContext, 'Divider')
    divider.initialize()
      .strokeWidth(1)
    // 向col添加divider
    col.appendChild(divider)

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myDividerController: MyDividerController = new MyDividerController();

  build() {
    Column({ space: 5 }) {
      Text('DividerSample')
      NodeContainer(this.myDividerController);

    }.width('100%')
  }
}
```

### createDividerNode<sup>23+</sup>

createDividerNode(context: UIContext, options?: FrameNodeOptions): Divider

创建Divider类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('Divider')](#createnodedivider)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建Divider类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Divider](#divider) | Divider类型的FrameNode节点。 |

## LoadingProgress

type LoadingProgress = TypedFrameNode&lt;LoadingProgressInterface, LoadingProgressAttribute&gt;

LoadingProgress类型的FrameNode节点类型。不允许添加子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[LoadingProgress](#loadingprogress23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;LoadingProgressInterface, LoadingProgressAttribute&gt; | 提供LoadingProgress类型FrameNode节点。<br/>**说明：**<br/> LoadingProgressInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为LoadingProgress组件的构造函数类型。 <br/> LoadingProgressAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回LoadingProgress组件的属性设置对象。<br/> LoadingProgressInterface表示LoadingProgress的[接口](./arkui-ts/ts-basic-components-loadingprogress.md#接口)，LoadingProgressAttribute表示LoadingProgress的[属性](./arkui-ts/ts-basic-components-loadingprogress.md#属性)。 |

## LoadingProgress<sup>23+</sup>

type LoadingProgress = LoadingProgressFrameNode

LoadingProgress类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[LoadingProgress](#loadingprogress)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [LoadingProgressFrameNode](#loadingprogressframenode23) | LoadingProgress类型的FrameNode节点。 |

## LoadingProgressFrameNode<sup>23+</sup>

LoadingProgressFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明LoadingProgress类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(): LoadingProgressAttribute

初始化LoadingProgress组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| LoadingProgressAttribute | 返回LoadingProgress组件的属性设置对象。 |

### createNode('LoadingProgress')

createNode(context: UIContext, nodeType: 'LoadingProgress'): LoadingProgress

创建LoadingProgress类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createLoadingProgressNode](#createloadingprogressnode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'LoadingProgress' | 是 | 创建LoadingProgress类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [LoadingProgress](#loadingprogress) | LoadingProgress类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义LoadingProgress控制器
class MyLoadingProgressNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    // 创建LoadingProgress
    let node = typeNode.createNode(uiContext, 'LoadingProgress');
    node.initialize()
      .width(100)
      .height(100)
      .color(Color.Red)
      .enableLoading(true)
    this!.rootNode!.appendChild(node);
    return this.rootNode;
  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyLoadingProgressNodeController()).margin(5)
    }.width('100%').height('100%')
  }
}
```

### createLoadingProgressNode<sup>23+</sup>

createLoadingProgressNode(context: UIContext, options?: FrameNodeOptions): LoadingProgress

创建LoadingProgress类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('LoadingProgress')](#createnodeloadingprogress)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否   | 创建节点的额外选项。默认值继承[FrameNodeOptions](#framenodeoptions24)。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [LoadingProgress](#loadingprogress23) | LoadingProgress类型的FrameNode节点。 |

### getAttribute('LoadingProgress')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'LoadingProgress'): LoadingProgressAttribute | undefined

获取[LoadingProgress](arkui-ts/ts-basic-components-loadingprogress.md)节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[getLoadingProgressAttribute](#getloadingprogressattribute23)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'LoadingProgress' | 是 | 获取LoadingProgress节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| LoadingProgressAttribute&nbsp;\|&nbsp;undefined | LoadingProgress节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义LoadingProgress控制器
class MyLoadingProgressNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    let node = typeNode.createNode(uiContext, 'LoadingProgress');
    node.initialize()
      .width(100)
      .height(100)
      .color(Color.Red)
      .enableLoading(true)
    // 获取LoadingProgress的属性
    typeNode.getAttribute(node, 'LoadingProgress');
    this!.rootNode!.appendChild(node);
    return this.rootNode;
  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyLoadingProgressNodeController()).margin(5)
    }.width('100%').height('100%')
  }
}
```

### getLoadingProgressAttribute<sup>23+</sup>

export function getLoadingProgressAttribute(node: FrameNode): LoadingProgressAttribute | undefined

获取LoadingProgress类型FrameNode的属性LoadingProgressAttribute。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[getAttribute('LoadingProgress')](#getattributeloadingprogress20)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| LoadingProgressAttribute&nbsp;\|&nbsp;undefined | LoadingProgress节点类型的属性，若获取失败，则返回undefined。 |

## Search

type Search = TypedFrameNode&lt;SearchInterface, SearchAttribute&gt;

Search类型的FrameNode节点类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Search](#search23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                   | 说明                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;SearchInterface, SearchAttribute&gt; | 提供Search类型FrameNode节点。<br/> SearchInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Search组件的构造函数类型。 <br/> SearchAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Search组件的属性设置对象。<br/> SearchInterface表示Search的[接口](./arkui-ts/ts-basic-components-search.md#接口)，SearchAttribute表示Search的[属性](./arkui-ts/ts-basic-components-search.md#属性)。 |

## Search<sup>23+</sup>

type Search = SearchFrameNode

Search类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Search](#search)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [SearchFrameNode](#searchframenode23) | Search类型FrameNode节点。 |

## SearchFrameNode<sup>23+</sup>

SearchFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Search](./arkui-ts/ts-basic-components-search.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value?: SearchOptions): SearchAttribute

初始化Search组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [SearchOptions](./arkui-ts/ts-basic-components-search.md#searchoptions18对象说明) | 否   | Search组件参数。默认值为空。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| SearchAttribute | 返回Search组件的属性设置对象。 |

### createNode('Search')

createNode(context: UIContext, nodeType: 'Search'): Search

创建Search类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createSearchNode](#createsearchnode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Search' | 是 | 创建Search类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Search](#search) | Search类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建Search
    let search = typeNode.createNode(uiContext, 'Search');
    search.initialize({ value: "Search" })
      .searchButton('SEARCH')
      .textFont({ size: 14, weight: 400 })
    col.appendChild(search);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Search sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### createSearchNode<sup>23+</sup>

createSearchNode(context: UIContext): Search

创建Search类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createNode('Search')](#createnodesearch)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Search](#search23) | Search类型的FrameNode节点。 |

## Blank

type Blank = TypedFrameNode&lt;BlankInterface, BlankAttribute&gt;

Blank类型的FrameNode节点类型。不允许添加子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[Blank](#blank23)。

**ArkTS-Dyn起始版本：** 12

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;BlankInterface, BlankAttribute&gt; | 提供Blank类型FrameNode节点。<br/> BlankInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Blank组件的构造函数类型。 <br/> BlankAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Blank组件的属性设置对象。<br/> BlankInterface表示Blank的[接口](./arkui-ts/ts-basic-components-blank.md#接口)，BlankAttribute表示Blank的[属性](./arkui-ts/ts-basic-components-blank.md#属性)。 |

## Blank<sup>23+</sup>
type Blank = BlankFrameNode

Stack类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[Blank](#blank)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [BlankFrameNode](#blankframenode23) | Blank类型FrameNode节点。 |

## BlankFrameNode<sup>23+</sup>

BlankFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Blank](./arkui-ts/ts-basic-components-blank.md)类型的FrameNode

### initialize<sup>23+</sup>

abstract initialize(min?: double&nbsp;|&nbsp;string): BlankAttribute

初始化Blank组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| min | double&nbsp;\|&nbsp;string | 否   | 空白填充组件在容器主轴上的最小尺寸。<br/>默认值：0 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| BlankAttribute | 返回Blank组件的属性设置对象。 |

### createNode('Blank')
createNode(context: UIContext, nodeType: 'Blank'): Blank

创建Blank类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[createBlankNode](#createblanknode23)。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Blank' | 是 | 创建Blank类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Blank](#blank) | Blank类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Blank控制器
class MyBlankController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Blank
    let blank = typeNode.createNode(uiContext, 'Blank')
    blank.initialize()
      .width('50%')
      .height('50%')
      .backgroundColor(Color.Blue)
    col.appendChild(blank)

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myBlankController: MyBlankController = new MyBlankController();

  build() {
    Column({ space: 5 }) {
      Text('BlankSample')
      NodeContainer(this.myBlankController);

    }.width('100%')
  }
}
```

### createBlankNode<sup>23+</sup>

createBlankNode(context: UIContext, options?: FrameNodeOptions): Blank

创建Blank类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[createNode('Blank')](#createnodeblank)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options |[FrameNodeOptions](#framenodeoptions24) | 否 | 创建Blank类型的FrameNode节点。 |

## Image

ArkTS-Dyn: type Image = TypedFrameNode&lt;ImageInterface, ImageAttribute&gt;

ArkTS-Sta: type Image = ImageFrameNode

Image类型的FrameNode节点类型。不允许添加子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 类型                                                 | 说明                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;ImageInterface, ImageAttribute&gt; | 提供Image类型FrameNode节点。<br/> ImageInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Image组件的构造函数类型。 <br/> ImageAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Image组件的属性设置对象。<br/> ImageInterface表示Image的[接口](./arkui-ts/ts-basic-components-image.md#接口)，ImageAttribute表示Image的[属性](./arkui-ts/ts-basic-components-image.md#属性)。 |

### createNode('Image')

createNode(context: UIContext, nodeType: 'Image'): Image

创建Image类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Image' | 是 | 创建Image类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Image](#image) | Image类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Image控制器
class MyImageController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    // 创建Image
    let imageNode = typeNode.createNode(uiContext, 'Image');
    imageNode
      // $r('app.media.img')需要替换为开发者所需的图像资源文件
      .initialize($r('app.media.img'))
      .width(100)
      .height(100)
      .fillColor(Color.Red)
      .objectFit(ImageFit.Contain)
      .renderMode(ImageRenderMode.Template)
      .fitOriginalSize(true)
      .matchTextDirection(true)
      .objectRepeat(ImageRepeat.X)
      .autoResize(true)

    this!.rootNode!.appendChild(imageNode);
    return this.rootNode;

  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyImageController()).margin(5)
    }.width('100%').height('100%')

  }
}
```

### getAttribute('Image')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Image'): ImageAttribute | undefined

获取Image节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Image' | 是 | 获取Image节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ImageAttribute&nbsp;\|&nbsp;undefined | Image节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 


```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Image控制器
class MyImageController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);
    let imageNode = typeNode.createNode(uiContext, 'Image');
    imageNode
      // $r('app.media.img')需要替换为开发者所需的图像资源文件
      .initialize($r('app.media.img'))
      .width(100)
      .height(100)
      .fillColor(Color.Red)
      .objectFit(ImageFit.Contain)
      .renderMode(ImageRenderMode.Template)
      .fitOriginalSize(true)
      .matchTextDirection(true)
      .objectRepeat(ImageRepeat.X)
      .autoResize(true)
    // 获取Image的属性
    typeNode.getAttribute(imageNode, 'Image');
    this!.rootNode!.appendChild(imageNode);
    return this.rootNode;

  }
}

@Entry
@Component
struct Sample {
  build() {
    Column({ space: 10 }) {
      NodeContainer(new MyImageController()).margin(5)
    }.width('100%').height('100%')

  }
}
```

## List

type List = TypedFrameNode&lt;ListInterface, ListAttribute&gt;

List类型的FrameNode节点类型。只允许添加[ListItem](#listitem)、[ListItemGroup](#listitemgroup)类型子组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;ListInterface, ListAttribute&gt; | 提供List类型FrameNode节点。<br/> ListInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为List组件的构造函数类型。 <br/> ListAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回List组件的属性设置对象。<br/> ListInterface表示List的[接口](./arkui-ts/ts-container-list.md#接口)，ListAttribute表示List的[属性](./arkui-ts/ts-container-list.md#属性)。 |

## ListFrameNode<sup>23+</sup>

ListFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明List类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(options?: ListOptions): ListAttribute

该接口用于创建List类型组件的构造参数，用于设置或更新组件的初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [ListOptions](./arkui-ts/ts-container-list.md#listoptions18对象说明) | 否   | 设置List组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListAttribute | 返回List组件的属性设置对象。<br/> ListAttribute表示List的[属性](./arkui-ts/ts-container-list.md#属性)。 |

## List<sup>23+</sup>

type List = ListFrameNode

List类型的FrameNode节点类型。只允许添加ListItem、ListItemGroup类型子组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [ListFrameNode](#listframenode23) | 提供List类型FrameNode节点。 |

### createNode('List')

createNode(context: UIContext, nodeType: 'List'): List

创建List类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'List' | 是 | 创建List类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [List](#list) | List类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义List控制器
class MyListController extends NodeController {
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    // 创建list节点
    this.rootNode = new FrameNode(uiContext);
    // 创建List
    let listNode = typeNode.createNode(uiContext, 'List');
    listNode.initialize({ space: 3 }).size({ width: '100%', height: '100%' });
    typeNode.getAttribute(listNode, "List")?.friction(0.6);

    // 在list下创建ListItemGroup节点
    let listItemGroupNode = typeNode.createNode(uiContext, 'ListItemGroup');
    listItemGroupNode.initialize({ space: 3 });
    listNode.appendChild(listItemGroupNode);

    // 在ListItemGroup中放入ListItem节点
    let listItemNode1 = typeNode.createNode(uiContext, 'ListItem');
    listItemNode1.initialize({ style: ListItemStyle.NONE }).height(100).borderWidth(1).backgroundColor('#FF00FF');
    let text1 = typeNode.createNode(uiContext, 'Text');
    text1.initialize('ListItem1');
    listItemNode1.appendChild(text1);
    listItemGroupNode.appendChild(listItemNode1);

    // 创建ListItem，添加Text至ListItem，添加至listItemGroup
    let listItemNode2 = typeNode.createNode(uiContext, 'ListItem');
    listItemNode2.initialize({ style: ListItemStyle.CARD }).borderWidth(1).backgroundColor('#FF00FF');
    typeNode.getAttribute(listItemNode2, "ListItem")?.height(100);
    let text2 = typeNode.createNode(uiContext, 'Text');
    text2.initialize('ListItem2');
    listItemNode2.appendChild(text2);
    listItemGroupNode.appendChild(listItemNode2);

    this!.rootNode!.appendChild(listNode);
    return this.rootNode;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myListController: MyListController = new MyListController();

  build() {
    Column({ space: 5 }) {
      Text('ListSample')
      NodeContainer(this.myListController)

    }.width('100%')
  }
}
```

### createListNode<sup>23+</sup>

createListNode(context: UIContext, options?: FrameNodeOptions): List

创建List类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 是 | 创建List类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [List](#list23) | List类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createNode(uiContext);
```

### getEvent('List')<sup>19+</sup>

getEvent(node: FrameNode, nodeType: 'List'): UIListEvent | undefined

获取List节点中持有的UIListEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 19

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取事件时所需的目标节点。 |
| nodeType | 'List' | 是 | 获取List节点类型的滚动事件。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [UIListEvent](./arkui-ts/ts-container-list.md#uilistevent19)&nbsp;\|&nbsp;undefined | List节点类型的滚动事件，若获取失败，则返回undefined。 |

**示例：**

完整示例请参考[滚动事件示例](#滚动事件示例)。

### getListEvent<sup>24+</sup>

getListEvent(node: FrameNode): UIListEvent | undefined

获取List节点中持有的UIListEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取事件时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [UIListEvent](./arkui-ts/ts-container-list.md#uilistevent19)&nbsp;\|&nbsp;undefined | List节点类型的滚动事件，若获取失败，则返回undefined。 |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.getListEvent(node);
```

### getAttribute('List')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'List'): ListAttribute | undefined

获取List节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'List' | 是 | 获取List节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListAttribute&nbsp;\|&nbsp;undefined | List节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

完整示例请参考[createNode('List')](#createnodelist)的示例。

### getListAttribute<sup>24+</sup>

getListAttribute(node: FrameNode): ListAttribute | undefined

获取List节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListAttribute&nbsp;\|&nbsp;undefined | List节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

<!--code_no_check-->

``` ts
typeNode.getListAttribute(node);
```

### bindController('List')<sup>20+</sup>

bindController(node: FrameNode, controller: Scroller, nodeType: 'List'): void

将滚动控制器[Scroller](arkui-ts/ts-container-scroll.md#scroller)绑定到[List](#list)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定滚动控制器的目标节点。 |
| controller | [Scroller](arkui-ts/ts-container-scroll.md#scroller) | 是   | 滚动控制器。 |
| nodeType | 'List' | 是 | 绑定滚动控制器的目标节点的节点类型为List。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. Introduced in API 20 and will not be threw above API 24. [since 20 - 24] |

**示例：**

<!--code_no_check-->

```ts
typeNode.bindController(node, scroller, 'List');
```

### bindListController<sup>24+</sup>

bindListController(node: FrameNode, controller: Scroller): void

将滚动控制器[Scroller](arkui-ts/ts-container-scroll.md#scroller)绑定到[List](#list)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定滚动控制器的目标节点。 |
| controller | [Scroller](arkui-ts/ts-container-scroll.md#scroller) | 是   | 滚动控制器。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |

**示例：**

<!--code_no_check-->

``` ts
typeNode.bindListController(node, scroller);
```

## ListItem

type ListItem = TypedFrameNode&lt;ListItemInterface, ListItemAttribute&gt;

ListItem类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

| 类型                                                       | 说明                                                         |
| ---------------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;ListItemInterface, ListItemAttribute&gt; | 提供ListItem类型FrameNode节点。<br/> ListItemInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为ListItem组件的构造函数类型。 <br/> ListItemAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回ListItem组件的属性设置对象。<br/> ListItemInterface表示ListItem的[接口](./arkui-ts/ts-container-listitem.md#接口)，ListItemAttribute表示ListItem的[属性](./arkui-ts/ts-container-listitem.md#属性)。 |

## ListItemFrameNode<sup>23+</sup>

ListItemFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明ListItem类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(options?: ListItemOptions): ListItemAttribute

该接口用于创建ListItem类型组件的构造参数，用于设置或更新组件的初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [ListItemOptions](./arkui-ts/ts-container-listitem.md#listitemoptions10对象说明) | 否   | 设置ListItem组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListItemAttribute | 返回ListItem组件的属性设置对象。<br/> ListItemAttribute表示ListItem的[属性](./arkui-ts/ts-container-listitem.md#属性)。 |

## ListItem<sup>23+</sup>

type ListItem = ListItemFrameNode

ListItem类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [ListItemFrameNode](#listitemframenode23) | 提供ListItem类型FrameNode节点。 |

### createNode('ListItem')

createNode(context: UIContext, nodeType: 'ListItem'): ListItem

创建ListItem类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'ListItem' | 是 | 创建ListItem类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [ListItem](#listitem) | ListItem类型的FrameNode节点。 |

**示例：**

参考[createNode('List')](#createnodelist)示例。

### createListItemNode<sup>23+</sup>

createListItemNode(context: UIContext, options?: FrameNodeOptions): ListItem

创建ListItem类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 是 | 创建ListItem类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [ListItem](#listitem23) | ListItem类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createNode(uiContext);
```

### getAttribute('ListItem')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'ListItem'): ListItemAttribute | undefined

获取ListItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'ListItem' | 是 | 获取ListItem节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListItemAttribute&nbsp;\|&nbsp;undefined | ListItem节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 

完整示例请参考[createNode('List')](#createnodelist)的示例。

### getListItemAttribute<sup>24+</sup>

getListItemAttribute(node: FrameNode): ListItemAttribute | undefined

获取ListItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListItemAttribute&nbsp;\|&nbsp;undefined | ListItem节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.getListItemAttribute(node);
```

## TextInput
type TextInput = TypedFrameNode&lt;TextInputInterface, TextInputAttribute&gt;

TextInput类型的FrameNode节点类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[TextInput](#textinput23)。

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;TextInputInterface, TextInputAttribute&gt; | 提供TextInput类型FrameNode节点。<br/> TextInputInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为TextInput组件的构造函数类型。 <br/> TextInputAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回TextInput组件的属性设置对象。<br/> TextInputInterface表示TextInput的[接口](./arkui-ts/ts-basic-components-textinput.md#接口)，TextInputAttribute表示TextInput的[属性](./arkui-ts/ts-basic-components-textinput.md#属性)。 |

## TextInput<sup>23+</sup>
type TextInput = TextInputFrameNode

TextInput类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[TextInput](#textinput)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [TextInputFrameNode](#textinputframenode23) | TextInput类型FrameNode节点。 |

## TextInputFrameNode<sup>23+</sup>

TextInputFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[TextInput](./arkui-ts/ts-basic-components-textinput.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value?: TextInputOptions): TextInputAttribute

初始化TextInput组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [TextInputOptions](./arkui-ts/ts-basic-components-textinput.md#textinputoptions对象说明) | 否   | TextInput组件的初始化选项。默认值为空。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextInputAttribute | 返回TextInput组件的属性设置对象。 |

### createNode('TextInput')

createNode(context: UIContext, nodeType: 'TextInput'): TextInput

创建TextInput类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createTextInputNode](#createtextinputnode23)。

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'TextInput' | 是 | 创建TextInput类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [TextInput](#textinput) | TextInput类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建TextInput
    let textInput = typeNode.createNode(uiContext, 'TextInput');
    textInput.initialize({ text: "TextInput" });
    col.appendChild(textInput);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextInput sample')
      NodeContainer(this.myNodeController);
    }
  }
}
```

### createTextInputNode<sup>23+</sup>

createTextInputNode(context: UIContext, options?: FrameNodeOptions): TextInput

创建TextInput类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('TextInput')](#createnodetextinput)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否   | 创建节点的额外选项。默认值继承[FrameNodeOptions](#framenodeoptions24)。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [TextInput](#textinput) | TextInput类型的FrameNode节点。 |

### getAttribute('TextInput')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'TextInput'): TextInputAttribute | undefined

获取TextInput节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[getTextInputAttribute](#gettextinputattribute24)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'TextInput' | 是 | 获取TextInput节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextInputAttribute&nbsp;\|&nbsp;undefined | TextInput节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建TextInput
    let textInput = typeNode.createNode(uiContext, 'TextInput');
    textInput.initialize({ placeholder: 'TextInput placeholderColor' });
    // 获取TextInput的属性
    typeNode.getAttribute(textInput, 'TextInput')?.placeholderColor(Color.Red);
    col.appendChild(textInput);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextInput getAttribute sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### getTextInputAttribute<sup>24+</sup>

getTextInputAttribute(node: FrameNode): TextInputAttribute | undefined

获取[TextInput](#textinput)类型的[FrameNode](./js-apis-arkui-frameNode.md#framenode-1)文本输入框的文本[属性](./arkui-ts/ts-basic-components-textinput.md#属性)（TextInputAttribute）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[getAttribute('TextInput')](#getattributetextinput20)。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextInputAttribute&nbsp;\|&nbsp;undefined | TextInput节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { Entry, Component, Column, NodeContainer, TextInput, FrameNode, Color, ColumnOptions, UIContext } from '@kit.ArkUI';
import { NodeController } from 'arkui.NodeController';
import { typeNode } from 'arkui.FrameNode';

class TextNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);

    let col = typeNode.createColumnNode(uiContext);
    col.initialize({ space: 5 } as ColumnOptions);
    node.appendChild(col);

    let text = typeNode.createTextInputNode(uiContext);
    text.initialize({ text: "Hello" });
    typeNode.getTextInputAttribute(text)?.fontColor(Color.Red)
    col.appendChild(text);

    let text2 = typeNode.createTextInputNode(uiContext);
    text2.initialize({ text: "world" });
    col.appendChild(text2);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private textNodeController: TextNodeController = new TextNodeController();

  build() {
    Column(undefined) {
      NodeContainer(this.textNodeController);
    }
    .height("100%")
    .width("100%")
  }
}
```

![image](figures/getTextInputAttribute_static.jpg)

### bindController('TextInput')<sup>20+</sup>
bindController(node: FrameNode, controller: TextInputController, nodeType: 'TextInput'): void

将输入框控制器[TextInputController](arkui-ts/ts-basic-components-textinput.md#textinputcontroller8)绑定到[TextInput](#textinput)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口从API版本26.0.0开始支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[bindTextInputController](#bindtextinputcontroller24)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定输入框控制器的目标节点。 |
| controller | [TextInputController](arkui-ts/ts-basic-components-textinput.md#textinputcontroller8) | 是   | 输入框控制器。 |
| nodeType | 'TextInput' | 是 | 绑定输入框控制器的目标节点的节点类型为TextInput。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建、初始化TextInput，默认获焦
    let textInput = typeNode.createNode(uiContext, 'TextInput');
    textInput.initialize({ text: "TextInput" })
      .defaultFocus(true)
    col.appendChild(textInput);
    // 绑定TextInputController，设置光标位置
    let controller: TextInputController = new TextInputController();
    typeNode.bindController(textInput, controller, 'TextInput');
    controller.caretPosition(3);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextInput bindController sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### bindTextInputController<sup>24+</sup>

bindTextInputController(node: FrameNode, controller: TextInputController): void

将输入框控制器[TextInputController](arkui-ts/ts-basic-components-textinput.md#textinputcontroller8)绑定到[TextInput](#textinput)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口从API版本26.0.0开始支持声明式方式创建的节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[bindController('TextInput')](#bindcontrollertextinput20)。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定输入框控制器的目标节点。 |
| controller | [TextInputController](arkui-ts/ts-basic-components-textinput.md#textinputcontroller8) | 是   | 输入框控制器。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. |

**示例：**

```ts
import { Entry, Component, Column, NodeContainer, TextInput, TextInputController, FrameNode, Color, ColumnOptions, UIContext } from '@kit.ArkUI';
import { NodeController } from 'arkui.NodeController';
import { typeNode } from 'arkui.FrameNode';

class TextNodeController extends NodeController {
  controller: TextInputController = new TextInputController();

  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);

    let col = typeNode.createColumnNode(uiContext);
    col.initialize({ space: 5 } as ColumnOptions);
    node.appendChild(col);

    let text = typeNode.createTextInputNode(uiContext);
    text.initialize({ text: "Hello world!" });
    typeNode.bindTextInputController(text, this.controller);
    col.appendChild(text);

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private textNodeController: TextNodeController = new TextNodeController();

  build() {
    Column(undefined) {
      NodeContainer(this.textNodeController);
    }
    .height("100%")
    .width("100%")
  }
}
```

![image](figures/bindTextInputController_static.jpg)

## Button

type Button = TypedFrameNode&lt;ButtonInterface, ButtonAttribute&gt;

Button类型的FrameNode节点类型。以子组件模式创建允许添加一个子组件。以label模式创建不可以添加子组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Button<sup>23+</sup>](#button23)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

| 类型                                                   | 说明                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;ButtonInterface, ButtonAttribute&gt; | 提供Button类型FrameNode节点。<br/> ButtonInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Button组件的构造函数类型。 <br/> ButtonAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Button组件的属性设置对象。<br/> 接口入参label不为空时，以label模式创建Button组件，以此模式创建无法包含子组件，并且不允许再设置子组件，否则会抛出异常。且label模式和子组件模式在第一次initialize创建之后无法在后续的initialize进行动态修改，如需要包含子组件，第一次initialize时不要设置label参数。<br/> 以子组件模式创建时，只能包含一个子组件，不能设置多个子组件，否则会抛出异常。<br/> ButtonInterface表示Button的[接口](./arkui-ts/ts-basic-components-button.md#接口)，ButtonAttribute表示Button的[属性](./arkui-ts/ts-basic-components-button.md#属性)。 |

### createNode('Button')

createNode(context: UIContext, nodeType: 'Button'): Button

创建Button类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createButtonNode](#createbuttonnode23)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Button' | 是 | 创建Button类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Button](#button) | Button类型的FrameNode节点。 |

**示例：** 

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Button控制器
class MyButtonController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Button
    let button = typeNode.createNode(uiContext, 'Button')
    button.initialize("This is Button")
      .onClick(() => {
        uiContext.getPromptAction().showToast({ message: "Button clicked" })
      })
    col.appendChild(button)

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myButtonController: MyButtonController = new MyButtonController();

  build() {
    Column({ space: 5 }) {
      Text('ButtonSample')
      NodeContainer(this.myButtonController);

    }.width('100%')
  }
}
```

### getAttribute('Button')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Button'): ButtonAttribute | undefined

获取Button节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Button' | 是 | 获取Button节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ButtonAttribute&nbsp;\|&nbsp;undefined | Button节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Button控制器
class MyButtonController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    let button = typeNode.createNode(uiContext, 'Button')
    button.initialize("This is Button")
      .onClick(() => {
        uiContext.getPromptAction().showToast({ message: "Button clicked" })
      })
    // 获取Button属性
    typeNode.getAttribute(button,'Button')?.buttonStyle(ButtonStyleMode.TEXTUAL)
    col.appendChild(button)

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myButtonController: MyButtonController = new MyButtonController();

  build() {
    Column({ space: 5 }) {
      Text('ButtonSample')
      NodeContainer(this.myButtonController);

    }.width('100%')
  }
}

```
## Button<sup>23+</sup>
type Button = ButtonFrameNode

Button类型的FrameNode节点。以子组件模式创建时允许添加一个子组件，以label模式创建不可以添加子组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Button](#button)。

**ArkTS-Sta起始版本：** 23

| 类型                                                   | 说明                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| [ButtonFrameNode](#buttonframenode23) | 提供Button类型FrameNode节点。|

### createButtonNode<sup>23+</sup>
createButtonNode(context: UIContext, options?: FrameNodeOptions): Button

创建Button类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Button')](#createnodebutton)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。|

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Button](#button23) | Button类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createButtonNode(uiContext);
```

## ButtonFrameNode<sup>23+</sup>

ButtonFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Button类型的FrameNode。

### initialize<sup>23+</sup>
abstract initialize(): ButtonAttribute

初始化空的Button组件。推荐添加子组件，否则Button显示内容为空。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ButtonAttribute | 返回Button组件的属性设置对象。 |

**示例：** 

```ts
import { Entry, Column, Component, Color, NodeContainer, ItemAlign, FlexAlign } from '@ohos.arkui.component'
import { NodeController, FrameNode, typeNode } from '@ohos.arkui.node'
import { UIContext } from '@ohos.arkui.UIContext'

class MyNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);

    let flexNode = typeNode.createNode(uiContext, "Flex");
    flexNode.initialize({ alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center })
      .size({ width: 100, height: 100 })
      .backgroundColor(Color.Gray)

    let button = typeNode.createButtonNode(uiContext);
    button.initialize();
    flexNode.appendChild(button);
    this!.rootNode!.appendChild(flexNode);
    return this.rootNode;
  }
}

@Entry
@Component
struct MyStateSample {
  private controller: MyNodeController = new MyNodeController()

  build() {
    Column(undefined) {
      NodeContainer(this.controller)
    }
  }
}
```
![image](figures/buttonInitialize1.png)

## ListItemGroup

type ListItemGroup = TypedFrameNode&lt;ListItemGroupInterface, ListItemGroupAttribute&gt;

ListItemGroup类型的FrameNode节点类型。只允许添加[ListItem](./arkui-ts/ts-container-listitem.md)类型子组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;ListItemGroupInterface, ListItemGroupAttribute&gt; | 提供ListItemGroup类型FrameNode节点。<br/> ListItemGroupInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为ListItemGroup组件的构造函数类型。 <br/> ListItemGroupAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回ListItemGroup组件的属性设置对象。<br/> ListItemGroupInterface表示ListItemGroup的[接口](./arkui-ts/ts-container-listitem.md#接口)，ListItemGroupAttribute表示ListItemGroup的[属性](./arkui-ts/ts-container-listitem.md#属性)。 |

## ListItemGroupFrameNode<sup>23+</sup>

ListItemGroupFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明ListItemGroup类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(options?: ListItemGroupOptions): ListItemGroupAttribute

该接口用于创建ListItemGroup类型组件的构造参数，用于设置或更新组件的初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [ListItemGroupOptions](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明) | 否   | 设置ListItemGroup组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListItemGroupAttribute | 返回ListItemGroup组件的属性设置对象。<br/> ListItemGroupAttribute表示ListItemGroup的[属性](./arkui-ts/ts-container-listitem.md#属性)。 |

## ListItemGroup<sup>23+</sup>

type ListItemGroup = ListItemGroupFrameNode

ListItemGroup类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [ListItemGroupFrameNode](#listitemgroupframenode23) | 提供ListItemGroup类型FrameNode节点。 |

### createNode('ListItemGroup')

createNode(context: UIContext, nodeType: 'ListItemGroup'): ListItemGroup

创建ListItemGroup类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'ListItemGroup' | 是 | 创建ListItemGroup类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [ListItemGroup](#listitemgroup) | ListItemGroup类型的FrameNode节点。 |

**示例：**

参考[createNode('List')](#createnodelist)示例。

### createListItemGroupNode<sup>23+</sup>

createListItemGroupNode(context: UIContext, options?: FrameNodeOptions): ListItemGroup

创建ListItemGroup类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 是 | 创建ListItemGroup类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [ListItemGroup](#listitemgroup23) | ListItemGroup类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createNode(uiContext);
```

### getAttribute('ListItemGroup')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'ListItemGroup'): ListItemGroupAttribute | undefined

获取ListItemGroup节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'ListItemGroup' | 是 | 获取ListItemGroup节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListItemGroupAttribute&nbsp;\|&nbsp;undefined | ListItemGroup节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

<!--code_no_check-->

```ts
typeNode.getAttribute(node, 'ListItemGroup');
```

### getListItemGroupAttribute<sup>24+</sup>

getListItemGroupAttribute(node: FrameNode): ListItemGroupAttribute | undefined

获取ListItemGroup节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ListItemGroupAttribute&nbsp;\|&nbsp;undefined | ListItemGroup节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

<!--code_no_check-->

``` ts
typeNode.getListItemGroupAttribute(node);
```

## WaterFlow

type WaterFlow = TypedFrameNode&lt;WaterFlowInterface, WaterFlowAttribute&gt;

WaterFlow类型的FrameNode节点类型。只允许添加[FlowItem](./arkui-ts/ts-container-flowitem.md)类型子组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;WaterFlowInterface, WaterFlowAttribute&gt; | 提供[WaterFlow](#waterflow)类型FrameNode节点。<br/> WaterFlowInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为WaterFlow组件的构造函数类型。 <br/> WaterFlowAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回WaterFlow组件的属性设置对象。<br/> WaterFlowInterface表示WaterFlow的[接口](./arkui-ts/ts-container-waterflow.md#接口)，WaterFlowAttribute表示WaterFlow的[属性](./arkui-ts/ts-container-waterflow.md#属性)。 |

## WaterFlowFrameNode<sup>23+</sup>

WaterFlowFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明WaterFlow类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(options?: WaterFlowOptions): WaterFlowAttribute

该接口用于创建WaterFlow类型组件的构造参数，用于设置或更新组件的初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [WaterFlowOptions](./arkui-ts/ts-container-waterflow.md#waterflowoptions对象说明) | 否   | 设置WaterFlow组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| WaterFlowAttribute | 返回WaterFlow组件的属性设置对象。<br/> WaterFlowAttribute表示WaterFlow的[属性](./arkui-ts/ts-container-waterflow.md#属性)。 |

## WaterFlow<sup>23+</sup>

type WaterFlow = WaterFlowFrameNode

WaterFlow类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [WaterFlowFrameNode](#waterflowframenode23) | 提供WaterFlow类型FrameNode节点。 |

### createNode('WaterFlow')

createNode(context: UIContext, nodeType: 'WaterFlow'): WaterFlow

创建WaterFlow类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'WaterFlow' | 是 | 创建WaterFlow类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [WaterFlow](#waterflow) | WaterFlow类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义WaterFlow控制器
class MyWaterFlowController extends NodeController {
  public rootNode: FrameNode | null = null;
  private minHeight: number = 80;
  private maxHeight: number = 180;

  // 计算FlowItem高
  private getHeight() {
    let ret = Math.floor(Math.random() * this.maxHeight);
    return (ret > this.minHeight ? ret : this.minHeight);
  }

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    // 创建WaterFlow并设置属性
    let waterFlowNode = typeNode.createNode(uiContext, 'WaterFlow');
    waterFlowNode.attribute.size({ width: '100%', height: '100%' })
      .columnsTemplate('1fr 1fr')
      .columnsGap(10)
      .rowsGap(5);
    typeNode.getAttribute(waterFlowNode, "WaterFlow")?.friction(0.6);

    // 创建FlowItem并设置属性
    for (let i = 0; i < 20; i++) {
      let flowItemNode = typeNode.createNode(uiContext, 'FlowItem');
      flowItemNode.attribute.size({ height: this.getHeight() });
      typeNode.getAttribute(flowItemNode, "FlowItem")?.width('100%');
      waterFlowNode.appendChild(flowItemNode);

      let text = typeNode.createNode(uiContext, 'Text');
      text.initialize('N' + i)
        .size({ width: '100%', height: '100%' })
        .textAlign(TextAlign.Center)
        .backgroundColor(0xF9CF93);
      flowItemNode.appendChild(text);
    }

    this!.rootNode!.appendChild(waterFlowNode);
    return this.rootNode;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myWaterFlowController: MyWaterFlowController = new MyWaterFlowController();

  build() {
    Column({ space: 5 }) {
      Text('WaterFlowSample')
      NodeContainer(this.myWaterFlowController);

    }.width('100%')
  }
}
```

### createWaterFlowNode<sup>23+</sup>

createWaterFlowNode(context: UIContext, options?: FrameNodeOptions): WaterFlow

创建WaterFlow类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 是 | 创建WaterFlow类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [WaterFlow](#waterflow23) | WaterFlow类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createNode(uiContext);
```

### getEvent('WaterFlow')<sup>19+</sup>

getEvent(node: FrameNode, nodeType: 'WaterFlow'): UIWaterFlowEvent | undefined

获取[WaterFlow](#waterflow)节点中持有的UIWaterFlowEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 19

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取事件时所需的目标节点。 |
| nodeType | 'WaterFlow' | 是 | 获取WaterFlow节点类型的滚动事件。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [UIWaterFlowEvent](./arkui-ts/ts-container-waterflow.md#uiwaterflowevent19)&nbsp;\|&nbsp;undefined | WaterFlow节点类型的滚动事件，若获取失败，则返回undefined。 |

**示例：**

完整示例请参考[滚动事件示例](#滚动事件示例)。

### getWaterFlowEvent<sup>24+</sup>

getWaterFlowEvent(node: FrameNode): UIWaterFlowEvent | undefined

获取WaterFlow节点中持有的UIWaterFlowEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取事件时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [UIWaterFlowEvent](./arkui-ts/ts-container-waterflow.md#uiwaterflowevent19)&nbsp;\|&nbsp;undefined | List节点类型的滚动事件，若获取失败，则返回undefined。 |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.getWaterFlowEvent(node);
```

### getAttribute('WaterFlow')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'WaterFlow'): WaterFlowAttribute | undefined

获取WaterFlow节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'WaterFlow' | 是 | 获取WaterFlow节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| WaterFlowAttribute&nbsp;\|&nbsp;undefined | WaterFlow节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

完整示例请参考[createNode('WaterFlow')](#createnodewaterflow)的示例。

### getWaterFlowAttribute<sup>24+</sup>

getWaterFlowAttribute(node: FrameNode): WaterFlowAttribute | undefined

获取WaterFlow节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| WaterFlowAttribute&nbsp;\|&nbsp;undefined | WaterFlow节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

<!--code_no_check-->

``` ts
typeNode.getWaterFlowAttribute(node);
```

### bindController('WaterFlow')<sup>20+</sup>

bindController(node: FrameNode, controller: Scroller, nodeType: 'WaterFlow'): void

将滚动控制器[Scroller](arkui-ts/ts-container-scroll.md#scroller)绑定到[WaterFlow](#waterflow)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定滚动控制器的目标节点。 |
| controller | [Scroller](arkui-ts/ts-container-scroll.md#scroller) | 是   | 滚动控制器。 |
| nodeType | 'WaterFlow' | 是 | 绑定滚动控制器的目标节点的节点类型为WaterFlow。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. Introduced in API 20 and will not be threw above API 24. [since 20 - 24] |

**示例：** 

<!--code_no_check-->

```ts
typeNode.bindController(node, scroller, 'WaterFlow');
```

### bindWaterFlowController<sup>24+</sup>

bindWaterFlowController(node: FrameNode, controller: Scroller): void

将滚动控制器[Scroller](arkui-ts/ts-container-scroll.md#scroller)绑定到[WaterFlow](#waterflow)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定滚动控制器的目标节点。 |
| controller | [Scroller](arkui-ts/ts-container-scroll.md#scroller) | 是   | 滚动控制器。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.bindWaterFlowController(node, scroller);
```

## FlowItem

type FlowItem = TypedFrameNode&lt;FlowItemInterface, FlowItemAttribute&gt;

FlowItem类型的FrameNode节点类型。允许添加一个子组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

| 类型                                                       | 说明                                                         |
| ---------------------------------------------------------- | ------------------------------------------------------------ |
| TypedFrameNode&lt;FlowItemInterface, FlowItemAttribute&gt; | 提供FlowItem类型FrameNode节点。<br/> FlowItemInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为FlowItem组件的构造函数类型。 <br/> FlowItemAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回FlowItem组件的属性设置对象。<br/> FlowItemInterface表示FlowItem的[接口](./arkui-ts/ts-container-flowitem.md#接口)，FlowItemAttribute表示FlowItem的[属性](./arkui-ts/ts-container-flowitem.md#属性)。 |

## FlowItemFrameNode<sup>23+</sup>

FlowItemFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明FlowItem类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(): FlowItemAttribute

该接口用于创建FlowItem类型组件的构造参数，用于设置或更新组件的初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| FlowItemAttribute | 返回FlowItem组件的属性设置对象。<br/> FlowItemAttribute表示FlowItem的[属性](./arkui-ts/ts-container-flowitem.md#属性)。 |

## FlowItem<sup>23+</sup>

type FlowItem = FlowItemFrameNode

FlowItem类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [FlowItemFrameNode](#flowitemframenode23) | 提供FlowItem类型FrameNode节点。 |

### createNode('FlowItem')

createNode(context: UIContext, nodeType: 'FlowItem'): FlowItem

创建FlowItem类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'FlowItem' | 是 | 创建FlowItem类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [FlowItem](#flowitem) | FlowItem类型的FrameNode节点。 |

**示例：**

参考[createNode('WaterFlow')](#createnodewaterflow)示例。

### createFlowItemNode<sup>23+</sup>

createFlowItemNode(context: UIContext, options?: FrameNodeOptions): FlowItem

创建FlowItem类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 是 | 创建FlowItem类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [FlowItem](#flowitem23) | FlowItem类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createNode(uiContext);
```

### getAttribute('FlowItem')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'FlowItem'): FlowItemAttribute | undefined

获取FlowItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'FlowItem' | 是 | 获取FlowItem节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| FlowItemAttribute&nbsp;\|&nbsp;undefined | FlowItem节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

完整示例请参考[createNode('WaterFlow')](#createnodewaterflow)的示例。

### getFlowItemAttribute<sup>24+</sup>

getFlowItemAttribute(node: FrameNode): FlowItemAttribute | undefined

获取FlowItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| FlowItemAttribute&nbsp;\|&nbsp;undefined | FlowItem节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

<!--code_no_check-->

``` ts
typeNode.getFlowItemAttribute(node);
```

## XComponent

type XComponent = TypedFrameNode&lt;XComponentInterface, XComponentAttribute&gt;

XComponent类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| TypedFrameNode&lt;XComponentInterface, XComponentAttribute&gt; | 提供XComponent类型FrameNode节点。<br/> XComponentInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为XComponent组件的构造函数类型。 <br/> XComponentAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回XComponent组件的属性设置对象。<br/> XComponentInterface表示XComponent的[接口](./arkui-ts/ts-basic-components-xcomponent.md#接口)，XComponentAttribute表示XComponent的[属性](./arkui-ts/ts-basic-components-xcomponent.md#属性)。 |

### createNode('XComponent')

createNode(context: UIContext, nodeType: 'XComponent'): XComponent

创建XComponent类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'XComponent' | 是 | 创建XComponent类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [XComponent](#xcomponent) | XComponent类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col);
    // 创建XComponent
    let xcomponent = typeNode.createNode(uiContext, 'XComponent');
    xcomponent.attribute.backgroundColor(Color.Red);
    col.appendChild(xcomponent);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('XComponentSample')
      NodeContainer(this.myNodeController)
    }.width('100%')
  }
}
```

### createNode('XComponent')

createNode(context: UIContext, nodeType: 'XComponent', options: XComponentOptions): XComponent

按照options中的配置参数创建XComponent类型的FrameNode节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'XComponent' | 是 | 创建XComponent类型的节点。 |
| options | [XComponentOptions](./arkui-ts/ts-basic-components-xcomponent.md#xcomponentoptions12) | 是 | 定义XComponent的具体配置参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [XComponent](#xcomponent) | XComponent类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  controller: XComponentController = new XComponentController();
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col);
    // 设置XComponent参数对象
    let options: XComponentOptions = {
      type: XComponentType.SURFACE,
      controller: this.controller
    };
    // 创建XComponent
    let xcomponent = typeNode.createNode(uiContext, 'XComponent', options);
    xcomponent.attribute.backgroundColor(Color.Red);
    col.appendChild(xcomponent);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('XComponentSample')
      NodeContainer(this.myNodeController)
    }.width('100%')
  }
}
```

### createNode('XComponent')<sup>19+</sup>

createNode(context: UIContext, nodeType: 'XComponent', parameters: NativeXComponentParameters): XComponent

按照parameters中的配置参数创建XComponent类型的FrameNode节点。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'XComponent' | 是 | 创建XComponent类型的节点。 |
| parameters | [NativeXComponentParameters](./arkui-ts/ts-basic-components-xcomponent.md#nativexcomponentparameters19) | 是 | 定义XComponent的具体配置参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [XComponent](#xcomponent) | XComponent类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  controller: XComponentController = new XComponentController();
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col);
    let parameters: NativeXComponentParameters = {
      type: XComponentType.SURFACE
    };
    // 创建XComponent
    let xcomponent = typeNode.createNode(uiContext, 'XComponent', parameters);
    xcomponent.attribute.backgroundColor(Color.Red);
    col.appendChild(xcomponent);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('XComponentSample')
      NodeContainer(this.myNodeController)
    }.width('100%')
  }
}
```

## XComponent<sup>23+</sup>
type XComponent = XComponentFrameNode

[XComponent](./arkui-ts/ts-basic-components-xcomponent.md)类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [XComponentFrameNode](#xcomponentframenode23) | 提供[XComponent](./arkui-ts/ts-basic-components-xcomponent.md)类型FrameNode节点。 |

### createXComponentNodeWithOptions<sup>23+</sup>
createXComponentNodeWithOptions(context: UIContext, value: XComponentOptions, options?: FrameNodeOptions): XComponent

按照value中的配置参数创建XComponent类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| value | [XComponentOptions](./arkui-ts/ts-basic-components-xcomponent.md#xcomponentoptions12) | 是 | 定义XComponent的具体配置参数，包括组件类型等。 |
| options<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [XComponent](#xcomponent23) | XComponent类型的FrameNode节点。 |

**示例：**

ArkTS-Sta示例：

```ts
import {
  Entry,
  Column,
  Color,
  Component,
  NodeContainer,
  UIContext,
  XComponentController,
  XComponentType,
  XComponentParameters,
  XComponentOptions
} from '@kit.ArkUI';
import {
  FrameNode,
  NodeController,
  typeNode
} from "@ohos.arkui.node";

class MyNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);

    const opt = {
      type: XComponentType.SURFACE,
      controller: new XComponentController()
    } as XComponentOptions;
    let xcomponentNode: typeNode.XComponent = typeNode.createXComponentNodeWithOptions(uiContext, opt);

    xcomponentNode!.attribute
      .width(100)
      .height(100)
      .backgroundColor(Color.Gray)

    this!.rootNode!.appendChild(xcomponentNode);
    return this.rootNode;
  }

  dispose(): void {
    if (this.rootNode) {
      this.rootNode!.clearChildren();
      this.rootNode!.dispose();
    }
  }
}

@Entry
@Component
struct MyStateSample {
  private controller: MyNodeController = new MyNodeController();
  aboutToDisappear(): void {
    this.controller.dispose();
  }
  build() {
    Column(undefined) {
      NodeContainer(this.controller)
    }
  }
}
```

## XComponentFrameNode<sup>23+</sup>

XComponentFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[XComponent](./arkui-ts/ts-basic-components-xcomponent.md)类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value: XComponentParameters): XComponentAttribute

使用XComponentParameters类型的参数初始化XComponent组件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | XComponentParameters | 是   | XComponent组件参数，包括组件类型等。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| XComponentAttribute | 返回XComponent组件的属性设置对象。 |

**示例：**

ArkTS-Sta示例：

```ts
import {
  Entry,
  Column,
  Color,
  Component,
  NativeXComponentPointer,
  NodeContainer,
  UIContext,
  XComponentController,
  XComponentType,
  XComponentParameters,
  XComponentOptions
} from '@kit.ArkUI';
import {
  FrameNode,
  NodeController,
  typeNode
} from "@ohos.arkui.node";

class MyNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);

    const opt = {
      type: XComponentType.SURFACE,
      controller: new XComponentController()
    } as XComponentOptions;
    let xcomponentNode: typeNode.XComponent = typeNode.createXComponentNodeWithOptions(uiContext, opt);

    const param = {
      id: 'xcomponentId',
      type: XComponentType.SURFACE,
      nativeXComponentHandler: (ptr: NativeXComponentPointer) => {}
    } as XComponentParameters;
    xcomponentNode!.initialize(param)
      .width(100)
      .height(100)
      .backgroundColor(Color.Gray)

    this!.rootNode!.appendChild(xcomponentNode);
    return this.rootNode;
  }

  dispose(): void {
    if (this.rootNode) {
      this.rootNode!.clearChildren();
      this.rootNode!.dispose();
    }
  }
}

@Entry
@Component
struct MyStateSample {
  private controller: MyNodeController = new MyNodeController();
  aboutToDisappear(): void {
    this.controller.dispose();
  }
  build() {
    Column(undefined) {
      NodeContainer(this.controller)
    }
  }
}
```

### createXComponentNodeWithNativeParameters<sup>23+</sup>
createXComponentNodeWithNativeParameters(context: UIContext, parameters: NativeXComponentParameters, options?: FrameNodeOptions): XComponent

按照parameters中的配置参数创建XComponent类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| parameters | [NativeXComponentParameters](./arkui-ts/ts-basic-components-xcomponent.md#nativexcomponentparameters19) | 是 | 定义XComponent的具体配置参数，包括组件类型等。 |
| options<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [XComponent](#xcomponent23) | XComponent类型的FrameNode节点。 |

**示例：**

ArkTS-Sta示例：

```ts
import {
  Entry,
  Column,
  Color,
  Component,
  NativeXComponentParameters,
  NodeContainer,
  UIContext,
  XComponentType
} from '@kit.ArkUI';
import {
  FrameNode,
  NodeController,
  typeNode
} from "@ohos.arkui.node";

class MyNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);

    const param = {
      type: XComponentType.SURFACE
    } as NativeXComponentParameters;
    let xcomponentNode: typeNode.XComponent = typeNode.createXComponentNodeWithNativeParameters(uiContext, param);

    xcomponentNode!.attribute
      .width(100)
      .height(100)
      .backgroundColor(Color.Gray)

    this!.rootNode!.appendChild(xcomponentNode);
    return this.rootNode;
  }

  dispose(): void {
    if (this.rootNode) {
      this.rootNode!.clearChildren();
      this.rootNode!.dispose();
    }
  }
}

@Entry
@Component
struct MyStateSample {
  private controller: MyNodeController = new MyNodeController();
  aboutToDisappear(): void {
    this.controller.dispose();
  }
  build() {
    Column(undefined) {
      NodeContainer(this.controller)
    }
  }
}
```

### createXComponentNodeDefault<sup>23+</sup>
createXComponentNodeDefault(context: UIContext, options?: FrameNodeOptions): XComponent

创建XComponent类型的FrameNode。通过此接口创建的XComponent组件为[XComponentType.SURFACE](./arkui-ts/ts-appendix-enums.md#xcomponenttype10)类型，且无法绑定XComponentController，推荐使用[createXComponentNodeWithOptions](#createxcomponentnodewithoptions23)。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [XComponent](#xcomponent23) | XComponent类型的FrameNode节点。 |

**示例：**

ArkTS-Sta示例：

```ts
import {
  Entry,
  Column,
  Color,
  Component,
  NodeContainer,
  UIContext,
  XComponentType
} from '@kit.ArkUI';
import {
  FrameNode,
  NodeController,
  typeNode
} from "@ohos.arkui.node";

class MyNodeController extends NodeController {
  public uiContext: UIContext | null = null;
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    this.rootNode = new FrameNode(uiContext);

    let xcomponentNode: typeNode.XComponent = typeNode.createXComponentNodeDefault(uiContext);

    xcomponentNode!.attribute
      .width(100)
      .height(100)
      .backgroundColor(Color.Gray)

    this!.rootNode!.appendChild(xcomponentNode);
    return this.rootNode;
  }

  dispose(): void {
    if (this.rootNode) {
      this.rootNode!.clearChildren();
      this.rootNode!.dispose();
    }
  }
}

@Entry
@Component
struct MyStateSample {
  private controller: MyNodeController = new MyNodeController();
  aboutToDisappear(): void {
    this.controller.dispose();
  }
  build() {
    Column(undefined) {
      NodeContainer(this.controller)
    }
  }
}
```


### getAttribute('XComponent')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'XComponent'): XComponentAttribute | undefined

获取XComponent节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'XComponent' | 是 | 获取XComponent节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| XComponentAttribute&nbsp;\|&nbsp;undefined | XComponent节点类型的属性，若获取失败，则返回undefined。<br/> XComponentAttribute表示XComponent的[属性](./arkui-ts/ts-basic-components-xcomponent.md#属性)。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.getAttribute(node, 'XComponent');
```

### createXComponentNodeDefault<sup>23+</sup>

createXComponentNodeDefault(context: UIContext, options?: FrameNodeOptions): XComponent

创建XComponent类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| --- | --- | --- | --- |
| context | [UIContext](arkts-apis-uicontext-uicontext.md) | 是 | UIContext实例。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否 | FrameNode创建的配置选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [XComponent](#xcomponent) | XComponent类型的FrameNode节点。 |

### createXComponentNodeWithOptions<sup>23+</sup>

createXComponentNodeWithOptions(context: UIContext, value: XComponentOptions, options?: FrameNodeOptions): XComponent

按照options中的配置参数创建XComponent类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| --- | --- | --- | --- |
| context | [UIContext](arkts-apis-uicontext-uicontext.md) | 是 | UIContext实例。 |
| value | [XComponentOptions](./arkui-ts/ts-basic-components-xcomponent.md#xcomponentoptions12) | 是 | 定义XComponent的具体配置参数。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否 | FrameNode创建的配置选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [XComponent](#xcomponent) | XComponent类型的FrameNode节点。 |

### createXComponentNodeWithNativeParameters<sup>23+</sup>

createXComponentNodeWithNativeParameters(context: UIContext, parameters: NativeXComponentParameters, options?: FrameNodeOptions): XComponent

按照parameters中的配置参数创建XComponent类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| --- | --- | --- | --- |
| context | [UIContext](arkts-apis-uicontext-uicontext.md) | 是 | UIContext实例。 |
| parameters | [NativeXComponentParameters](./arkui-ts/ts-basic-components-xcomponent.md#nativexcomponentparameters19) | 是 | 定义XComponent的具体配置参数。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否 | FrameNode创建的配置选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [XComponent](#xcomponent) | XComponent类型的FrameNode节点。 |

### getXComponentAttribute<sup>23+</sup>

getXComponentAttribute(node: FrameNode): XComponentAttribute | undefined

获取XComponent节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| --- | --- | --- | --- |
| node | [FrameNode](./js-apis-arkui-frameNode.md#framenode-1) | 是 | 获取属性时所需的目标节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| XComponentAttribute&nbsp;\|&nbsp;undefined | XComponent节点类型的属性，若获取失败，则返回undefined。<br/> XComponentAttribute表示XComponent的[属性](./arkui-ts/ts-basic-components-xcomponent.md#属性)。 |

## FrameNodeOptions<sup>24+</sup>

FrameNode创建的配置选项。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| supportMultiThread | boolean | 否 | 是否支持多线程操作。设置为true时，节点可以安全地在多线程场景中使用。 |

## QRCode<sup>14+</sup>

type QRCode = TypedFrameNode&lt;QRCodeInterface, QRCodeAttribute&gt;

QRCode类型的FrameNode节点类型。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[QRCode](#qrcode23)。

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;QRCodeInterface, QRCodeAttribute&gt; | 提供QRCode类型FrameNode节点。<br/> QRCodeInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为QRCode组件的构造函数类型。 <br/> QRCodeAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回QRCode组件的属性设置对象。<br/> QRCodeInterface表示QRCode的[接口](./arkui-ts/ts-basic-components-qrcode.md#接口)，QRCodeAttribute表示QRCode的[属性](./arkui-ts/ts-basic-components-qrcode.md#属性)。 |

## QRCode<sup>23+</sup>

type QRCode = QRCodeFrameNode

QRCode类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[QRCode](#qrcode14)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [QRCodeFrameNode](#qrcodeframenode23) | QRCode类型FrameNode节点。 |

## QRCodeFrameNode<sup>23+</sup>

QRCodeFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[QRCode](./arkui-ts/ts-basic-components-qrcode.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value: string): QRCodeAttribute

初始化QRCode组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | string | 是   | 二维码内容。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| QRCodeAttribute | 返回QRCode组件的属性设置对象。 |

### createNode('QRCode')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'QRCode'): QRCode

创建QRCode类型的FrameNode节点。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createQRCodeNode](#createqrcodenode23)。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'QRCode' | 是 | 创建QRCode类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [QRCode](#qrcode14) | QRCode类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
typeNode.createNode(uiContext, 'QRCode');
```

### createQRCodeNode<sup>23+</sup>

createQRCodeNode(context: UIContext): QRCode

创建QRCode类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('QRCode')](#createnodeqrcode14)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [QRCode](#qrcode23) | QRCode类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
typeNode.createQRCodeNode(uiContext);
```

## Badge<sup>14+</sup>

type Badge = TypedFrameNode&lt;BadgeInterface, BadgeAttribute&gt;

Badge类型的FrameNode节点类型。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Badge](#badge23)。

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;BadgeInterface, BadgeAttribute&gt; | 提供Badge类型FrameNode节点。<br/> BadgeInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Badge组件的构造函数类型。 <br/> BadgeAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Badge组件的属性设置对象。<br/> BadgeInterface表示Badge的[接口](./arkui-ts/ts-container-badge.md#接口)，BadgeAttribute表示Badge的[属性](./arkui-ts/ts-container-badge.md#属性)。 |

## Badge<sup>23+</sup>

type Badge = BadgeFrameNode

Badge类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Badge](#badge14)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [BadgeFrameNode](#badgeframenode23) | Badge类型FrameNode节点。 |

## BadgeFrameNode<sup>23+</sup>

BadgeFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Badge](./arkui-ts/ts-container-badge.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value: BadgeParamWithNumber): BadgeAttribute

初始化数字Badge组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [BadgeParamWithNumber](./arkui-ts/ts-container-badge.md#badgeparamwithnumber对象说明) | 是   | Badge组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| BadgeAttribute | 返回Badge组件的属性设置对象。 |

### initialize<sup>23+</sup>

abstract initialize(value: BadgeParamWithString): BadgeAttribute

初始化字符串Badge组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [BadgeParamWithString](./arkui-ts/ts-container-badge.md#badgeparamwithstring对象说明) | 是   | Badge组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| BadgeAttribute | 返回Badge组件的属性设置对象。 |

### createNode('Badge')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'Badge'): Badge

创建Badge类型的FrameNode节点。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createBadgeNode](#createbadgenode23)。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Badge' | 是 | 创建Badge类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Badge](#badge14) | Badge类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
typeNode.createNode(uiContext, 'Badge');
```

### createBadgeNode<sup>23+</sup>

export function createBadgeNode(context: UIContext): Badge

创建Badge类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Badge')](#createnodebadge14)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Badge](#badge23) | Badge类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
typeNode.createBadgeNode(uiContext);
```

## Grid<sup>14+</sup>

type Grid = TypedFrameNode&lt;GridInterface, GridAttribute&gt;

Grid类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;GridInterface, GridAttribute&gt; | 提供Grid类型FrameNode节点。<br/> GridInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Grid组件的构造函数类型。 <br/> GridAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Grid组件的属性设置对象。<br/> GridInterface表示Grid的[接口](./arkui-ts/ts-container-grid.md#接口)，GridAttribute表示Grid的[属性](./arkui-ts/ts-container-grid.md#属性)。 |

## GridFrameNode<sup>23+</sup>

GridFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Grid类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(scroller?: Scroller, layoutoptions?: GridLayoutOptions): GridAttribute

该接口用于创建Grid类型组件的构造参数，用于设置或更新组件的初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| scroller | [Scroller](./arkui-ts/ts-container-scroll.md#scroller) | 否   | 滚动控制器。 |
| layoutoptions | [GridLayoutOptions](./arkui-ts/ts-container-grid.md#gridlayoutoptions10对象说明) | 否   | 设置Grid组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| GridAttribute | 返回Grid组件的属性设置对象。<br/> GridAttribute表示Grid的[属性](./arkui-ts/ts-container-grid.md#属性)。 |

## Grid<sup>23+</sup>

type Grid = GridFrameNode

Grid类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [GridFrameNode](#gridframenode23) | 提供Grid类型FrameNode节点。 |

### createNode('Grid')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'Grid'): Grid

创建Grid类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Grid' | 是 | 创建Grid类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Grid](#grid14) | Grid类型的FrameNode节点。 |

**示例：** 

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Grid控制器
class MyGridController extends NodeController {
  public rootNode: FrameNode | null = null;
  private scroller: Scroller = new Scroller();

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    // 创建Grid设置属性
    let gridNode = typeNode.createNode(uiContext, 'Grid');
    gridNode.initialize(this.scroller, { regularSize: [1, 1] })
      .size({ width: '90%', height: 300 })
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10);
    typeNode.getAttribute(gridNode, "Grid")?.friction(0.6);

    // 创建GridItem并设置属性
    for (let i = 0; i < 25; i++) {
      let gridItemNode = typeNode.createNode(uiContext, 'GridItem');
      gridItemNode.initialize({ style: GridItemStyle.NONE }).size({ height: '100%' });
      typeNode.getAttribute(gridItemNode, "GridItem")?.width('100%');

      let text = typeNode.createNode(uiContext, 'Text');
      text.initialize((i % 5).toString())
        .size({ width: '100%', height: '100%' })
        .textAlign(TextAlign.Center)
        .backgroundColor(0xF9CF93);
      gridItemNode.appendChild(text);
      gridNode.appendChild(gridItemNode);
    }

    this!.rootNode!.appendChild(gridNode);
    return this.rootNode;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myGridController: MyGridController = new MyGridController();

  build() {
    Column({ space: 5 }) {
      Text('GridSample')
      NodeContainer(this.myGridController)

    }.width('100%')
  }
}
```

### createGridNode<sup>23+</sup>

createGridNode(context: UIContext, options?: FrameNodeOptions): Grid

创建Grid类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 是 | 创建Grid类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Grid](#grid23) | Grid类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createNode(uiContext);
```

### getEvent('Grid')<sup>19+</sup>

getEvent(node: FrameNode, nodeType: 'Grid'): UIGridEvent | undefined

获取Grid节点中持有的UIGridEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 19

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取事件时所需的目标节点。 |
| nodeType | 'Grid' | 是 | 获取Grid节点类型的滚动事件。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [UIGridEvent](./arkui-ts/ts-container-grid.md#uigridevent19)&nbsp;\|&nbsp;undefined | Grid节点类型的滚动事件，若获取失败，则返回undefined。 |

**示例：** 

完整示例请参考[滚动事件示例](#滚动事件示例)。

### getGridEvent<sup>24+</sup>

getGridEvent(node: FrameNode): UIGridEvent | undefined

获取Grid节点中持有的UIGridEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取事件时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [UIGridEvent](./arkui-ts/ts-container-grid.md#uigridevent19)&nbsp;\|&nbsp;undefined | Grid节点类型的滚动事件，若获取失败，则返回undefined。 |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.getGridEvent(node);
```

### getAttribute('Grid')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Grid'): GridAttribute | undefined

获取Grid节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Grid' | 是 | 获取Grid节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| GridAttribute&nbsp;\|&nbsp;undefined | Grid节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 

完整示例请参考[createNode('Grid')](#createnodegrid14)的示例。

### getGridAttribute<sup>24+</sup>

getGridAttribute(node: FrameNode): GridAttribute | undefined

获取Grid节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| GridAttribute&nbsp;\|&nbsp;undefined | Grid节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.getGridAttribute(node);
```

### bindController('Grid')<sup>20+</sup>

bindController(node: FrameNode, controller: Scroller, nodeType: 'Grid'): void

将滚动控制器[Scroller](arkui-ts/ts-container-scroll.md#scroller)绑定到[Grid](#grid14)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定滚动控制器的目标节点。 |
| controller | [Scroller](arkui-ts/ts-container-scroll.md#scroller) | 是   | 滚动控制器。 |
| nodeType | 'Grid' | 是 | 绑定滚动控制器的目标节点的节点类型为Grid。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. Introduced in API 20 and will not be threw above API 24. [since 20 - 24] |

**示例：** 

<!--code_no_check-->

```ts
typeNode.bindController(node, scroller, 'Grid');
```

### bindGridController<sup>24+</sup>

bindGridController(node: FrameNode, controller: Scroller): void

将滚动控制器[Scroller](arkui-ts/ts-container-scroll.md#scroller)绑定到[Grid](#grid14)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定滚动控制器的目标节点。 |
| controller | [Scroller](arkui-ts/ts-container-scroll.md#scroller) | 是   | 滚动控制器。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.bindGridController(node, scroller);
```

## GridItem<sup>14+</sup>

type GridItem = TypedFrameNode&lt;GridItemInterface, GridItemAttribute&gt;

GridItem类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;GridItemInterface, GridItemAttribute&gt; | 提供GridItem类型FrameNode节点。<br/> GridItemInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为GridItem组件的构造函数类型。 <br/> GridItemAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回GridItem组件的属性设置对象。<br/> GridItemInterface表示GridItem的[接口](./arkui-ts/ts-container-griditem.md#接口)，GridItemAttribute表示GridItem的[属性](./arkui-ts/ts-container-griditem.md#属性)。 |

## GridItemFrameNode<sup>23+</sup>

GridItemFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明GridItem类型的FrameNode。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(options?: GridItemOptions): GridItemAttribute

该接口用于创建GridItem类型组件的构造参数，用于设置或更新组件的初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [GridItemOptions](./arkui-ts/ts-container-griditem.md#griditemoptions11对象说明) | 否   | 设置GridItem组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| GridItemAttribute | 返回GridItem组件的属性设置对象。<br/> GridItemAttribute表示GridItem的[属性](./arkui-ts/ts-container-griditem.md#属性)。 |

## GridItem<sup>23+</sup>

type GridItem = GridItemFrameNode

GridItem类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                               | 说明                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ |
| [GridItemFrameNode](#griditemframenode23) | 提供GridItem类型FrameNode节点。 |

### createNode('GridItem')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'GridItem'): GridItem

创建GridItem类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'GridItem' | 是 | 创建GridItem类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [GridItem](#griditem14) | GridItem类型的FrameNode节点。 |

**示例：** 

参考[createNode('Grid')](#createnodegrid14)示例。

### createGridItemNode<sup>23+</sup>

createGridItemNode(context: UIContext, options?: FrameNodeOptions): GridItem

创建GridItem类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 是 | 创建GridItem类型的FrameNode节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [GridItem](#griditem23) | GridItem类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createNode(uiContext);
```

### getAttribute('GridItem')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'GridItem'): GridItemAttribute | undefined

获取GridItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'GridItem' | 是 | 获取GridItem节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| GridItemAttribute&nbsp;\|&nbsp;undefined | GridItem节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 

完整示例请参考[createNode('Grid')](#createnodegrid14)的示例。

### getGridItemAttribute<sup>24+</sup>

getGridItemAttribute(node: FrameNode): GridItemAttribute | undefined

获取GridItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| GridItemAttribute&nbsp;\|&nbsp;undefined | GridItem节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 

<!--code_no_check-->

``` ts
typeNode.getGridItemAttribute(node);
```

## TextClock<sup>14+</sup>

type TextClock = TypedFrameNode&lt;TextClockInterface, TextClockAttribute&gt;

TextClock类型的FrameNode节点类型。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[TextClock](#textclock23)。

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;TextClockInterface, TextClockAttribute&gt; | 提供TextClock类型FrameNode节点。<br/> TextClockInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为TextClock组件的构造函数类型。 <br/> TextClockAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回TextClock组件的属性设置对象。<br/> TextClockInterface表示TextClock的[接口](./arkui-ts/ts-basic-components-textclock.md#接口)，TextClockAttribute表示TextClock的[属性](./arkui-ts/ts-basic-components-textclock.md#属性)。 |

## TextClock<sup>23+</sup>

type TextClock = TextClockFrameNode

TextClock类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[TextClock](#textclock14)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [TextClockFrameNode](#textclockframenode23) | TextClock类型FrameNode节点。 |

## TextClockFrameNode<sup>23+</sup>

TextClockFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[TextClock](./arkui-ts/ts-basic-components-textclock.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(options?: TextClockOptions): TextClockAttribute

初始化TextClock组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [TextClockOptions](./arkui-ts/ts-basic-components-textclock.md#textclockoptions18对象说明) | 否   | TextClock组件参数。默认值继承[TextClockOptions](./arkui-ts/ts-basic-components-textclock.md#textclockoptions18对象说明)。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextClockAttribute | 返回TextClock组件的属性设置对象。 |

### createNode('TextClock')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'TextClock'): TextClock

创建TextClock类型的FrameNode节点。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createTextClockNode](#createtextclocknode23)。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'TextClock' | 是 | 创建TextClock类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [TextClock](#textclock14) | TextClock类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
typeNode.createNode(uiContext, 'TextClock');
```

### createTextClockNode<sup>23+</sup>

createTextClockNode(context: UIContext): TextClock

创建TextClock类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createNode('TextClock')](#createnodetextclock14)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [TextClock](#textclock23) | TextClock类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
typeNode.createTextClockNode(uiContext);
```

## TextTimer<sup>14+</sup>

type TextTimer = TypedFrameNode&lt;TextTimerInterface, TextTimerAttribute&gt;

TextTimer类型的FrameNode节点类型。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[TextTimer](#texttimer23)。

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;TextTimerInterface, TextTimerAttribute&gt; | 提供TextTimer类型FrameNode节点。<br/> TextTimerInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为TextTimer组件的构造函数类型。 <br/> TextTimerAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回TextTimer组件的属性设置对象。<br/> TextTimerInterface表示TextTimer的[接口](./arkui-ts/ts-basic-components-texttimer.md#接口)，TextTimerAttribute表示TextTimer的[属性](./arkui-ts/ts-basic-components-texttimer.md#属性)。 |

## TextTimer<sup>23+</sup>

type TextTimer = TextTimerFrameNode

TextTimer类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[TextTimer](#texttimer14)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [TextTimerFrameNode](#texttimerframenode23) | TextTimer类型FrameNode节点。 |

## TextTimerFrameNode<sup>23+</sup>

TextTimerFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[TextTimer](./arkui-ts/ts-basic-components-texttimer.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(options?: TextTimerOptions): TextTimerAttribute

初始化TextTimer组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [TextTimerOptions](./arkui-ts/ts-basic-components-texttimer.md#texttimeroptions对象说明) | 否   | TextTimer组件参数。默认值继承[TextTimerOptions](./arkui-ts/ts-basic-components-texttimer.md#texttimeroptions对象说明)。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextTimerAttribute | 返回TextTimer组件的属性设置对象。 |

### createNode('TextTimer')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'TextTimer'): TextTimer

创建TextTimer类型的FrameNode节点。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createTextTimerNode](#createtexttimernode23)。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'TextTimer' | 是 | 创建TextTimer类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [TextTimer](#texttimer14) | TextTimer类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createNode(uiContext, 'TextTimer');
```

### createTextTimerNode<sup>23+</sup>

createTextTimerNode(context: UIContext): TextTimer

创建TextTimer类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createNode('TextTimer')](#createnodetexttimer14)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [TextTimer](#texttimer23) | TextTimer类型的FrameNode节点。 |

**示例：**

<!--code_no_check-->

```ts
typeNode.createTextTimerNode(uiContext);
```

## Marquee<sup>14+</sup>

type Marquee = TypedFrameNode&lt;MarqueeInterface, MarqueeAttribute&gt;

Marquee类型的FrameNode节点类型。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Marquee](#marquee23)。

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;MarqueeInterface, MarqueeAttribute&gt; | 提供Marquee类型FrameNode节点。<br/> MarqueeInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Marquee组件的构造函数类型。 <br/> MarqueeAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Marquee组件的属性设置对象。<br/> MarqueeInterface表示Marquee的[接口](./arkui-ts/ts-basic-components-marquee.md#接口)，MarqueeAttribute表示Marquee的[属性](./arkui-ts/ts-basic-components-marquee.md#属性)。 |

## Marquee<sup>23+</sup>

type Marquee = MarqueeFrameNode

Marquee类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Marquee](#marquee14)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [MarqueeFrameNode](#marqueeframenode23) | Marquee类型FrameNode节点。 |

## MarqueeFrameNode<sup>23+</sup>

MarqueeFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[Marquee](./arkui-ts/ts-basic-components-marquee.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value?: MarqueeOptions): MarqueeAttribute

初始化Marquee组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [MarqueeOptions](./arkui-ts/ts-basic-components-marquee.md#marqueeoptions18对象说明) | 否   | Marquee组件的初始化选项。默认值为空。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| MarqueeAttribute | 返回Marquee组件的属性设置对象。 |

### createNode('Marquee')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'Marquee'): Marquee

创建Marquee类型的FrameNode节点。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createMarqueeNode](#createmarqueenode23)。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Marquee' | 是 | 创建Marquee类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Marquee](#marquee14) | Marquee类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 })
    node.appendChild(col);
    // 创建marquee
    let marquee = typeNode.createNode(uiContext, 'Marquee');
    marquee.initialize({start:true,src:'Marquee, if need display, src shall be long'})
      .width(100);
    col.appendChild(marquee);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('Marquee createNode sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### createMarqueeNode<sup>23+</sup>

createMarqueeNode(context: UIContext, options?: FrameNodeOptions): Marquee

创建Marquee类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Marquee')](#createnodemarquee14)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否   | 创建节点的额外选项。默认值继承[FrameNodeOptions](#framenodeoptions24)。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Marquee](#marquee23) | Marquee类型的FrameNode节点。 |

## TextArea<sup>14+</sup>

type TextArea = TypedFrameNode&lt;TextAreaInterface, TextAreaAttribute&gt;

TextArea类型的FrameNode节点类型。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[TextArea](#textarea23)。

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;TextAreaInterface, TextAreaAttribute&gt; | 提供TextArea类型FrameNode节点。<br/> TextAreaInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为TextArea组件的构造函数类型。 <br/> TextAreaAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回TextArea组件的属性设置对象。<br/> TextAreaInterface表示TextArea的[接口](./arkui-ts/ts-basic-components-textarea.md#接口)，TextAreaAttribute表示TextArea的[属性](./arkui-ts/ts-basic-components-textarea.md#属性)。 |

## TextArea<sup>23+</sup>

type TextArea = TextAreaFrameNode

TextArea类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[TextArea](#textarea14)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [TextAreaFrameNode](#textareaframenode23) | TextArea类型FrameNode节点。 |

## TextAreaFrameNode<sup>23+</sup>

TextAreaFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[TextArea](./arkui-ts/ts-basic-components-textarea.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value?: TextAreaOptions): TextAreaAttribute

初始化TextArea组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [TextAreaOptions](./arkui-ts/ts-basic-components-textarea.md#textareaoptions对象说明) | 否   | TextArea组件的初始化选项。默认值为空。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextAreaAttribute | 返回TextArea组件的属性设置对象。 |

### createNode('TextArea')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'TextArea'): TextArea

创建TextArea类型的FrameNode节点。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createTextAreaNode](#createtextareanode23)。

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'TextArea' | 是 | 创建TextArea类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [TextArea](#textarea14) | TextArea类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 })
    node.appendChild(col);
    // 创建textArea
    let textArea = typeNode.createNode(uiContext, 'TextArea');
    textArea.initialize({ text: "TextArea" });
    col.appendChild(textArea);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextArea create sample')
      NodeContainer(this.myNodeController);
    }
  }
}
```

### createTextAreaNode<sup>23+</sup>

createTextAreaNode(context: UIContext, options?: FrameNodeOptions): TextArea

创建TextArea类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('TextArea')](#createnodetextarea14)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [FrameNodeOptions](#framenodeoptions24) | 否   | 创建节点的额外选项。默认值继承[FrameNodeOptions](#framenodeoptions24)。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [TextArea](#textarea14) | TextArea类型的FrameNode节点。 |

### getAttribute('TextArea')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'TextArea'): TextAreaAttribute | undefined

获取TextArea节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[getTextAreaAttribute](#gettextareaattribute24)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'TextArea' | 是 | 获取TextArea节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| TextAreaAttribute&nbsp;\|&nbsp;undefined | TextArea节点类型的属性，若获取失败，则返回undefined。 |

**示例：** 

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建TextArea
    let textArea = typeNode.createNode(uiContext, 'TextArea');
    textArea.initialize({ placeholder: 'TextArea placeholderColor' });
    col.appendChild(textArea);
    // 获取TextArea节点的属性
    typeNode.getAttribute(textArea, 'TextArea')?.placeholderColor(Color.Red);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextArea getAttribute sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### getTextAreaAttribute<sup>24+</sup>

export function getTextAreaAttribute(node: FrameNode): TextAreaAttribute | undefined

获取TextArea类型的FrameNode多行文本输入框的文本属性TextAreaAttribute。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[getAttribute('TextArea')](#getattributetextarea20)。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| --- | --- | --- | --- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是 | 获取属性时所需的目标节点。|

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextAreaAttribute \| undefined | 若node为合法的TextArea节点，则返回其属性对象，否则返回undefined。 |

**示例：**

```ts
import { Entry, Component, Column, NodeContainer, TextArea, FrameNode, Color, ColumnOptions, UIContext } from '@kit.ArkUI';
import { NodeController } from 'arkui.NodeController';
import { typeNode } from 'arkui.FrameNode';

class TextNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);

    let col = typeNode.createColumnNode(uiContext);
    col.initialize({ space: 5 } as ColumnOptions);
    node.appendChild(col);

    let text = typeNode.createTextAreaNode(uiContext);
    text.initialize({ text: "Hello" });
    typeNode.getTextAreaAttribute(text)?.fontColor(Color.Red);
    col.appendChild(text);

    let text2 = typeNode.createTextAreaNode(uiContext);
    text2.initialize({ text: "world!" });
    col.appendChild(text2);

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private textNodeController: TextNodeController = new TextNodeController();

  build() {
    Column(undefined) {
      NodeContainer(this.textNodeController);
    }
    .height("100%")
    .width("100%")
  }
}
```

![image](figures/getTextAreaAttribute_static.jpg)

### bindController('TextArea')<sup>20+</sup>

bindController(node: FrameNode, controller: TextAreaController, nodeType: 'TextArea'): void

将输入框控制器[TextAreaController](arkui-ts/ts-basic-components-textarea.md#textareacontroller8)绑定到[TextArea](#textarea14)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口从API版本26.0.0开始支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[bindTextAreaController](#bindtextareacontroller24)。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 绑定输入框控制器的目标节点。 |
| controller | [TextAreaController](arkui-ts/ts-basic-components-textarea.md#textareacontroller8) | 是   | 输入框控制器。 |
| nodeType | 'TextArea' | 是 | 绑定输入框控制器的目标节点的节点类型为TextArea。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. |

**示例：** 

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建、初始化TextArea，默认获焦
    let textArea = typeNode.createNode(uiContext, 'TextArea');
    textArea.initialize({ text: "TextArea" })
      .defaultFocus(true)
    col.appendChild(textArea);
    // 绑定TextAreaController，设置光标位置
    let controller: TextAreaController = new TextAreaController()
    typeNode.bindController(textArea, controller, 'TextArea');
    controller.caretPosition(3);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('TextArea bindController sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### bindTextAreaController<sup>24+</sup>

export function bindTextAreaController(node: FrameNode, controller: TextAreaController): void

将TextAreaController绑定到指定的多行文本输入框节点上。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[bindController('TextArea')](#bindcontrollertextarea20)。

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| --- | --- | --- | --- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是 | 绑定输入框控制器的目标节点。|
| controller | [TextAreaController](./arkui-ts/ts-basic-components-textarea.md#textareacontroller8) | 是 | 输入框控制器。 |

**错误码：**

以下错误码的详细介绍请参见[自定义节点错误码](./errorcode-node.md)。

| 错误码ID | 错误信息                         |
| -------- | -------------------------------- |
| 100023   | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |
| 100021   | The FrameNode is not modifiable. |

**示例：**

```ts
import { Entry, Component, Column, Button, NodeContainer, TextArea, TextAreaController, FrameNode, Color, ColumnOptions, UIContext } from '@kit.ArkUI';
import { NodeController } from 'arkui.NodeController';
import { typeNode } from 'arkui.FrameNode';

class TextNodeController extends NodeController {
  controller: TextAreaController = new TextAreaController();

  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);

    let col = typeNode.createColumnNode(uiContext);
    col.initialize({ space: 5 } as ColumnOptions);
    node.appendChild(col);

    let text = typeNode.createTextAreaNode(uiContext);
    text.initialize({ text: "Hello world!" });
    typeNode.bindTextAreaController(text, this.controller);
    col.appendChild(text);

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private textNodeController: TextNodeController = new TextNodeController();

  build() {
    Column(undefined) {
      NodeContainer(this.textNodeController);
    }
    .height("100%")
    .width("100%")
  }
}
```

![image](figures/bindTextAreaController_static.jpg)

## SymbolGlyph<sup>14+</sup>

type SymbolGlyph = TypedFrameNode&lt;SymbolGlyphInterface, SymbolGlyphAttribute&gt;

SymbolGlyph类型的FrameNode节点类型。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[SymbolGlyph](#symbolglyph23)。

**ArkTS-Dyn起始版本：** 14

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;SymbolGlyphInterface, SymbolGlyphAttribute&gt; | 提供SymbolGlyph类型FrameNode节点。<br/> SymbolGlyphInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为SymbolGlyph组件的构造函数类型。 <br/> SymbolGlyphAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回SymbolGlyph组件的属性设置对象。<br/> SymbolGlyphInterface表示SymbolGlyph的[接口](./arkui-ts/ts-basic-components-symbolGlyph.md#接口)，SymbolGlyphAttribute表示SymbolGlyph的[属性](./arkui-ts/ts-basic-components-symbolGlyph.md#属性)。 |

## SymbolGlyph<sup>23+</sup>

type SymbolGlyph = SymbolGlyphFrameNode

SymbolGlyph类型的FrameNode节点类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[SymbolGlyph](#symbolglyph14)。

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| ---- | ---- |
| [SymbolGlyphFrameNode](#symbolglyphframenode23) | SymbolGlyph类型FrameNode节点。 |

## SymbolGlyphFrameNode<sup>23+</sup>

SymbolGlyphFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明[SymbolGlyph](./arkui-ts/ts-basic-components-symbolGlyph.md)类型的FrameNode。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

### initialize<sup>23+</sup>

abstract initialize(value?: Resource): SymbolGlyphAttribute

初始化SymbolGlyph组件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [Resource](./arkui-ts/ts-types.md#resource) | 否   | SymbolGlyph资源。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| SymbolGlyphAttribute | 返回SymbolGlyph组件的属性设置对象。 |

### createNode('SymbolGlyph')<sup>14+</sup>

createNode(context: UIContext, nodeType: 'SymbolGlyph'): SymbolGlyph

创建SymbolGlyph类型的FrameNode节点。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createNode('SymbolGlyph')](#createnodesymbolglyph14)。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'SymbolGlyph' | 是 | 创建SymbolGlyph类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [SymbolGlyph](#symbolglyph14) | SymbolGlyph类型的FrameNode节点。 |

**示例：**

```ts
import { FrameNode, NodeController, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute;
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    node.appendChild(col);
    // 创建SymbolGlyph
    let symbolGlyph = typeNode.createNode(uiContext, 'SymbolGlyph');
    symbolGlyph.initialize($r('sys.symbol.ohos_trash'));
    col.appendChild(symbolGlyph);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 5 }) {
      Text('SymbolGlyph sample');
      NodeContainer(this.myNodeController);
    }
  }
}
```

### createSymbolGlyphNode<sup>23+</sup>

export function createSymbolGlyphNode(context: UIContext): SymbolGlyph

创建SymbolGlyph类型的FrameNode节点。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('SymbolGlyph')](#createnodesymbolglyph14)。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [SymbolGlyph](#symbolglyph23) | SymbolGlyph类型的FrameNode节点。 |

## Checkbox<sup>18+</sup>

type Checkbox = TypedFrameNode&lt;CheckboxInterface, CheckboxAttribute&gt;

Checkbox类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Checkbox<sup>23+</sup>](#checkbox23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;CheckboxInterface, CheckboxAttribute&gt; | 提供Checkbox类型FrameNode节点。<br/> CheckboxInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Checkbox组件的构造函数类型。 <br/> CheckboxAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Checkbox组件的属性设置对象。<br/> CheckboxInterface表示Checkbox的[接口](./arkui-ts/ts-basic-components-checkbox.md#接口)，CheckboxAttribute表示Checkbox的[属性](./arkui-ts/ts-basic-components-checkbox.md#属性)。 |

### createNode('Checkbox')<sup>18+</sup>

createNode(context: UIContext, nodeType: 'Checkbox'): Checkbox

创建Checkbox类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createCheckboxNode](#createcheckboxnode23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Checkbox' | 是 | 创建Checkbox类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Checkbox](#checkbox18) | Checkbox类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Checkbox控制器
class MyCheckboxController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Checkbox
    let checkbox = typeNode.createNode(uiContext, 'Checkbox')
    checkbox.initialize({ name: 'checkbox1', group: 'checkboxGroup1' })

    // 创建另一个Checkbox
    let checkbox1 = typeNode.createNode(uiContext, 'Checkbox')
    checkbox1.initialize({ name: 'checkbox2', group: 'checkboxGroup1' })

    // 将两个checkbox添加至col进行比较
    col.appendChild(checkbox)
    col.appendChild(checkbox1)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myCheckboxController: MyCheckboxController = new MyCheckboxController();

  build() {
    Column({ space: 5 }) {
      Text('CheckboxSample')
      NodeContainer(this.myCheckboxController);
    }.width('100%')
  }
}
```

### getAttribute('Checkbox')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Checkbox'): CheckboxAttribute | undefined

获取Checkbox节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Checkbox' | 是 | 获取Checkbox节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| CheckboxAttribute&nbsp;\|&nbsp;undefined | Checkbox节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Checkbox控制器
class MyCheckboxController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Checkbox
    let checkbox = typeNode.createNode(uiContext, 'Checkbox')
    checkbox.initialize({ name: 'checkbox1', group: 'checkboxGroup1' })

    // 创建另一个Checkbox
    let checkbox1 = typeNode.createNode(uiContext, 'Checkbox')
    checkbox1.initialize({ name: 'checkbox2', group: 'checkboxGroup1' })
    // 给首个Checkbox设置形状属性
    typeNode.getAttribute(checkbox1,'Checkbox')?.shape(CheckBoxShape.ROUNDED_SQUARE)
    // 将两个checkbox添加至col进行比较
    col.appendChild(checkbox)
    col.appendChild(checkbox1)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myCheckboxController: MyCheckboxController = new MyCheckboxController();

  build() {
    Column({ space: 5 }) {
      Text('CheckboxSample')
      NodeContainer(this.myCheckboxController);
    }.width('100%')
  }
}
```

## CheckboxFrameNode<sup>23+</sup>

CheckboxFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Checkbox类型的FrameNode。

### initialize<sup>23+</sup>
abstract initialize(options?: CheckboxOptions): CheckboxAttribute

设置或更新CheckboxOptions初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [CheckboxOptions](./arkui-ts/ts-basic-components-checkbox.md#checkboxoptions对象说明) | 否   | 组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| CheckboxAttribute | 返回Checkbox组件的属性设置对象。 |

## Checkbox<sup>23+</sup>
type Checkbox = CheckboxFrameNode

Checkbox类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Checkbox<sup>18+</sup>](#checkbox18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| [CheckboxFrameNode](#checkboxframenode23) | 提供Checkbox类型FrameNode节点。|

### createCheckboxNode<sup>23+</sup>
createCheckboxNode(context: UIContext, options?: FrameNodeOptions): Checkbox

创建Checkbox类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Checkbox')<sup>18+</sup>](#createnodecheckbox18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Checkbox](#checkbox23) | Checkbox类型的FrameNode节点。 |

## CheckboxGroup<sup>18+</sup>

type CheckboxGroup = TypedFrameNode&lt;CheckboxGroupInterface, CheckboxGroupAttribute&gt;

CheckboxGroup类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[CheckboxGroup<sup>23+</sup>](#checkboxgroup23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;CheckboxGroupInterface, CheckboxGroupAttribute&gt; | 提供CheckboxGroup类型FrameNode节点。<br/> CheckboxGroupInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为CheckboxGroup组件的构造函数类型。 <br/> CheckboxGroupAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回CheckboxGroup组件的属性设置对象。<br/> CheckboxGroupInterface表示CheckboxGroup的[接口](./arkui-ts/ts-basic-components-checkboxgroup.md#接口)，CheckboxGroupAttribute表示CheckboxGroup的[属性](./arkui-ts/ts-basic-components-checkboxgroup.md#属性)。 |

### createNode('CheckboxGroup')<sup>18+</sup>

createNode(context: UIContext, nodeType: 'CheckboxGroup'): CheckboxGroup

创建CheckboxGroup类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createCheckboxGroupNode](#createcheckboxgroupnode23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'CheckboxGroup' | 是 | 创建CheckboxGroup类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [CheckboxGroup](#checkboxgroup18) | CheckboxGroup类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义CheckboxGroup控制器
class MyCheckboxGroupController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    let checkbox = typeNode.createNode(uiContext, 'Checkbox')
    checkbox.initialize({ name: 'checkbox1', group: 'checkboxGroup1' })

    let checkbox1 = typeNode.createNode(uiContext, 'Checkbox')
    checkbox1.initialize({ name: 'checkbox2', group: 'checkboxGroup1' })

    // 创建checkboxGroup
    let checkboxGroup = typeNode.createNode(uiContext, 'CheckboxGroup')
    checkboxGroup.initialize({ group: 'checkboxGroup1' })

    col.appendChild(checkbox)
    col.appendChild(checkbox1)
    col.appendChild(checkboxGroup)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myCheckboxGroupController: MyCheckboxGroupController = new MyCheckboxGroupController();

  build() {
    Column({ space: 5 }) {
      Text('CheckboxGroupSample')
      NodeContainer(this.myCheckboxGroupController);
    }.width('100%')
  }
}
```

## CheckboxGroupFrameNode<sup>23+</sup>

CheckboxGroupFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明CheckboxGroup类型的FrameNode。

### initialize<sup>23+</sup>
abstract initialize(options?: CheckboxGroupOptions): CheckboxGroupAttribute

设置或更新CheckboxGroupOptions初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [CheckboxGroupOptions](./arkui-ts/ts-basic-components-checkboxgroup.md#checkboxgroupoptions对象说明) | 否   | 组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| CheckboxGroupAttribute | 返回CheckboxGroup组件的属性设置对象。 |

## CheckboxGroup<sup>23+</sup>
type CheckboxGroup = CheckboxGroupFrameNode

CheckboxGroup类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[CheckboxGroup<sup>18+</sup>](#checkboxgroup18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| [CheckboxGroupFrameNode](#checkboxgroupframenode23) | 提供CheckboxGroup类型FrameNode节点。|

### createCheckboxGroupNode<sup>23+</sup>
createCheckboxGroupNode(context: UIContext, options?: FrameNodeOptions): CheckboxGroup

创建CheckboxGroup类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('CheckboxGroup')<sup>18+</sup>](#createnodecheckboxgroup18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [CheckboxGroup](#checkboxgroup23) | CheckboxGroup类型的FrameNode节点。 |

## Rating<sup>18+</sup>

type Rating = TypedFrameNode&lt;RatingInterface, RatingAttribute&gt;

Rating类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Rating<sup>23+</sup>](#rating23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;RatingInterface, RatingAttribute&gt; | 提供Rating类型FrameNode节点。<br/> RatingInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Rating组件的构造函数类型。 <br/> RatingAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Rating组件的属性设置对象。<br/> RatingInterface表示Rating的[接口](./arkui-ts/ts-basic-components-rating.md#接口)，RatingAttribute表示Rating的[属性](./arkui-ts/ts-basic-components-rating.md#属性)。 |

### createNode('Rating')<sup>18+</sup>

createNode(context: UIContext, nodeType: 'Rating'): Rating

创建Rating类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn

**相关接口：** 该接口对应的ArkTS-Sta接口是[createRatingNode](#createratingnode23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Rating' | 是 | 创建Rating类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Rating](#rating18) | Rating类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Rating控制器
class MyRatingController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建rating
    let rating = typeNode.createNode(uiContext, 'Rating')
    rating.initialize({ rating: 0 })
    col.appendChild(rating)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myRatingController: MyRatingController = new MyRatingController();

  build() {
    Column({ space: 5 }) {
      Text('RatingSample')

      NodeContainer(this.myRatingController);

    }.width('100%')
  }
}
```

## RatingFrameNode<sup>23+</sup>

RatingFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Rating类型的FrameNode。

### initialize<sup>23+</sup>
abstract initialize(options?: RatingOptions): RatingAttribute

设置或更新RatingOptions初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [RatingOptions](./arkui-ts/ts-basic-components-rating.md#ratingoptions18对象说明) | 否   | 组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RatingAttribute | 返回Rating组件的属性设置对象。 |

## Rating<sup>23+</sup>
type Rating = RatingFrameNode

Rating类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Rating<sup>18+</sup>](#rating18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| [RatingFrameNode](#ratingframenode23) | 提供Rating类型FrameNode节点。|

### createRatingNode<sup>23+</sup>
createRatingNode(context: UIContext): Rating

创建Rating类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Rating')<sup>18+</sup>](#createnoderating18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Rating](#rating23) | Rating类型的FrameNode节点。 |

## Radio<sup>18+</sup>

type Radio = TypedFrameNode&lt;RadioInterface, RadioAttribute&gt;

Radio类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Radio<sup>23+</sup>](#radio23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;RadioInterface, RadioAttribute&gt; | 提供Radio类型FrameNode节点。<br/> RadioInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Radio组件的构造函数类型。 <br/> RadioAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Radio组件的属性设置对象。<br/> RadioInterface表示Radio的[接口](./arkui-ts/ts-basic-components-radio.md#接口)，RadioAttribute表示Radio的[属性](./arkui-ts/ts-basic-components-radio.md#属性)。 |

### createNode('Radio')<sup>18+</sup>

createNode(context: UIContext, nodeType: 'Radio'): Radio

创建Radio类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createRadioNode](#createradionode23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Radio' | 是 | 创建Radio类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Radio](#radio18) | Radio类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Radio控制器
class MyRadioController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Radio
    let radio1 = typeNode.createNode(uiContext, 'Radio')
    radio1.initialize({ value: 'radio1', group: 'radioGroup' })

    // 创建另一个Radio用于对比
    let radio2 = typeNode.createNode(uiContext, 'Radio')
    radio2.initialize({ value: 'radio2', group: 'radioGroup' })

    col.appendChild(radio1)
    col.appendChild(radio2)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myRadioController: MyRadioController = new MyRadioController();

  build() {
    Column({ space: 5 }) {
      Text('RadioSample')
      NodeContainer(this.myRadioController);
    }.width('100%')
  }
}
```

### getAttribute('Radio')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Radio'): RadioAttribute | undefined

获取Radio节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Radio' | 是 | 获取Radio节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RadioAttribute&nbsp;\|&nbsp;undefined | Radio节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Radio控制器
class MyRadioController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建radio
    let radio1 = typeNode.createNode(uiContext, 'Radio')
    radio1.initialize({ value: 'radio1', group: 'radioGroup' })
    typeNode.getAttribute(radio1,'Radio')?.checked(true)
    // 创建另一个radio用于对比
    let radio2 = typeNode.createNode(uiContext, 'Radio')
    radio2.initialize({ value: 'radio2', group: 'radioGroup' })


    col.appendChild(radio1)
    col.appendChild(radio2)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myRadioController: MyRadioController = new MyRadioController();

  build() {
    Column({ space: 5 }) {
      Text('RadioSample')
      NodeContainer(this.myRadioController);
    }.width('100%')
  }
}
```

## RadioFrameNode<sup>23+</sup>

RadioFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Radio类型的FrameNode。

### initialize<sup>23+</sup>
abstract initialize(value: RadioOptions): RadioAttribute

设置或更新RadioOptions初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [RadioOptions](./arkui-ts/ts-basic-components-radio.md#radiooptions对象说明) | 是   | 组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| RadioAttribute | 返回Radio组件的属性设置对象。 |

## Radio<sup>23+</sup>
type Radio = RadioFrameNode

Radio类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Radio<sup>18+</sup>](#radio18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| [RadioFrameNode](#radioframenode23) | 提供Radio类型FrameNode节点。|

### createRadioNode<sup>23+</sup>
createRadioNode(context: UIContext, options?: FrameNodeOptions): Radio

创建Radio类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Radio')<sup>18+</sup>](#createnoderadio18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Radio](#radio23) | Radio类型的FrameNode节点。 |

## Slider<sup>18+</sup>

type Slider = TypedFrameNode&lt;SliderInterface, SliderAttribute&gt;

Slider类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Slider<sup>23+</sup>](#slider23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTs-Dyn起始版本：** 18

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;SliderInterface, SliderAttribute&gt; | 提供Slider类型FrameNode节点。<br/> SliderInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Slider组件的构造函数类型。 <br/> SliderAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Slider组件的属性设置对象。<br/> SliderInterface表示Slider的[接口](./arkui-ts/ts-basic-components-slider.md#接口)，SliderAttribute表示Slider的[属性](./arkui-ts/ts-basic-components-slider.md#属性)。 |

### createNode('Slider')<sup>18+</sup>

createNode(context: UIContext, nodeType: 'Slider'): Slider

创建Slider类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createSliderNode](#createslidernode23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Slider' | 是 | 创建Slider类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Slider](#slider18) | Slider类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Slider控制器
class MySliderController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Slider
    let slider = typeNode.createNode(uiContext, 'Slider')
    slider.initialize({value:50})
    col.appendChild(slider)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private mySliderController: MySliderController = new MySliderController();

  build() {
    Column({ space: 5 }) {
      Text('SliderSample')
      NodeContainer(this.mySliderController);

    }.width('100%')
  }
}
```

### getAttribute('Slider')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Slider'): SliderAttribute | undefined

获取Slider节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Slider' | 是 | 获取Slider节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| SliderAttribute&nbsp;\|&nbsp;undefined | Slider节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Slider控制器
class MySliderController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Slider
    let slider = typeNode.createNode(uiContext, 'Slider')
    slider.initialize({value:50})
    typeNode.getAttribute(slider,'Slider')?.selectedColor(Color.Pink)
    col.appendChild(slider)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private mySliderController: MySliderController = new MySliderController();

  build() {
    Column({ space: 5 }) {
      Text('SliderSample')
      NodeContainer(this.mySliderController);

    }.width('100%')
  }
}
```

## SliderFrameNode<sup>23+</sup>

SliderFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Slider类型的FrameNode。

### initialize<sup>23+</sup>
abstract initialize(options?: SliderOptions): SliderAttribute;

设置或更新SliderOptions初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| options | [SliderOptions](./arkui-ts/ts-basic-components-slider.md#slideroptions对象说明) | 否   | 组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| SliderAttribute | 返回Slider组件的属性设置对象。 |

## Slider<sup>23+</sup>

type Slider = SliderFrameNode

Slider类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Slider<sup>18+</sup>](#slider18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| [SliderFrameNode](#sliderframenode23) | 提供Slider类型FrameNode节点。|

### createSliderNode<sup>23+</sup>
createSliderNode(context: UIContext, options?: FrameNodeOptions): Slider

创建Slider类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Slider')<sup>18+</sup>](#createnodeslider18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Slider](#slider23) | Slider类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createSliderNode(uiContext);
```

## Select<sup>18+</sup>

type Select = TypedFrameNode&lt;SelectInterface, SelectAttribute&gt;

Select类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Select<sup>23+</sup>](#select23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;SelectInterface, SelectAttribute&gt; | 提供Select类型FrameNode节点。<br/> SelectInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Select组件的构造函数类型。 <br/> SelectAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Select组件的属性设置对象。<br/> SelectInterface表示Select的[接口](./arkui-ts/ts-basic-components-select.md#接口)，SelectAttribute表示Select的[属性](./arkui-ts/ts-basic-components-select.md#属性)。 |

### createNode('Select')<sup>18+</sup>

createNode(context: UIContext, nodeType: 'Select'): Select

创建Select类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createSelectNode](#createselectnode23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Select' | 是 | 创建Select类型的节点。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Select](#select18) | Select类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Select控制器
class MySelectController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Select并设置选项
    let select = typeNode.createNode(uiContext, 'Select')
    select.initialize([{ value: "option one" }, { value: "option two" }, { value: "option three" }])
    col.appendChild(select)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private mySelectController: MySelectController = new MySelectController();

  build() {
    Column({ space: 5 }) {
      Text('SelectSample')
      NodeContainer(this.mySelectController);
    }.width('100%')
  }
}
```

## SelectFrameNode<sup>23+</sup>

SelectFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Select类型的FrameNode。

### initialize<sup>23+</sup>

abstract initialize(value: Array&lt;SelectOption&gt;): SelectAttribute

设置或更新Array&lt;SelectOption&gt;初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | Array<[SelectOption](./arkui-ts/ts-basic-components-select.md#selectoption对象说明)> | 是   | 组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| SelectAttribute | 返回Select组件的属性设置对象。 |

## Select<sup>23+</sup>

type Select = SelectFrameNode

Select类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Select<sup>18+</sup>](#select18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| [SelectFrameNode](#selectframenode23) | 提供Select类型FrameNode节点。|

### createSelectNode<sup>23+</sup>

createSelectNode(context: UIContext): Select

创建Select类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Select')<sup>18+</sup>](#createnodeselect18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Select](#select23) | Select类型的FrameNode节点。 |

**示例：** 

<!--code_no_check-->

```ts
typeNode.createSelectNode(uiContext);
```

## Toggle<sup>18+</sup>

type Toggle = TypedFrameNode&lt;ToggleInterface, ToggleAttribute&gt;

[Toggle](arkui-ts/ts-basic-components-toggle.md)类型的FrameNode节点类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[Toggle<sup>23+</sup>](#toggle23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| TypedFrameNode&lt;ToggleInterface, ToggleAttribute&gt; | 提供Toggle类型FrameNode节点。<br/> ToggleInterface用于[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)的[initialize](./js-apis-arkui-frameNode.md#属性)接口的入参，入参为Toggle组件的构造函数类型。 <br/> ToggleAttribute用于TypedFrameNode的[attribute](./js-apis-arkui-frameNode.md#属性)接口的返回值，返回Toggle组件的属性设置对象。<br/> ToggleInterface表示Toggle的[接口](./arkui-ts/ts-basic-components-toggle.md#接口)，ToggleAttribute表示Toggle的[属性](./arkui-ts/ts-basic-components-toggle.md#属性)。 |

### createNode('Toggle')<sup>18+</sup>

createNode(context: UIContext, nodeType: 'Toggle', options?: ToggleOptions): Toggle

创建Toggle类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[createToggleNode](#createtogglenode23)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| nodeType | 'Toggle' | 是 | 创建Toggle类型的节点。 |
| options | [ToggleOptions](./arkui-ts/ts-basic-components-toggle.md#toggleoptions18对象说明) | 否 | 创建Toggle节点的接口参数，仅可通过ToggleOptions中的type属性设置开关样式。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Toggle](#toggle18) | Toggle类型的FrameNode节点。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Toggle控制器
class MyToggleController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Toggle
    let toggleSwitch = typeNode.createNode(uiContext, 'Toggle')
    toggleSwitch.initialize({ type: ToggleType.Switch })
    col.appendChild(toggleSwitch)

    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myToggleController: MyToggleController = new MyToggleController();

  build() {
    Column({ space: 5 }) {
      Text('ToggleSample')
      NodeContainer(this.myToggleController);

    }.width('100%')
  }
}
```

### getAttribute('Toggle')<sup>20+</sup>

getAttribute(node: FrameNode, nodeType: 'Toggle'): ToggleAttribute | undefined

获取Toggle节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | 是   | 获取属性时所需的目标节点。 |
| nodeType | 'Toggle' | 是 | 获取Toggle节点类型的属性。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ToggleAttribute&nbsp;\|&nbsp;undefined | Toggle节点类型的属性，若获取失败，则返回undefined。 |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义Toggle控制器
class MyToggleController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext)
    node.commonAttribute
    let col = typeNode.createNode(uiContext, 'Column')
    col.initialize({ space: 5 })
      .width('100%')
      .height('100%')
    node.appendChild(col)
    // 创建Toggle
    let toggleSwitch = typeNode.createNode(uiContext, 'Toggle')
    toggleSwitch.initialize({ type: ToggleType.Switch })
    typeNode.getAttribute(toggleSwitch,'Toggle')?.selectedColor(Color.Orange)
    col.appendChild(toggleSwitch)
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myToggleController: MyToggleController = new MyToggleController();

  build() {
    Column({ space: 5 }) {
      Text('ToggleSample')
      NodeContainer(this.myToggleController);

    }.width('100%')
  }
}
```

## ToggleFrameNode<sup>23+</sup>

ToggleFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode23)，用于声明Toggle类型的FrameNode。

### initialize<sup>23+</sup>

abstract initialize(value: ToggleOptions): ToggleAttribute;

设置或更新ToggleOptions初始值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| value | [ToggleOptions](./arkui-ts/ts-basic-components-toggle.md#toggleoptions18对象说明) | 是   | 组件参数。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| ToggleAttribute | 返回Toggle组件的属性设置对象。 |

## Toggle<sup>23+</sup>

type Toggle = ToggleFrameNode

Toggle类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[Toggle<sup>18+</sup>](#toggle18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 类型                            | 说明                   |
| ----------------------------- | -------------------- |
| [ToggleFrameNode](#toggleframenode23) | 提供Toggle类型FrameNode节点。|

### createToggleNode<sup>23+</sup>
createToggleNode(context: UIContext, options?: ToggleOptions, frameNodeOptions?: FrameNodeOptions): Toggle

创建Toggle类型的FrameNode节点。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[createNode('Toggle')<sup>18+</sup>](#createnodetoggle18)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明  |
| ------------------ | ------------------ | ------------------- | ------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | 是   | 创建对应节点时所需的UI上下文。 |
| options | [ToggleOptions](./arkui-ts/ts-basic-components-toggle.md#toggleoptions18对象说明) | 否 | 创建Toggle节点的接口参数，仅可通过ToggleOptions中的type属性设置开关样式。 |
| frameNodeOptions<sup>24+</sup> | [FrameNodeOptions](#framenodeoptions24) | 否   | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。 |

**返回值：**

| 类型                  | 说明      |
| ------------------ | ------------------ |
| [Toggle](#toggle23) | Toggle类型的FrameNode节点。 |

## BlankFrameNode<sup>23+</sup>

BlankFrameNode继承自[TypedFrameNode](./js-apis-arkui-frameNode.md#typedframenode12)，用于声明[Blank](./arkui-ts/ts-basic-components-blank.md)类型的FrameNode

## 自定义具体类型节点示例

以Text节点为例，创建Text类型节点。

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let node = new FrameNode(uiContext);
    node.commonAttribute.width(100)
      .height(50)
      .borderColor(Color.Gray)
      .borderWidth(1)
      .margin({ left: 10 });
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 })
      .width('100%').height('100%').margin({ top: 5 });
    node.appendChild(col);
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize("Hello").fontColor(Color.Blue).fontSize(14);
    col.appendChild(text);
    return node;
  }
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController);
    }
  }
}
```

![FrameNodeTextTest](figures/FrameNodeTextTest.png)

## 滚动事件示例

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.rootNode.commonAttribute.width(100)
    return this.rootNode;
  }

  addCommonEvent(frameNode: FrameNode) {
    let gridEvent: UIGridEvent | undefined = typeNode.getEvent(frameNode, "Grid");
    gridEvent?.setOnWillScroll((scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => {
      console.info(`onWillScroll scrollOffset = ${scrollOffset}, scrollState = ${scrollState}, scrollSource = ${scrollSource}`)
    })
    gridEvent?.setOnDidScroll((scrollOffset: number, scrollState: ScrollState) => {
      console.info(`onDidScroll scrollOffset = ${scrollOffset}, scrollState = ${scrollState}`)
    })
    gridEvent?.setOnReachStart(() => {
      console.info(`onReachStart`)
    })
    gridEvent?.setOnReachEnd(() => {
      console.info(`onReachEnd`)
    })
    gridEvent?.setOnScrollStart(() => {
      console.info(`onScrollStart`)
    })
    gridEvent?.setOnScrollStop(() => {
      console.info(`onScrollStop`)
    })
    gridEvent?.setOnScrollFrameBegin((offset: number, state: ScrollState) => {
      console.info(`onScrollFrameBegin offset = ${offset}, state = ${state}`)
      return undefined;
    })
    gridEvent?.setOnScrollIndex((first: number, last: number) => {
      console.info(`onScrollIndex start = ${first}, end = ${last}`)
    })
  }
}

@Entry
@Component
struct Index {
  @State index: number = 0;
  private myNodeController: MyNodeController = new MyNodeController();
  @State numbers: string[] = []

  aboutToAppear() {
    for (let i = 0; i < 5; i++) {
      for (let j = 0; j < 5; j++) {
        this.numbers.push(j.toString());
      }
    }
  }

  build() {
    Column() {
      Button("add CommonEvent to Grid")
        .onClick(() => {
          this.myNodeController!.addCommonEvent(this.myNodeController!.rootNode!.getParent()!.getPreviousSibling()!)
        })
      Grid() {
        ForEach(this.numbers, (day: string, index: number) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (day: string, index: number) => index.toString() + day)
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .enableScrollInteraction(true)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)

      NodeContainer(this.myNodeController)
    }.width("100%")
  }
}
```
