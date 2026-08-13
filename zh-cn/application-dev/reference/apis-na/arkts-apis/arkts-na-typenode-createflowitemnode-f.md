# createFlowItemNode

## createFlowItemNode

```TypeScript
export function createFlowItemNode(context: UIContext, options?: FrameNodeOptions): FlowItem
```

创建 FlowItem 类型的 FrameNode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function createFlowItemNode(context: UIContext, options?: FrameNodeOptions): FlowItem--><!--Device-typeNode-export function createFlowItemNode(context: UIContext, options?: FrameNodeOptions): FlowItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 用于创建 FrameNode 的 UI 上下文 |
| options | [FrameNodeOptions](arkts-na-framenode-framenodeoptions-i.md) | 否 | Options for configuring FrameNode creation.<br>**起始版本：** 24 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FlowItem | 返回 FlowItem 类型的 FrameNode |

