# NodeContent

NodeContent是节点内容的实体封装。

**继承/实现关系：** NodeContent extends Content

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class NodeContent--><!--Device-unnamed-export declare class NodeContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addFrameNode

```TypeScript
addFrameNode(node: FrameNode): void
```

根据参数将 FrameNode 添加到 NodeContent 中。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeContent-addFrameNode(node: FrameNode): void--><!--Device-NodeContent-addFrameNode(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | 待添加的 FrameNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../../apis-arkui/errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: it cannot be adopted." |

## constructor

```TypeScript
constructor()
```

构造函数

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeContent-constructor()--><!--Device-NodeContent-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## removeFrameNode

```TypeScript
removeFrameNode(node: FrameNode): void
```

移除目标FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeContent-removeFrameNode(node: FrameNode): void--><!--Device-NodeContent-removeFrameNode(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | 被移除的FrameNode。 |

