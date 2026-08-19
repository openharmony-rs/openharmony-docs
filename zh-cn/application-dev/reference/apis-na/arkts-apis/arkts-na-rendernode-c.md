# RenderNode

提供自绘制渲染节点RenderNode，支持开发者通过C API进行开发，完成自定义绘制需求。 > **说明：** > > - 不建议对[BuilderNode](../../apis-arkui/arkts-apis/arkts-arkui-buildernode-c.md)中的RenderNode进行修改操作。BuilderNode中持有的FrameNode仅用于将该 > BuilderNode作为子节点挂载到其他FrameNode上，对该FrameNode或对应的RenderNode进行属性设置与子节点操作可能会产生未定义行为，包括但不限于显示异常、事件异常、稳定性问题等。 > > - RenderNode对象不支持使用JSON序列化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class RenderNode--><!--Device-unnamed-export declare class RenderNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appendChild

```TypeScript
appendChild(node: RenderNode): void
```

在RenderNode最后一个子节点后添加新的子节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-appendChild(node: RenderNode): void--><!--Device-RenderNode-appendChild(node: RenderNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [RenderNode](arkts-na-rendernode-c.md) | 是 | 需要添加的RenderNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../../apis-arkui/errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: its corresponding FrameNode cannot be adopted." |

## clearChildren

```TypeScript
clearChildren(): void
```

清除当前RenderNode的所有子节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-clearChildren(): void--><!--Device-RenderNode-clearChildren(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

RenderNode的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-constructor()--><!--Device-RenderNode-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dispose

```TypeScript
dispose(): void
```

立即释放当前RenderNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-dispose(): void--><!--Device-RenderNode-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## draw

```TypeScript
draw(context: DrawContext): void
```

绘制方法，需要开发者进行实现。该方法会在RenderNode进行绘制时被调用。 该接口的[DrawContext](../../apis-arkui/arkts-apis/arkts-arkui-graphics-drawcontext-c.md)中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见 [调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-arktsNode-renderNode.md#调整自定义绘制canvas的变换矩阵)。 > **说明：** > > RenderNode初始化时，会调用两次draw方法。第一次调用是在首次创建FrameNode时触发Render流程，第二次调用是在首次设置modifier时触发绘制。后续绘制流程皆由modifier触发。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-draw(context: DrawContext): void--><!--Device-RenderNode-draw(context: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [DrawContext](../../apis-arkui/arkts-apis/arkts-arkui-graphics-drawcontext-c.md) | 是 | 图形绘制上下文。 |

## getChild

```TypeScript
getChild(index: int): RenderNode | null
```

通过索引获取当前RenderNode的子节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-getChild(index: int): RenderNode | null--><!--Device-RenderNode-getChild(index: int): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 需要查询的子节点的序列号。 <br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-na-rendernode-c.md) | Returns a RenderNode. When the required node does not exist, returns null. |

## getFirstChild

```TypeScript
getFirstChild(): RenderNode | null
```

获取当前RenderNode的第一个子节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-getFirstChild(): RenderNode | null--><!--Device-RenderNode-getFirstChild(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-na-rendernode-c.md) | Returns a RenderNode, which is first child of the current RenderNode. If current RenderNode does not have child node, returns null. |

## getNextSibling

```TypeScript
getNextSibling(): RenderNode | null
```

获取当前RenderNode的下一个同级节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-getNextSibling(): RenderNode | null--><!--Device-RenderNode-getNextSibling(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-na-rendernode-c.md) | Returns a RenderNode. If current RenderNode does not have next sibling node, returns null. |

## getPreviousSibling

```TypeScript
getPreviousSibling(): RenderNode | null
```

获取当前RenderNode的上一个同级节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-getPreviousSibling(): RenderNode | null--><!--Device-RenderNode-getPreviousSibling(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-na-rendernode-c.md) | Returns a RenderNode. |

## insertChildAfter

```TypeScript
insertChildAfter(child: RenderNode, sibling: RenderNode | null): void
```

在RenderNode指定子节点之后添加新的子节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-insertChildAfter(child: RenderNode, sibling: RenderNode | null): void--><!--Device-RenderNode-insertChildAfter(child: RenderNode, sibling: RenderNode | null): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [RenderNode](arkts-na-rendernode-c.md) | 是 | 需要添加的子节点。 |
| sibling | [RenderNode](arkts-na-rendernode-c.md) \| null | 是 | 新节点将插入到该节点之后。若该参数设置为空，则新节点将插入到首个子节点之前。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../../apis-arkui/errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: its corresponding FrameNode cannot be adopted." |

## invalidate

```TypeScript
invalidate(): void
```

该方法会触发RenderNode的重新渲染。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-invalidate(): void--><!--Device-RenderNode-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前RenderNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在 dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-isDisposed(): boolean--><!--Device-RenderNode-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

## removeChild

```TypeScript
removeChild(node: RenderNode): void
```

从RenderNode中删除指定的子节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderNode-removeChild(node: RenderNode): void--><!--Device-RenderNode-removeChild(node: RenderNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [RenderNode](arkts-na-rendernode-c.md) | 是 | 需要删除的子节点。 |

