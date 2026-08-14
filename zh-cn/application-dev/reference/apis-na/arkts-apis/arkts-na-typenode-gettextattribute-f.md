# getTextAttribute

## getTextAttribute

```TypeScript
export function getTextAttribute(node: FrameNode): TextAttribute | undefined
```

获取FrameNode的属性实例来设置属性。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function getTextAttribute(node: FrameNode): TextAttribute | undefined--><!--Device-typeNode-export function getTextAttribute(node: FrameNode): TextAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-na-framenode-c.md) | 是 | 目标FrameNode。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextAttribute | Return the attribute instance of FrameNode, and return undefined if it does not exist. |

