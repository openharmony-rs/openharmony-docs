# XComponentNode

Defines XComponent Node.

@extends FrameNode

**Inheritance/Implementation:** XComponentNode extends [FrameNode](arkts-arkui-framenode-c.md)

**Since:** 11

**Deprecated since:** 12

**Substitutes:** XComponent

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changeRenderType

```TypeScript
changeRenderType(type: NodeRenderType): boolean
```

Set the render type of the builderNode.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** appendChild

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | Yes | render type |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns if change the render type successfully. |

## constructor

```TypeScript
constructor(uiContext: UIContext, options: RenderOptions,
    id: string, type: XComponentType, libraryName?: string)
```

constructor.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** createNode

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UIContext used to create the FrameNode |
| options | [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | Yes | Render options of the Builder Node |
| id | string | Yes | XComponent id defined by the application |
| type | [XComponentType](arkts-arkui-xcomponenttype-e.md) | Yes | XComponent type |
| libraryName | string | No | The name of the library to be loaded by XComponent |

## onCreate

```TypeScript
onCreate(event?: Object): void
```

Called when the XComponent surface has been created.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** onLoad

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Object | No | event from native when the library loaded |

## onDestroy

```TypeScript
onDestroy(): void
```

Called when the XComponent surface has been destroyed.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** onDestroy

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
