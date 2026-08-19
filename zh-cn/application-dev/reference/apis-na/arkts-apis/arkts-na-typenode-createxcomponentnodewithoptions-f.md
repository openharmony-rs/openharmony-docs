# createXComponentNodeWithOptions

## createXComponentNodeWithOptions

```TypeScript
export function createXComponentNodeWithOptions(
    context: UIContext, value: XComponentOptions, options?: FrameNodeOptions): XComponent
```

创建 XComponent 类型的 FrameNode（支持 XComponent 组件选项）

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function createXComponentNodeWithOptions(    context: UIContext, value: XComponentOptions, options?: FrameNodeOptions): XComponent--><!--Device-typeNode-export function createXComponentNodeWithOptions(    context: UIContext, value: XComponentOptions, options?: FrameNodeOptions): XComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | 用于创建 FrameNode 的 UI 上下文 |
| value | XComponentOptions | 是 | XComponent 组件选项 |
| options | [FrameNodeOptions](arkts-na-framenode-framenodeoptions-i.md) | 否 | Options for configuring FrameNode creation.<br>**起始版本：** 24 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| XComponent | Return XComponent type FrameNode. |

