# AxisEvent

轴事件的对象说明，继承于[BaseEvent](arkts-arkui-baseevent-i.md)。

**继承/实现关系：** AxisEvent extends [BaseEvent](arkts-arkui-baseevent-i.md)

**起始版本：** 17

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

获取点击位置相对于当前组件实时位置的左上角坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Coordinate2D | - 点击位置相对于当前组件实时位置的左上角坐标。 |

## getHorizontalAxisValue

```TypeScript
getHorizontalAxisValue(): number
```

获取此次轴事件的水平轴值。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 水平轴值。<br>单位：vp |

## getPinchAxisScaleValue

```TypeScript
getPinchAxisScaleValue(): number
```

返回此次轴事件双指缩放的比例。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 双指缩放比例。<br/> **说明：** 缩放比例指的是触控板双指缩放事件触发过程中双指当前的距离与双指最初按下时的距离的比值。<br/>默认值：0<br/>取值范围：[0, +∞)<br/> |

## getVerticalAxisValue

```TypeScript
getVerticalAxisValue(): number
```

获取此次轴事件的垂直轴值。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 垂直轴值。<br>单位：vp |

## hasAxis

```TypeScript
hasAxis(axisType: AxisType): boolean
```

检测此轴事件是否包含指定的轴类型。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| axisType | AxisType | 是 | 轴事件的轴类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 此轴事件是否包含指定的轴类型。<br>true：包含指定的轴类型；false：不包含指定的轴类型。 |

## action

```TypeScript
action: AxisAction
```

轴事件的动作类型。

**类型：** AxisAction

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: number
```

鼠标光标在当前应用屏幕坐标系中的X坐标。

单位：vp

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

鼠标光标在当前应用屏幕坐标系中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## eventHandleId

```TypeScript
eventHandleId?: number
```

用于事件处理的唯一标识。

取值范围：[0, +∞)

**说明：** 在使用[postInputEventWithStrategy](../arkts-apis/arkts-arkui-buildernode-c.md#postinputeventwithstrategy-1)接口分发事件时会使用该字段，事件每分
发一次字段会增加100000。

多次使用相同的eventHandleId进行事件分发将导致事件响应异常。仅在构造事件的时候需要对此字段赋值，其余情况开发者无需处理。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

鼠标光标在[全局坐标系](../../../../windowmanager/window-terminology.md#全局坐标系)中的X坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

鼠标光标或手写笔位置在[全局坐标系](../../../../windowmanager/window-terminology.md#全局坐标系)中的Y坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## propagation

```TypeScript
propagation: Callback<void>
```

激活[事件冒泡](../../../../ui/arkts-interaction-basic-principles.md#事件冒泡)。

**类型：** Callback<void>

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollStep

```TypeScript
scrollStep?: number
```

鼠标轴滚动步长配置。

**说明：** 仅支持鼠标滚轮，取值范围：[0~65535]

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

鼠标光标在当前应用窗口坐标系中的X坐标。

单位：vp

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

鼠标光标在当前应用窗口坐标系中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

鼠标光标在被点击元素为基准的[组件坐标系](../../../../ui/arkui-glossary.md#组件坐标系)中的X坐标。

单位：vp

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

鼠标光标在被点击元素为基准的[组件坐标系](../../../../ui/arkui-glossary.md#组件坐标系)中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

