# getToggleAttribute

## getToggleAttribute

```TypeScript
export function getToggleAttribute(node: FrameNode): ToggleAttribute | undefined
```

获取FrameNode的属性实例以设置属性。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function getToggleAttribute(node: FrameNode): ToggleAttribute | undefined--><!--Device-typeNode-export function getToggleAttribute(node: FrameNode): ToggleAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | 目标FrameNode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ToggleAttribute | Return the attribute instance of FrameNode, and return undefined if it does not exist. |

