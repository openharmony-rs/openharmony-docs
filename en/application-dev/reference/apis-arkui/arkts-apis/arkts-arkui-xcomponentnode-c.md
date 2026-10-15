# XComponentNode

```TypeScript
export declare class XComponentNode extends FrameNode
```

Provides APIs for the XComponentNode, which represents an XComponent in the component tree. You can write EGL/OpenGL ES and media data and display it on the XComponent, whose render type can be dynamically modified. It is suitable for scenarios where native self-rendering content needs to be embedded in the ArkUI component tree.

@extends FrameNode

**Inheritance/Implementation:** XComponentNode extends [FrameNode](arkts-arkui-framenode-c.md)

**Since:** 11

**Deprecated since:** 12

**Substitutes:** XComponent

<!--Device-unnamed-export declare class XComponentNode extends FrameNode--><!--Device-unnamed-export declare class XComponentNode extends FrameNode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changeRenderType

```TypeScript
changeRenderType(type: NodeRenderType): boolean
```

Dynamically changes the render type of the **XComponentNode**. The render policy can be switched dynamically at runtime, which is suitable for scenarios where different render types are selected based on content rendering requirements. For example, the **DISPLAY** type can be used when direct EGL/OpenGL ES drawing on the component is required; the **TEXTURE** type can be used when the rendered content needs to participate in composition as a texture (such as implementing semi-transparent overlay effects or off-screen rendering).

**Since:** 11

**Deprecated since:** 12

**Substitutes:** appendChild

**Model restriction:** This API can be used only in the stage model.

<!--Device-XComponentNode-changeRenderType(type: NodeRenderType): boolean--><!--Device-XComponentNode-changeRenderType(type: NodeRenderType): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | Yes | Target render type to change, specified using the NodeRenderType enumeration. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the render type is changed successfully. The value **true** indicates that the render type is changed successfully, and **false** indicates the opposite. |

## constructor

```TypeScript
constructor(uiContext: UIContext, options: RenderOptions,
    id: string, type: XComponentType, libraryName?: string)
```

Constructor used to create an XComponentNode. <br>You need to explicitly specify **selfIdealSize** in RenderOptions. Otherwise, the XComponentNode's content size is empty, resulting in no content being displayed.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** createNode

**Model restriction:** This API can be used only in the stage model.

<!--Device-XComponentNode-constructor(uiContext: UIContext, options: RenderOptions,    id: string, type: XComponentType, libraryName?: string)--><!--Device-XComponentNode-constructor(uiContext: UIContext, options: RenderOptions,    id: string, type: XComponentType, libraryName?: string)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UI context. For details about how to obtain it, see Obtaining UI Context. |
| options | [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | Yes | Rendering options of an XComponentNode, used to set node rendering related parameters such as the ideal size (**selfIdealSize**). |
| id | string | Yes | Unique ID of the **XComponent**. The value can contain a maximum of 128 characters. If the length exceeds the limit, the API fails to create the component. For details, see [XComponent](../arkui-ts/ts-basic-components-xcomponent.md). |
| type | [XComponentType](arkts-arkui-xcomponenttype-e.md) | Yes | Type of the **XComponent**, specified using the [XComponentType](../arkui-ts/ts-appendix-enums.md#xcomponenttype10) enumeration. For details, see [XComponent](../arkui-ts/ts-basic-components-xcomponent.md). |
| libraryName | string | No | Name of the dynamic library compiled and output at the native layer. If this parameter is not passed, the native dynamic library is not loaded by default. For details, see [XComponent](../arkui-ts/ts-basic-components-xcomponent.md). |

## onCreate

```TypeScript
onCreate(event?: Object): void
```

Called when the XComponentNode loading is complete.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** onLoad

**Model restriction:** This API can be used only in the stage model.

<!--Device-XComponentNode-onCreate(event?: Object): void--><!--Device-XComponentNode-onCreate(event?: Object): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Object | No | Event parameter of the **XComponent** instance, used to obtain the context of the **XComponent** instance. The APIs mounted on the context are defined by you at the C++ layer, and you can call the APIs registered at the native layer through this context. |

## onDestroy

```TypeScript
onDestroy(): void
```

Called when the XComponentNode is destroyed.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** onDestroy

**Model restriction:** This API can be used only in the stage model.

<!--Device-XComponentNode-onDestroy(): void--><!--Device-XComponentNode-onDestroy(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
