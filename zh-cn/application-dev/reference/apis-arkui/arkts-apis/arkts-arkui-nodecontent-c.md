# NodeContent

NodeContent是ArkUI提供的ContentSlot的管理器，用于管理挂载到ContentSlot上的FrameNode节点内 容，支持动态添加、删除FrameNode节点。适用于需要通过ContentSlot动态管理FrameNode节点内容的场景，例如根据用户交互动态新增或移除文本、图片等自定义FrameNode节点。 > **说明：** > > - NodeContent对象不支持使用JSON序列化。

**继承/实现关系：** NodeContent extends Content

**起始版本：** 12

<!--Device-unnamed-export class NodeContent--><!--Device-unnamed-export class NodeContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addFrameNode

```TypeScript
addFrameNode(node: FrameNode): void
```

将FrameNode添加到NodeContent中，添加后FrameNode将通过关联的ContentSlot渲染显示。适用于需要动态管理ContentSlot中显示内容节点的场景，例如根据用户交互动态新增文本、图片等自定义 FrameNode节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeContent-addFrameNode(node: FrameNode): void--><!--Device-NodeContent-addFrameNode(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 需要添加的FrameNode，该节点需为可被添加的有效FrameNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: it cannot be adopted."<br>**适用版本：** 22+ |

## constructor

```TypeScript
constructor()
```

节点内容的实体封装。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeContent-constructor()--><!--Device-NodeContent-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { nativeNode } from 'libNativeNode.so'; // 开发者自己实现的so
import { NodeContent } from '@kit.ArkUI';

@Component
struct Parent {
  private nodeContent: NodeContent = new NodeContent();

  aboutToAppear() {
    // 通过C-API创建节点，并添加到管理器nodeContent上
    nativeNode.createNativeNode(this.nodeContent);
  }

  build() {
    Column() {
      // 显示nodeContent管理器里存放的Native侧的组件
      ContentSlot(this.nodeContent)
    }
  }
}
```

## removeFrameNode

```TypeScript
removeFrameNode(node: FrameNode): void
```

将FrameNode从NodeContent中删除，删除后FrameNode将不再通过ContentSlot显示。适用于需要动态移除已添加内容节点的场景，例如用户交互后移除指定的文本、图片等自定义FrameNode节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeContent-removeFrameNode(node: FrameNode): void--><!--Device-NodeContent-removeFrameNode(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 需要删除的FrameNode，该节点需已添加到当前NodeContent中，若未添加则删除无效。 |

**示例**

添加和删除NodeContent中的FrameNode节点。

```TypeScript
// xxx.ets
import { NodeContent, typeNode } from '@kit.ArkUI';

class NodeContentCtrl {
  content: NodeContent;
  textNode: Array<typeNode.Text> = new Array();
  uiContext: UIContext;

  constructor(uiContext: UIContext) {
    this.content = new NodeContent();
    this.uiContext = uiContext;
  }

  addNode() {
    let node = typeNode.createNode(this.uiContext, 'Text');
    node.initialize('ContentText:' + this.textNode.length).fontSize(20);
    this.textNode.push(node);
    this.content.addFrameNode(node);
  }

  removeNode() {
    let node = this.textNode.pop();
    if (node) {
      this.content.removeFrameNode(node);
    }
  }

  removeFront() {
    let node = this.textNode.shift();
    if (node) {
      this.content.removeFrameNode(node);
    }
  }

  getContent(): NodeContent {
    return this.content;
  }
}

@Entry
@Component
struct Index {
  controller = new NodeContentCtrl(this.getUIContext());

  build() {
    Row() {
      Column() {
        ContentSlot(this.controller.getContent())
        Button('AddToSlot')
          .onClick(() => {
            this.controller.addNode();
          })
        Button('RemoveBack')
          .onClick(() => {
            this.controller.removeNode();
          })
        Button('RemoveFront')
          .onClick(() => {
            this.controller.removeFront();
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

