# NodeContent

```TypeScript
export class NodeContent extends Content
```

**NodeContent** is a manager for [ContentSlot](../arkts-components/arkts-arkui-contentslot-comp.md) provided by ArkUI. It manages the FrameNode node content mounted on **ContentSlot**, and supports dynamic addition and removal of FrameNodes. It is applicable to scenarios where FrameNode node content needs to be dynamically managed through **ContentSlot**, for example, dynamically adding or removing custom FrameNodes such as text and images based on user interactions.

> **NOTE:** 
> 
> - **NodeContent** objects do not support JSON serialization.

**Inheritance/Implementation:** NodeContent extends [Content](arkts-arkui-content-c.md)

**Since:** 12

<!--Device-unnamed-export class NodeContent extends Content--><!--Device-unnamed-export class NodeContent extends Content-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addFrameNode

```TypeScript
addFrameNode(node: FrameNode): void
```

Adds a FrameNode to **NodeContent**. After being added, the FrameNode is rendered and displayed through the associated **ContentSlot**. This is applicable to scenarios where the content nodes displayed in **ContentSlot** need to be dynamically managed, for example, dynamically adding custom FrameNodes such as text and images based on user interactions.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeContent-addFrameNode(node: FrameNode): void--><!--Device-NodeContent-addFrameNode(node: FrameNode): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | FrameNode to add, which must be a valid FrameNode that can be added. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100025](../errorcode-node.md#100025-invalid-parameter-value) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: it cannot be adopted."<br>**Applicable version:** 22 and later |

## constructor

```TypeScript
constructor()
```

A constructor used to create a **NodeContent** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeContent-constructor()--><!--Device-NodeContent-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
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

## removeFrameNode

```TypeScript
removeFrameNode(node: FrameNode): void
```

Removes a FrameNode from **NodeContent**. After being removed, the FrameNode is no longer displayed through **ContentSlot**. This is applicable to scenarios where added content nodes need to be dynamically removed, for example, removing specified custom FrameNodes such as text and images after user interactions.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeContent-removeFrameNode(node: FrameNode): void--><!--Device-NodeContent-removeFrameNode(node: FrameNode): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | FrameNode to remove. The node must have been added to the current **NodeContent**; otherwise, the removal is invalid. |

**Examples**

This example shows how to add and remove a FrameNode in NodeContent.

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
