# BaseEvent

基础事件类型。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getModifierKeyState

```TypeScript
getModifierKeyState?(keys: Array<string>): boolean
```

获取功能键按压状态。报错信息请参考以下错误码。支持功能键'Ctrl'\|'Alt'\|'Shift'。

> **说明：**
>
> 此接口不支持在手写笔场景下使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | 是 | 功能键列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回功能键按压状态。当功能键均处于按压状态时返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameterverification failed. |

## axisHorizontal

```TypeScript
axisHorizontal ?: number
```

水平轴值。

默认值：0

**说明：**

当前仅在鼠标滚轮或触控板双指滑动触发的Pan手势，或使用Ctrl+鼠标滚轮触发的Pinch手势中可以获取。

对于Shift+鼠标滚轮触发的横向滚动场景，axisHorizontal为0，滚动值体现在axisVertical中。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## axisPinch

```TypeScript
axisPinch?: number
```

双指缩放比例。

默认值：0

**说明：**

仅在触控板上通过双指缩放操作触发的Pinch手势，或在轴事件中，可以获取该值；在其他场景下，获取到的将是默认值。

缩放比例是指在双指缩放事件触发过程中，双指当前距离与最初按下时距离的比值。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## axisVertical

```TypeScript
axisVertical ?: number
```

垂直轴值。

默认值：0

**说明：**

当前仅在鼠标滚轮或触控板双指滑动触发的Pan手势，或使用Ctrl+鼠标滚轮触发的Pinch手势中可以获取。

对于Shift+鼠标滚轮触发的横向滚动场景，滚动值体现在axisVertical中。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deviceId

```TypeScript
deviceId?: number
```

触发当前事件的输入设备ID。

默认值：0

取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pressure

```TypeScript
pressure: number
```

按压的压力大小。

默认值：0

取值范围：[0,1]，典型值0.913168，压感大小与数值正相关。在部分设备中，由于设备的硬件参数配置不同，可能会返回大于1的值。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rollAngle

```TypeScript
rollAngle?: number
```

手写笔与设备平面的夹角。

单位：deg

**类型：** number

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本17开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本17开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## source

```TypeScript
source: SourceType
```

事件输入设备的类型。

**类型：** SourceType

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sourceTool

```TypeScript
sourceTool: SourceTool
```

事件输入源的类型。

**类型：** SourceTool

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## target

```TypeScript
target: EventTarget
```

触发手势事件的元素对象。

**类型：** EventTarget

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetDisplayId

```TypeScript
targetDisplayId?: number
```

事件发生的屏幕ID。

默认值：0

取值范围：[0, +∞)

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tiltX

```TypeScript
tiltX: number
```

手写笔在设备平面上的投影与设备平面X轴的夹角。

单位：deg

默认值：0

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tiltY

```TypeScript
tiltY: number
```

手写笔在设备平面上的投影与设备平面Y轴的夹角。

单位：deg

默认值：0

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

事件时间戳，触发事件时距离系统启动的时间间隔。

单位：ns

**类型：** number

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

