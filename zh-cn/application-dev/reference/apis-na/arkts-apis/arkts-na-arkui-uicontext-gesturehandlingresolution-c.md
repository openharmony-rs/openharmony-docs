# GestureHandlingResolution

类手势处理解决方案。表示开发者对智能手势处理的决策结果。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class GestureHandlingResolution--><!--Device-unnamed-export declare class GestureHandlingResolution-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(isConsumed: boolean)
```

GestureHandlingResolution构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureHandlingResolution-constructor(isConsumed: boolean)--><!--Device-GestureHandlingResolution-constructor(isConsumed: boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isConsumed | boolean | 是 | 是否消费当前手势事件。 |

## isConsumed

```TypeScript
isConsumed: boolean
```

判断是否消费当前手势事件。如果手势没有被消费，它会告诉消费者该手势不被支持。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureHandlingResolution-isConsumed: boolean--><!--Device-GestureHandlingResolution-isConsumed: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedProposal

```TypeScript
selectedProposal?: BaseGestureHandlingProposal
```

开发者最终选择的手势处理方案。

**类型：** [BaseGestureHandlingProposal](arkts-na-arkui-uicontext-basegesturehandlingproposal-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureHandlingResolution-selectedProposal?: BaseGestureHandlingProposal--><!--Device-GestureHandlingResolution-selectedProposal?: BaseGestureHandlingProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

