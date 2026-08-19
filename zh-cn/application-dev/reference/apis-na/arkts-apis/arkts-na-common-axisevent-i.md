# AxisEvent

The axis event triggers this method invocation.

**继承/实现关系：** AxisEvent extends [BaseEvent](arkts-na-common-baseevent-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface AxisEvent--><!--Device-unnamed-export declare interface AxisEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition(): Coordinate2D
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-AxisEvent-getCurrentLocalPosition(): Coordinate2D--><!--Device-AxisEvent-getCurrentLocalPosition(): Coordinate2D-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Coordinate2D](../../apis-arkui/arkts-apis/arkts-arkui-coordinate2d-i.md) |  |

## getHorizontalAxisValue

```TypeScript
getHorizontalAxisValue(): double
```

Obtains the value of the horizontal scroll axis for this axis event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-getHorizontalAxisValue(): double--><!--Device-AxisEvent-getHorizontalAxisValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## getPinchAxisScaleValue

```TypeScript
getPinchAxisScaleValue(): double
```

Obtains the value of the pinch axis for this axis event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-getPinchAxisScaleValue(): double--><!--Device-AxisEvent-getPinchAxisScaleValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## getVerticalAxisValue

```TypeScript
getVerticalAxisValue(): double
```

Obtains the value of the vertical scroll axis for this axis event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-getVerticalAxisValue(): double--><!--Device-AxisEvent-getVerticalAxisValue(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## hasAxis

```TypeScript
hasAxis(axisType: AxisType): boolean
```

Checks whether this event contains a specified axis type.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-hasAxis(axisType: AxisType): boolean--><!--Device-AxisEvent-hasAxis(axisType: AxisType): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| axisType | [AxisType](../../apis-arkui/arkts-apis/arkts-arkui-axistype-e.md) | 是 | Indicates the axis type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean |  |

## propagation

```TypeScript
propagation(): void
```

Active event bubbling.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-propagation(): void--><!--Device-AxisEvent-propagation(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: AxisAction
```

Axis action of the axis event.

**类型：** [AxisAction](../../apis-arkui/arkts-apis/arkts-arkui-axisaction-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-action: AxisAction--><!--Device-AxisEvent-action: AxisAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## default

```TypeScript
default
```

Gets the coordinates of the top-left corner of the current component based on its real-time position.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-default--><!--Device-AxisEvent-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: double
```

X coordinate of the mouse cursor relative to the left edge of the device screen.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-displayX: double--><!--Device-AxisEvent-displayX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: double
```

Y coordinate of the mouse cursor relative to the upper edge of the device screen.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-displayY: double--><!--Device-AxisEvent-displayY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## eventHandleId

```TypeScript
eventHandleId?: int
```

The unique handle for the event processing session. This handle must be used for any further operations on the event. The system ensures that for a given finger, only one event with this handle can be active at a time.

**类型：** int

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-eventHandleId?: int--><!--Device-AxisEvent-eventHandleId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: double
```

X coordinate of the point relative to the global display.

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-globalDisplayX?: double--><!--Device-AxisEvent-globalDisplayX?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: double
```

Y coordinate of the point relative to the global display.

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-globalDisplayY?: double--><!--Device-AxisEvent-globalDisplayY?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollStep

```TypeScript
scrollStep?: int
```

Scroll step configuration which is only mouse wheel has. *

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-scrollStep?: int--><!--Device-AxisEvent-scrollStep?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: double
```

X coordinate of the mouse cursor relative to the left edge of the current window.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-windowX: double--><!--Device-AxisEvent-windowX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: double
```

Y coordinate of the mouse cursor relative to the upper edge of the current window.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-windowY: double--><!--Device-AxisEvent-windowY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: double
```

X coordinate of the mouse cursor relative to the left edge of the axis event hit element.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-x: double--><!--Device-AxisEvent-x: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: double
```

Y coordinate of the mouse cursor relative to the upper edge of the axis event hit element.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AxisEvent-y: double--><!--Device-AxisEvent-y: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

