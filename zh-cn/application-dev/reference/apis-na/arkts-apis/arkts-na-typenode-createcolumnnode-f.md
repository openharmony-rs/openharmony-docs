# createColumnNode

## createColumnNode

```TypeScript
export function createColumnNode(context: UIContext, options?: FrameNodeOptions): Column
```

创建Column类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function createColumnNode(context: UIContext, options?: FrameNodeOptions): Column--><!--Device-typeNode-export function createColumnNode(context: UIContext, options?: FrameNodeOptions): Column-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 用于创建FrameNode的UI上下文。 |
| options | [FrameNodeOptions](arkts-na-framenode-framenodeoptions-i.md) | 否 | Options for configuring FrameNode creation.<br>**起始版本：** 24 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Column | 返回Column类型的FrameNode。 |

