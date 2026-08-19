# getFlexAttribute

## getFlexAttribute

```TypeScript
export function getFlexAttribute(node: FrameNode): FlexAttribute | undefined
```

Get the attribute instance of FrameNode to set attributes.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function getFlexAttribute(node: FrameNode): FlexAttribute | undefined--><!--Device-typeNode-export function getFlexAttribute(node: FrameNode): FlexAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | the target FrameNode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FlexAttribute | Return the attribute instance of FrameNode, and return undefined if it does not exist. |

