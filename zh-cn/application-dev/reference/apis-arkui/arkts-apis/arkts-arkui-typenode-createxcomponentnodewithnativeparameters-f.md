# createXComponentNodeWithNativeParameters

## createXComponentNodeWithNativeParameters

```TypeScript
export function createXComponentNodeWithNativeParameters(
    context: UIContext, parameters: NativeXComponentParameters, options?: FrameNodeOptions): XComponent
```

创建 XComponent 类型的 FrameNode（支持原生开发参数）

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function createXComponentNodeWithNativeParameters(    context: UIContext, parameters: NativeXComponentParameters, options?: FrameNodeOptions): XComponent--><!--Device-typeNode-export function createXComponentNodeWithNativeParameters(    context: UIContext, parameters: NativeXComponentParameters, options?: FrameNodeOptions): XComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于创建 FrameNode 的 UI 上下文 |
| parameters | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 原生开发初始化参数 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Options for configuring FrameNode creation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 26.0.0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - 返回 XComponent 类型的 FrameNode |

