# ContentSlot
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @HelloCrease-->

The **ContentSlot** component is a component designed to render and manage components created on the native layer using C APIs.

With support for hybrid development, the **ContentSlot** component is recommended when the container is an ArkTS component and the child component is created on the native side.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## APIs

ContentSlot(content: Content)

Called when content is added to a placeholder component

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type| Mandatory| Description                                                    |
| ------- | -------- | ---- | ------------------------------------------------------------ |
| content | [Content](#content)  | Yes  | Manager of the **ContentSlot** component. Through the APIs provided by the native side, it can register and trigger the attach and detach event callbacks for **ContentSlot**, as well as manage the child components of **ContentSlot**.|

## Content

type Content = Content

Defines a base class for **ComponentContent** and **NodeContent**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type| Description                                                    |
| ---- | ------------------------------------------------------------ |
| [Content](../js-apis-arkui-Content.md)   | Base class for **ComponentContent** and **NodeContent**.|

## Example

The following example shows the basic usage of **ContentSlot**.

```ts
import { nativeNode } from 'libNativeNode.so'; // .so file you implemented
import { NodeContent } from '@kit.ArkUI';

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

For details about the implementation of the .so file in the preceding code, see [Native XComponent](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/NdkXComponent).
