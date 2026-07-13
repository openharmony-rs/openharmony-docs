# NodeContent

NodeContent是节点内容的实体封装。

**继承/实现关系：** NodeContent extends [Content](arkts-arkui-content-c.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addFrameNode

```TypeScript
addFrameNode(node: FrameNode): void
```

根据参数将FrameNode添加到NodeContent中。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 需要添加的FrameNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reasonare included in the error message.For example: "The parameter 'node' is invalid: it cannot be adopted."<br>**适用版本：** 22+ |

## constructor

```TypeScript
constructor()
```

节点内容的实体封装。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## removeFrameNode

```TypeScript
removeFrameNode(node: FrameNode): void
```

根据参数将FrameNode从NodeContent中删除。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 需要删除的FrameNode。 |

