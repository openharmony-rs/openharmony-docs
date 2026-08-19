# getButtonAttribute

## getButtonAttribute

```TypeScript
export function getButtonAttribute(node: FrameNode): ButtonAttribute | undefined
```

获取FrameNode的属性实例以设置属性。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function getButtonAttribute(node: FrameNode): ButtonAttribute | undefined--><!--Device-typeNode-export function getButtonAttribute(node: FrameNode): ButtonAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | 目标FrameNode |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ButtonAttribute | Return the attribute instance of FrameNode, and return undefined if it does not exist. |

