# ContentSlot

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d89c4be0c26be57dcac6e3a0bb8b7f968642aa19 translatedAt=2026-07-30T02:33:56.675Z pushedAt=2026-08-01T06:42:55.879Z -->

Renders components created using C-API on the native side and manages these components through the Content manager.

With support for hybrid development, the **ContentSlot** component is recommended when the container is an ArkTS component and the child component is created on the native side.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## APIs

ContentSlot(content: Content)

Creates a **ContentSlot** placeholder component for rendering components created on the native side in the Content manager.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type| Mandatory| Description                                                    |
| ------- | -------- | ---- | ------------------------------------------------------------ |
| content | [Content](#content) | Yes | Manager of **ContentSlot**. Through the APIs provided by the native side, it can register and trigger the callback for **ContentSlot** attach/detach events (i.e., when a component node is added to or removed from the component rendering tree) and manage child components of **ContentSlot**. |

## Content

type Content = import('../api/@ohos.arkui.node').Content

Defines a base class for **ComponentContent** and **NodeContent**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type| Description                                                    |
| ---- | ------------------------------------------------------------ |
| import('../api/@ohos.arkui.node').[Content](../js-apis-arkui-Content.md)   | Defines the base class of ComponentContent and NodeContent. |

## Example

The following example shows the basic usage of **ContentSlot**.

```ts
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

For the implementation of the .so file in the above code, see [Native XComponent](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeXComponent).