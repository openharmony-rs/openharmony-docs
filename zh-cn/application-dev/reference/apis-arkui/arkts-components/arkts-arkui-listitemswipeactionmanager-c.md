# ListItemSwipeActionManager

ListItem划出菜单的管理器。

**起始版本：** 21

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## collapse

```TypeScript
static collapse(node: FrameNode): void
```

收起指定ListItem的划出菜单。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | ListItem节点对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../errorcode-node.md#100023-参数错误) | The component type of the node is incorrect. |
| [106203](../errorcode-node.md#106203-传入的节点未挂载到组件树上) | The node not mounted to component tree. |

## expand

```TypeScript
static expand(node: FrameNode, direction: ListItemSwipeActionDirection): void
```

展开指定ListItem的划出菜单。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | ListItem节点对象。 |
| direction | ListItemSwipeActionDirection | 是 | ListItem划出菜单的展开方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../errorcode-node.md#100023-参数错误) | The component type of the node is incorrect. |
| [106203](../errorcode-node.md#106203-传入的节点未挂载到组件树上) | The node not mounted to component tree. |

