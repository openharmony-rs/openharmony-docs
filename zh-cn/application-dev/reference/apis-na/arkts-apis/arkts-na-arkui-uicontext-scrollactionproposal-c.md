# ScrollActionProposal

类ScrollActionProposal。默认滚动方向为向前。

**继承/实现关系：** ScrollActionProposal extends [TargetedGestureProposal](arkts-na-arkui-uicontext-targetedgestureproposal-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class ScrollActionProposal--><!--Device-unnamed-export declare class ScrollActionProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(node: FrameNode, distance: double)
```

ScrollActionProposal构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollActionProposal-constructor(node: FrameNode, distance: double)--><!--Device-ScrollActionProposal-constructor(node: FrameNode, distance: double)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 响应滚动动作的节点。 |
| distance | double | 是 | 滚动或滑动的距离。 |

## distance

```TypeScript
distance: double
```

手势操作的距离参数。用于滚动或滑动等动作，以指定移动距离。

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollActionProposal-distance: double--><!--Device-ScrollActionProposal-distance: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

