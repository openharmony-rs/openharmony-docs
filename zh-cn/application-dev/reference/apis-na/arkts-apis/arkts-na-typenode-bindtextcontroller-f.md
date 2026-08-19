# bindTextController

## bindTextController

```TypeScript
export function bindTextController(node: FrameNode, controller: TextController): void
```

绑定Text节点的控制器。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-typeNode-export function bindTextController(node: FrameNode, controller: TextController): void--><!--Device-typeNode-export function bindTextController(node: FrameNode, controller: TextController): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | 目标节点。 |
| controller | TextController | 是 | the controller which is bind to 目标节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100023](../../apis-arkui/errorcode-node.md#100023-参数错误) | Parameter error. Possible causes: 1. The component type of the node is incorrect. 2. The node is null or undefined. 3. The controller is null or undefined. |

