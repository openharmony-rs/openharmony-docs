# PageSwitchActionProposal

类PageSwitchActionProposal。默认的页面切换方向为前进。

**继承/实现关系：** PageSwitchActionProposal extends [TargetedGestureProposal](arkts-arkui-arkui-uicontext-targetedgestureproposal-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class PageSwitchActionProposal extends TargetedGestureProposal--><!--Device-unnamed-export declare class PageSwitchActionProposal extends TargetedGestureProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(node: FrameNode, pageCount: int)
```

PageSwitchActionProposal构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageSwitchActionProposal-constructor(node: FrameNode, pageCount: int)--><!--Device-PageSwitchActionProposal-constructor(node: FrameNode, pageCount: int)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 响应页面切换动作的节点。 |
| pageCount | int | 是 | 要切换的页数。取值限定为整数。 |

## pageCount

```TypeScript
pageCount: int
```

手势操作的页数参数。指定要导航的页数。 取值限定为整数。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageSwitchActionProposal-pageCount: int--><!--Device-PageSwitchActionProposal-pageCount: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

