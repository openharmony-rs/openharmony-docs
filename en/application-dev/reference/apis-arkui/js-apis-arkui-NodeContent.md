# NodeContent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=033859cddd4818ba4c62bad26b6ee850b2b31a63 translatedAt=2026-08-29T09:35:37.491Z pushedAt=2026-08-31T11:36:14.710Z -->

**NodeContent** is a manager for [ContentSlot](./arkui-ts/ts-components-contentSlot.md) provided by ArkUI. It manages the FrameNode node content mounted on **ContentSlot**, and supports dynamic addition and removal of FrameNodes. It is applicable to scenarios where FrameNode node content needs to be dynamically managed through **ContentSlot**, for example, dynamically adding or removing custom FrameNodes such as text and images based on user interactions.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - **NodeContent** objects do not support JSON serialization.

## Modules to Import

```ts
import { NodeContent } from '@kit.ArkUI';
```

## NodeContent

An entity encapsulation of node content. It provides management capabilities such as dynamic addition and removal of FrameNodes, and is applicable to scenarios where the content nodes displayed in **ContentSlot** need to be dynamically managed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

A constructor used to create a **NodeContent** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

<!--code_no_check-->

```ts
import { nativeNode } from 'libNativeNode.so'; // Developer-implemented .so file.
import { NodeContent } from '@kit.ArkUI';

@Component
struct Parent {
  private nodeContent: NodeContent = new NodeContent();

  aboutToAppear() {
    // Create a node through the C API and add it to the nodeContent manager.
    nativeNode.createNativeNode(this.nodeContent);
  }

  build() {
    Column() {
      // Display the native components stored in the nodeContent manager.
      ContentSlot(this.nodeContent)
    }
  }
}
```

For details about the implementation of the .so file in the preceding code, see <!--RP1-->[Native XComponent](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeXComponent)<!--RP1End-->.

### addFrameNode

addFrameNode(node: FrameNode): void

Adds a FrameNode to **NodeContent**. After being added, the FrameNode is rendered and displayed through the associated **ContentSlot**. This is applicable to scenarios where the content nodes displayed in **ContentSlot** need to be dynamically managed, for example, dynamically adding custom FrameNodes such as text and images based on user interactions.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                  | Mandatory| Description            |
| ------- | ------------------------------------------------------ | ---- | ---------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | Yes | FrameNode to add, which must be a valid FrameNode that can be added. |

**Error codes**

For details about the error codes, see [Custom Node Error Codes](./errorcode-node.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 100025 | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: it cannot be adopted." <br>Applicable versions: 22+|

### removeFrameNode

removeFrameNode(node: FrameNode): void

Removes a FrameNode from **NodeContent**. After being removed, the FrameNode is no longer displayed through **ContentSlot**. This is applicable to scenarios where added content nodes need to be dynamically removed, for example, removing specified custom FrameNodes such as text and images after user interactions.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                  | Mandatory| Description            |
| ------- | ------------------------------------------------------ | ---- | ---------------- |
| node | [FrameNode](./js-apis-arkui-frameNode.md) | Yes | FrameNode to remove. The node must have been added to the current **NodeContent**; otherwise, the removal is invalid. |

**Example**

This example shows how to add and remove a FrameNode in **NodeContent**.

```ts
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