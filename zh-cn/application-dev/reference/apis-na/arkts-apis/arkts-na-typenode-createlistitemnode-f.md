# createListItemNode

## createListItemNode

```TypeScript
export function createListItemNode(context: UIContext, options?: FrameNodeOptions): ListItem
```

创建 ListItem 类型的 FrameNode

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function createListItemNode(context: UIContext, options?: FrameNodeOptions): ListItem--><!--Device-typeNode-export function createListItemNode(context: UIContext, options?: FrameNodeOptions): ListItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | 用于创建 FrameNode 的 UI 上下文 |
| options | [FrameNodeOptions](arkts-na-framenode-framenodeoptions-i.md) | 否 | Options for configuring FrameNode creation.<br>**起始版本：** 24 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ListItem | 返回 ListItem 类型的 FrameNode |

