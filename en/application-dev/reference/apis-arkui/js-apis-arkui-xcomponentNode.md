# XComponentNode
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!--deprecated_code_no_check-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-08-29T09:40:43.921Z pushedAt=2026-09-01T02:56:11.817Z -->

The XComponentNode module provides APIs for the XComponentNode, which represents an [XComponent](arkui-ts/ts-basic-components-xcomponent.md) in the component tree. You can write [EGL](../native-lib/egl.md)/[OpenGL ES](../native-lib/opengles.md) and media data and display it on the **XComponent**, whose render type can be dynamically modified. It is suitable for scenarios where native self-rendering content needs to be embedded in the ArkUI component tree.

> **NOTE**
>
> - The APIs of this module are supported since API version 11 and deprecated since API version 12. You are advised to use the APIs of the **typeNode** module in the [XComponent](./js-apis-arkui-frameNode.md#xcomponent12) type instead.
>
> - The APIs of this module can be used only in the stage model.
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - **XComponentNode** is not available in DevEco Studio Previewer.

## Modules to Import

```ts
import { XComponentNode } from '@kit.ArkUI';
```

## XComponentNode<sup>(deprecated)</sup>

### constructor<sup>(deprecated)</sup>

constructor(uiContext: UIContext, options: RenderOptions, id: string, type: XComponentType, libraryName?: string)

Constructor used to create an XComponentNode.

> **NOTE**
>
> This API is supported since API version 11 and deprecated since API version 12. You are advised to use [createNode](./js-apis-arkui-frameNode.md#createnodexcomponent12) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                                        | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| uiContext   | [UIContext](./arkts-apis-uicontext-uicontext.md)                      | Yes  | UI context. For details about how to obtain it, see [Obtaining UI Context](./js-apis-arkui-node.md#obtaining-ui-context). |
| options     | [RenderOptions](./js-apis-arkui-builderNode.md#renderoptions) | Yes  | Rendering options of an XComponentNode, used to set node rendering related parameters such as the ideal size (**selfIdealSize**). |
| id          | string                                                       | Yes  | Unique ID of the **XComponent**. The value can contain a maximum of 128 characters. If the length exceeds the limit, the API fails to create the component. For details, see [XComponent](arkui-ts/ts-basic-components-xcomponent.md). |
| type        | [XComponentType](arkui-ts/ts-appendix-enums.md#xcomponenttype10) | Yes  | Type of the **XComponent**, specified using the [XComponentType](arkui-ts/ts-appendix-enums.md#xcomponenttype10) enumeration. For details, see [XComponent](arkui-ts/ts-basic-components-xcomponent.md). |
| libraryName | string                                                       | No   | Name of the dynamic library compiled and output at the native layer. If this parameter is not passed, the native dynamic library is not loaded by default. For details, see [XComponent](arkui-ts/ts-basic-components-xcomponent.md). |

> **NOTE**
>
> You need to explicitly specify **selfIdealSize** in [RenderOptions](./js-apis-arkui-builderNode.md#renderoptions). Otherwise, the XComponentNode's content size is empty, resulting in no content being displayed.

### onCreate<sup>(deprecated)</sup>

onCreate(event?: Object): void

Called when the XComponentNode loading is complete.

> **NOTE**
>
> This API is supported since API version 11 and deprecated since API version 12. You are advised to use [onLoad](arkui-ts/ts-basic-components-xcomponent.md#onload) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| event  | Object | No   | Event parameter of the **XComponent** instance, used to obtain the context of the **XComponent** instance. The APIs mounted on the context are defined by you at the C++ layer, and you can call the APIs registered at the native layer through this context. |

### onDestroy<sup>(deprecated)</sup>

onDestroy(): void

Called when the XComponentNode is destroyed.

> **NOTE**
>
> This API is supported since API version 11 and deprecated since API version 12. You are advised to use [onDestroy](arkui-ts/ts-basic-components-xcomponent.md#ondestroy) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### changeRenderType<sup>(deprecated)</sup>

changeRenderType(type: NodeRenderType): boolean

Dynamically changes the render type of the **XComponentNode**. The render policy can be switched dynamically at runtime, which is suitable for scenarios where different render types are selected based on content rendering requirements. For example, the **DISPLAY** type can be used when direct EGL/OpenGL ES drawing on the component is required; the **TEXTURE** type can be used when the rendered content needs to participate in composition as a texture (such as implementing semi-transparent overlay effects or off-screen rendering).

> **NOTE**
>
> This API is supported since API version 11 and deprecated since API version 12. You are advised to use [appendChild](./js-apis-arkui-frameNode.md#appendchild12) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                    | Mandatory| Description            |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| type   | [NodeRenderType](./js-apis-arkui-builderNode.md#noderendertype) | Yes | Target render type to change, specified using the [NodeRenderType](./js-apis-arkui-builderNode.md#noderendertype) enumeration. |

**Return value**

| Type| Description                  |
| ---- | ---------------------- |
| boolean | Whether the render type is changed successfully. The value **true** indicates that the render type is changed successfully, and **false** indicates the opposite. |

## Example

```ts
import { NodeController, FrameNode, XComponentNode, NodeRenderType, XComponentType, UIContext } from '@kit.ArkUI';

class XComponentNodeController extends NodeController {
  private xComponentNode: MyXComponentNode | null = null;
  private soName: string = 'tetrahedron_napi'; // This .so file is written and generated by you using the Node-API.

  constructor() {
    super();
  }

  makeNode(context: UIContext): FrameNode | null {
    this.xComponentNode = new MyXComponentNode(context, {
      selfIdealSize: { width: 200, height: 200 }
    }, 'xComponentId', XComponentType.SURFACE, this.soName);
    return this.xComponentNode;
  }

  changeRenderType(renderType: NodeRenderType): void {
    if (this.xComponentNode) {
      this.xComponentNode.changeRenderType(renderType);
    }
  }
}

class MyXComponentNode extends XComponentNode {
  onCreate(event: Object) {
    // do something when XComponentNode has created
  }

  onDestroy() {
    // do something when XComponentNode is destroying
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        NodeContainer(new XComponentNodeController())
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

![XComponentNodeSample](figures/xcomponent_node.jpg)

<!--Del-->
> **NOTE**
>
> The native layer compilation output in this example references the [OpenGL Triangular Pyramid](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/NdkOpenGL) (API version 10) dynamic library. To build the complete example, download that project and copy all files from its **cpp** directory to your current project's **cpp** directory.
<!--DelEnd-->
