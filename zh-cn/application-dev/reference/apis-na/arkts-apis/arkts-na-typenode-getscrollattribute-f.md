# getScrollAttribute

## getScrollAttribute

```TypeScript
export function getScrollAttribute(node: FrameNode): ScrollAttribute | undefined
```

获取FrameNode属性实例用于属性设置

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function getScrollAttribute(node: FrameNode): ScrollAttribute | undefined--><!--Device-typeNode-export function getScrollAttribute(node: FrameNode): ScrollAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-na-framenode-c.md) | 是 | 目标FrameNode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ScrollAttribute | Return the attribute instance of FrameNode, and return undefined if it does not exist. |

