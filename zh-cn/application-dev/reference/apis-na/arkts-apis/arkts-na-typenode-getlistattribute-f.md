# getListAttribute

## getListAttribute

```TypeScript
export function getListAttribute(node: FrameNode): ListAttribute | undefined
```

获取属性实例用于设置属性

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function getListAttribute(node: FrameNode): ListAttribute | undefined--><!--Device-typeNode-export function getListAttribute(node: FrameNode): ListAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | 目标FrameNode |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ListAttribute | Return the attribute instance of FrameNode, and return undefined if it does not exist. |

