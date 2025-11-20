# ComponentContent.static

提供ComponentContentBase以及ComponentContent类型。

> **说明：**
>
> 从API version 20开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 本模块仅适用于ArkTS1.2。

## 导入模块

```ts
import { ComponentContent, ComponentContentBase } from '@ohos.arkui.node';
```

## ComponentContentBase

ComponentContentBase表示[ComponentContent](#componentcontent)的基础类型。

## ComponentContent

ComponentContent表示组件内容的实体封装，支持在非UI组件中创建与传递。底层使用BuilderNode，具体使用规格参见[BuilderNode](./js-apis-arkui-builderNode-static.md)。ComponentContent继承自[ComponentContentBase](#componentcontentbase)。

### constructor

constructor(uiContext: UIContext, builder: WrappedBuilder\<CustomBuilder>)

ComponentContent的构造函数。用于按照[CustomBuilder](./arkui-ts/ts-types.md#custombuilder20)创建组件树。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名    | 类型                                      | 必填 | 说明                               |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| uiContext | [UIContext](./js-apis-arkui-UIContext.md) | 是 | 创建节点所需UI上下文。 |
| builder  | WrappedBuilder\<[CustomBuilder](./arkui-ts/ts-types.md#custombuilder20)> | 是   |   封装不带参builder函数的[WrappedBuilder对象](../../ui/state-management/arkts-static-wrapBuilder.md)。 |

**示例**

``` ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  FontWeight,
  ContentSlot,
  Button,
  ClickEvent
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeContent, FrameNode, ComponentContent } from '@ohos.arkui.node';

@Builder
function buildText() {
  Column() {
    Text("HELLO")
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}

@Entry
@Component
struct Index {
  private content: NodeContent = new NodeContent();

  build() {
    Row() {
      Column() {
        Button('addComponentContent')
          .onClick((event: ClickEvent) => {
            let frameNode: FrameNode = new FrameNode(this.getUIContext());
            frameNode.addComponentContent(new ComponentContent(this.getUIContext(), wrapBuilder(buildText)));
            this.content.addFrameNode(frameNode);
          })
        ContentSlot(this.content)
      }
      .id("column")
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### constructor

constructor(uiContext: UIContext, builder: WrappedBuilder\<CustomBuilderT\<T>>, args: T)

ComponentContent的构造函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名    | 类型                                      | 必填 | 说明                               |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| uiContext | [UIContext](./js-apis-arkui-UIContext.md) | 是   | 用于创建对应节点的UI上下文。|
| builder  | WrappedBuilder\<[CustomBuilderT\<T>](./arkui-ts/ts-types.md#custombuildertt20)> | 是   |   封装带参builder函数的WrappedBuilder对象。 |
| args     |     T     |   是   |   WrappedBuilder对象封装的builder函数的参数。 |

### constructor

constructor(uiContext: UIContext, builder: WrappedBuilder\<CustomBuilderT\<T>>, args: T, options: BuildOptions)

ComponentContent的构造函数。用于按照带参数的[CustomBuilderT\<T>](./arkui-ts/ts-types.md#custombuildertt20)创建组件树。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名    | 类型                                      | 必填 | 说明                               |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| uiContext | [UIContext](./js-apis-arkui-UIContext.md) | 是   | 用于创建对应节点的UI上下文。 |
| builder  | WrappedBuilder\<[CustomBuilderT\<T>](./arkui-ts/ts-types.md#custombuildertt20)>  | 是   |   封装带参builder函数的WrappedBuilder对象。 |
| args     |     T     |   是   |   WrappedBuilder对象封装的builder函数的参数。 |
| options | [BuildOptions](./js-apis-arkui-builderNode.md#buildoptions12)                                                    | 是   |  build的配置参数。该值无效，默认支持@Builder参数不一致，且行为与@Builder的行为保持一致。                                  |

### update

update(args: T): void

用于更新WrappedBuilder对象封装的builder函数参数。这些参数与构造函数传入的参数类型一致。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名 | 类型 | 必填 | 说明                                                         |
| ------ | ---- | ---- | ------------------------------------------------------------ |
| args   | T    | 是   | 用于更新WrappedBuilder对象封装的builder函数参数，与constructor传入的参数类型保持一致。 |

### dispose

dispose(): void

立即释放当前ComponentContent对象对[基本概念：实体节点](../../ui/arkts-user-defined-node.md#基本概念)的引用。关于ComponentContent的解绑场景请参见[解除实体节点引用关系](../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

> **说明：**
>
> 当ComponentContent对象调用dispose之后，会与后端实体节点解除引用关系。若前端对象ComponentContent无法释放，容易引发内存泄漏。建议在不再需要操作该ComponentContent对象时，开发者主动调用dispose释放后端节点，以减少引用关系的复杂性，降低内存泄漏的风险。同时，调用dispose的时候会将自己从父节点上移除。

### updateConfiguration

updateConfiguration(): void

传递[系统环境变化](../apis-ability-kit/js-apis-app-ability-configuration.md)事件，触发相关组件的全量更新。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

> **说明：**
>
> updateConfiguration接口用于通知对象当前的系统环境有变化。

**示例**

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
  FontWeight,
  ContentSlot,
  Button,
  ClickEvent
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeContent, FrameNode, ComponentContent } from '@ohos.arkui.node';

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
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = "hello";
  private content: NodeContent = new NodeContent();
  private componentContent: ComponentContent<Params> | undefined;

  build() {
    Row() {
      Column() {
        ContentSlot(this.content)
        Button("click me")
          .onClick((event: ClickEvent) => {
            let uiContext = this.getUIContext();
            let frameNode: FrameNode = new FrameNode(this.getUIContext());
            this.content.addFrameNode(frameNode);
            this.componentContent =
              new ComponentContent<Params>(uiContext, wrapBuilder(buildText), new Params(this.message))
            frameNode.addComponentContent(this.componentContent!);
            this.componentContent!.update(new Params("new message"));
          })
        Button("Dispose")
          .onClick((event: ClickEvent) => {
            this.componentContent?.dispose();
            this.componentContent = undefined;
          })
        Button("updateConfiguration")
          .onClick((event: ClickEvent) => {
            this.componentContent?.updateConfiguration();
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```
