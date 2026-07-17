# RenderNode

提供自绘制渲染节点RenderNode，支持开发者通过C API进行开发，完成自定义绘制需求。

> **说明：**

> - 不建议对[BuilderNode](arkts-arkui-buildernode-c.md)中的RenderNode进行修改操作。BuilderNode中持有的[FrameNode](arkts-arkui-framenode-c.md)仅用于将该  
> BuilderNode作为子节点挂载到其他FrameNode上，对该FrameNode或对应的RenderNode进行属性设置与子节点操作可能会产生未定义行为，包括但不限于显示异常、事件异常、稳定性问题等。  
>  
> - RenderNode对象不支持使用JSON序列化。

**起始版本：** 11

<!--Device-unnamed-export class RenderNode--><!--Device-unnamed-export class RenderNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appendChild

```TypeScript
appendChild(node: RenderNode): void
```

在RenderNode最后一个子节点后添加新的子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-appendChild(node: RenderNode): void--><!--Device-RenderNode-appendChild(node: RenderNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [RenderNode](arkts-arkui-rendernode-c.md) | 是 | 需要添加的RenderNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: its corresponding FrameNode cannot be adopted."<br>**适用版本：** 22+ |

## clearChildren

```TypeScript
clearChildren(): void
```

清除当前RenderNode的所有子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-clearChildren(): void--><!--Device-RenderNode-clearChildren(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

RenderNode的构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-constructor()--><!--Device-RenderNode-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dispose

```TypeScript
dispose(): void
```

立即释放当前RenderNode。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-dispose(): void--><!--Device-RenderNode-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## draw

```TypeScript
draw(context: DrawContext): void
```

绘制方法，需要开发者进行实现。该方法会在RenderNode进行绘制时被调用。

该接口的[DrawContext](arkts-arkui-graphics-drawcontext-c.md)中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见[调整自定义绘制Canvas的变换矩阵](../../../../ui/arkts-user-defined-arktsNode-renderNode.md#调整自定义绘制canvas的变换矩阵)。

> **说明：**  
>  
> RenderNode初始化时，会调用两次draw方法。第一次调用是在首次创建FrameNode时触发Render流程，第二次调用是在首次设置modifier时触发绘制。后续绘制流程皆由modifier触发。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-draw(context: DrawContext): void--><!--Device-RenderNode-draw(context: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [DrawContext](../arkts-components/arkts-arkui-drawcontext-t.md) | 是 | 图形绘制上下文。 |

## getChild

```TypeScript
getChild(index: number): RenderNode | null
```

获取当前RenderNode指定位置的子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-getChild(index: number): RenderNode | null--><!--Device-RenderNode-getChild(index: number): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 需要查询的子节点的序列号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-arkui-rendernode-c.md) | Child node obtained. If the RenderNode does not contain the specified child node,null is returned. |

## getFirstChild

```TypeScript
getFirstChild(): RenderNode | null
```

获取当前RenderNode的第一个子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-getFirstChild(): RenderNode | null--><!--Device-RenderNode-getFirstChild(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-arkui-rendernode-c.md) | First child node. If the RenderNode does not contain any child node, null is returned. |

## getNextSibling

```TypeScript
getNextSibling(): RenderNode | null
```

获取当前RenderNode的下一个同级节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-getNextSibling(): RenderNode | null--><!--Device-RenderNode-getNextSibling(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-arkui-rendernode-c.md) | Next sibling node of the current RenderNode. If the RenderNode does not have the next sibling node, null is returned. |

## getPreviousSibling

```TypeScript
getPreviousSibling(): RenderNode | null
```

获取当前RenderNode的上一个同级节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-getPreviousSibling(): RenderNode | null--><!--Device-RenderNode-getPreviousSibling(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-arkui-rendernode-c.md) | Previous sibling node of the current RenderNode. If the RenderNode does not have the previous sibling node, null is returned. |

## insertChildAfter

```TypeScript
insertChildAfter(child: RenderNode, sibling: RenderNode | null): void
```

在RenderNode指定子节点之后添加新的子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-insertChildAfter(child: RenderNode, sibling: RenderNode | null): void--><!--Device-RenderNode-insertChildAfter(child: RenderNode, sibling: RenderNode | null): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [RenderNode](arkts-arkui-rendernode-c.md) | 是 | 需要添加的子节点。 |
| sibling | RenderNode \| null | 是 | 需要添加的子节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: its corresponding FrameNode cannot be adopted."<br>**适用版本：** 22+ |

## invalidate

```TypeScript
invalidate(): void
```

该方法会触发RenderNode的重新渲染。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-invalidate(): void--><!--Device-RenderNode-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前RenderNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

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

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-removeChild(node: RenderNode): void--><!--Device-RenderNode-removeChild(node: RenderNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [RenderNode](arkts-arkui-rendernode-c.md) | 是 | 需要删除的子节点。 |

## backgroundBlur

```TypeScript
get backgroundBlur(): BackgroundBlur
```

获取背景模糊效果。

**类型：** BackgroundBlur

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get backgroundBlur(): BackgroundBlur--><!--Device-RenderNode-get backgroundBlur(): BackgroundBlur-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
get backgroundColor(): number
```

Get the background color of the RenderNode.

**类型：** number

**默认值：** 0X00000000 [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get backgroundColor(): number--><!--Device-RenderNode-get backgroundColor(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
get borderColor(): Edges<number>
```

Get border color of the RenderNode.

**类型：** Edges<number>

**默认值：** 0XFF000000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get borderColor(): Edges<number>--><!--Device-RenderNode-get borderColor(): Edges<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
get borderRadius(): BorderRadiuses
```

Get border radius of the RenderNode.

**类型：** BorderRadiuses

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get borderRadius(): BorderRadiuses--><!--Device-RenderNode-get borderRadius(): BorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
get borderStyle(): Edges<BorderStyle>
```

获取当前RenderNode的边框样式。

**类型：** Edges<BorderStyle>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get borderStyle(): Edges<BorderStyle>--><!--Device-RenderNode-get borderStyle(): Edges<BorderStyle>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
get borderWidth(): Edges<number>
```

Get border width of the RenderNode.

**类型：** Edges<number>

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get borderWidth(): Edges<number>--><!--Device-RenderNode-get borderWidth(): Edges<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clipToFrame

```TypeScript
get clipToFrame(): boolean
```

Get whether the RenderNode clip to frame.

**类型：** boolean

**默认值：** true [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get clipToFrame(): boolean--><!--Device-RenderNode-get clipToFrame(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentBlur

```TypeScript
get contentBlur(): ContentBlur
```

获取内容模糊效果。

**类型：** ContentBlur

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get contentBlur(): ContentBlur--><!--Device-RenderNode-get contentBlur(): ContentBlur-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foregroundBlur

```TypeScript
get foregroundBlur(): ForegroundBlur
```

获取前景模糊效果。

**类型：** ForegroundBlur

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get foregroundBlur(): ForegroundBlur--><!--Device-RenderNode-get foregroundBlur(): ForegroundBlur-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## frame

```TypeScript
get frame(): Frame
```

Get frame info of the RenderNode.

**类型：** Frame

**默认值：** Frame { x: 0, y: 0, width: 0, height: 0 } [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get frame(): Frame--><!--Device-RenderNode-get frame(): Frame-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
get label(): string
```

获取当前RenderNode的标签。默认值为""。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get label(): string--><!--Device-RenderNode-get label(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lengthMetricsUnit

```TypeScript
get lengthMetricsUnit(): LengthMetricsUnit
```

Get the length metrics unit of RenderNode.

**类型：** LengthMetricsUnit

**默认值：** LengthMetricsUnit.DEFAULT

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get lengthMetricsUnit(): LengthMetricsUnit--><!--Device-RenderNode-get lengthMetricsUnit(): LengthMetricsUnit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## markNodeGroup

```TypeScript
get markNodeGroup(): boolean
```

Get whether to preferentially draw the node and its children.

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get markNodeGroup(): boolean--><!--Device-RenderNode-get markNodeGroup(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
get opacity(): number
```

Get opacity of the RenderNode.

**类型：** number

**默认值：** 1 [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get opacity(): number--><!--Device-RenderNode-get opacity(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pivot

```TypeScript
get pivot(): Pivot
```

Get pivot vector of the RenderNode.

**类型：** Pivot

**默认值：** Pivot { x: 0.5, y: 0.5 } [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get pivot(): Pivot--><!--Device-RenderNode-get pivot(): Pivot-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
get position(): Position
```

Get frame position of the RenderNode.

**类型：** Position

**默认值：** Position { x: 0, y: 0 } [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get position(): Position--><!--Device-RenderNode-get position(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotation

```TypeScript
get rotation(): Rotation
```

Get rotation vector of the RenderNode.

**类型：** Rotation

**默认值：** Rotation { x: 0, y: 0, z: 0 } [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get rotation(): Rotation--><!--Device-RenderNode-get rotation(): Rotation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
get scale(): Scale
```

Get scale vector of the RenderNode.

**类型：** Scale

**默认值：** Scale { x: 1, y: 1 } [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get scale(): Scale--><!--Device-RenderNode-get scale(): Scale-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowAlpha

```TypeScript
get shadowAlpha(): number
```

Get shadow alpha of the RenderNode.

**类型：** number

**默认值：** 0 [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get shadowAlpha(): number--><!--Device-RenderNode-get shadowAlpha(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowColor

```TypeScript
get shadowColor(): number
```

Get shadow color of the RenderNode.

**类型：** number

**默认值：** 0X00000000 [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get shadowColor(): number--><!--Device-RenderNode-get shadowColor(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowElevation

```TypeScript
get shadowElevation(): number
```

Get shadow elevation of the RenderNode.

**类型：** number

**默认值：** 0 [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get shadowElevation(): number--><!--Device-RenderNode-get shadowElevation(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowOffset

```TypeScript
get shadowOffset(): Offset
```

Get shadow offset of the RenderNode.

**类型：** Offset

**默认值：** Offset { x: 0, y: 0 } [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get shadowOffset(): Offset--><!--Device-RenderNode-get shadowOffset(): Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadowRadius

```TypeScript
get shadowRadius(): number
```

Get shadow radius of the RenderNode.

**类型：** number

**默认值：** 0 [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get shadowRadius(): number--><!--Device-RenderNode-get shadowRadius(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shapeClip

```TypeScript
get shapeClip(): ShapeClip
```

获取目标RenderNode的形状裁剪属性

**类型：** ShapeClip

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get shapeClip(): ShapeClip--><!--Device-RenderNode-get shapeClip(): ShapeClip-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shapeMask

```TypeScript
get shapeMask(): ShapeMask
```

获取当前RenderNode的遮罩。

**类型：** ShapeMask

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get shapeMask(): ShapeMask--><!--Device-RenderNode-get shapeMask(): ShapeMask-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
get size(): Size
```

Get frame size of the RenderNode.

**类型：** Size

**默认值：** Size { width: 0, height: 0 } [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get size(): Size--><!--Device-RenderNode-get size(): Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transform

```TypeScript
get transform(): Matrix4
```

Get transform info of the RenderNode.

**类型：** Matrix4

**默认值：** Matrix4 [ 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1 ] [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get transform(): Matrix4--><!--Device-RenderNode-get transform(): Matrix4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## translation

```TypeScript
get translation(): Translation
```

Get translation vector of the RenderNode.

**类型：** Translation

**默认值：** Translation { x: 0, y: 0 } [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-get translation(): Translation--><!--Device-RenderNode-get translation(): Translation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

