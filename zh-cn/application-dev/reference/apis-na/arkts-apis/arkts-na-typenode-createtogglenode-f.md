# createToggleNode

## createToggleNode

```TypeScript
export function createToggleNode(
    context: UIContext, options?: ToggleOptions, frameNodeOptions?: FrameNodeOptions): Toggle
```

创建 Toggle 类型的 FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function createToggleNode(    context: UIContext, options?: ToggleOptions, frameNodeOptions?: FrameNodeOptions): Toggle--><!--Device-typeNode-export function createToggleNode(    context: UIContext, options?: ToggleOptions, frameNodeOptions?: FrameNodeOptions): Toggle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | 用于创建 FrameNode 的 UI 上下文。 |
| options | ToggleOptions | 否 | Toggle 组件选项。 |
| frameNodeOptions | [FrameNodeOptions](arkts-na-framenode-framenodeoptions-i.md) | 否 | FrameNode创建配置选项。【since24】。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Toggle | Return Toggle type FrameNode. |

