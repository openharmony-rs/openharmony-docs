# NodeContent

NodeContent是节点内容的实体封装。

**继承/实现关系：** NodeContent extends [Content](arkts-arkui-content-c.md)

**起始版本：** 12

<!--Device-unnamed-export class NodeContent extends Content--><!--Device-unnamed-export class NodeContent extends Content-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="addframenode"></a>
## addFrameNode

```TypeScript
addFrameNode(node: FrameNode): void
```

根据参数将FrameNode添加到NodeContent中。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeContent-addFrameNode(node: FrameNode): void--><!--Device-NodeContent-addFrameNode(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 是 | 需要添加的FrameNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message.For example: "The parameter 'node' is invalid: it cannot be adopted."<br>**适用版本：** 22+ |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

节点内容的实体封装。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeContent-constructor()--><!--Device-NodeContent-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="removeframenode"></a>
## removeFrameNode

```TypeScript
removeFrameNode(node: FrameNode): void
```

根据参数将FrameNode从NodeContent中删除。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeContent-removeFrameNode(node: FrameNode): void--><!--Device-NodeContent-removeFrameNode(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 是 | 需要删除的FrameNode。 |

