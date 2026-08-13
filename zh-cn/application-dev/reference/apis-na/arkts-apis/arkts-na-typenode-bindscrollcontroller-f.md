# bindScrollController

## bindScrollController

```TypeScript
export function bindScrollController(node: FrameNode, controller: Scroller): void
```

绑定FrameNode的控制器。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function bindScrollController(node: FrameNode, controller: Scroller): void--><!--Device-typeNode-export function bindScrollController(node: FrameNode, controller: Scroller): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-na-framenode-c.md) | 是 | 目标FrameNode。 |
| controller | Scroller | 是 | the controller which is bind to 目标FrameNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100023](../../apis-arkui/errorcode-node.md#100023-参数错误) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |

