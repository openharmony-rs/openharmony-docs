# ContentSlot

Renders components created using C-API on the native side and manages these components through the Content manager.

With support for hybrid development, the **ContentSlot** component is recommended when the container is an ArkTS component and the child component is created on the native side.

## ContentSlot

```TypeScript
ContentSlot(content: Content)
```

Creates a **ContentSlot** placeholder component for rendering components created on the native side in the Content manager.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ContentSlotInterface-(content: Content): ContentSlotAttribute--><!--Device-ContentSlotInterface-(content: Content): ContentSlotAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [Content](arkts-arkui-contentslot-comp-content-t.md) | Yes | Manager of **ContentSlot**. Through the APIs provided by the native side, it can register and trigger the callback for **ContentSlot** attach/detach events (i.e., when a component node is added to or removed from the component rendering tree) and manage child components of **ContentSlot**. |

## Summary

### Types

| Name | Description |
| --- | --- |
| [Content](arkts-arkui-contentslot-comp-content-t.md) | Defines a base class for **ComponentContent** and **NodeContent**. |

## Examples

The following example shows the basic usage of ContentSlot.

```TypeScript
import { nativeNode } from 'libNativeNode.so'; // Developer-implemented .so file.
import { NodeContent, Content } from '@kit.ArkUI';

@Entry
@Component
struct Parent {
  private nodeContent: Content = new NodeContent();

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
