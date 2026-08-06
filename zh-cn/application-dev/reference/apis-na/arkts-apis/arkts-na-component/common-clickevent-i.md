# ClickEvent

The tap action triggers this method invocation.

**继承/实现关系：** ClickEvent extends [BaseEvent](common-baseevent-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ClickEvent extends BaseEvent--><!--Device-unnamed-export declare interface ClickEvent extends BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
default getCurrentLocalPosition(): Coordinate2D
```

Gets the coordinates of the top-left corner of the current component based on its real-time position.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-default getCurrentLocalPosition(): Coordinate2D--><!--Device-ClickEvent-default getCurrentLocalPosition(): Coordinate2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - return the coordinates of the top-left corner of the current component based on its |

## preventDefault

```TypeScript
preventDefault(): void
```

Prevent the default function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-preventDefault(): void--><!--Device-ClickEvent-preventDefault(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100017](../../../apis-arkui/errorcode-event.md#100017-组件不支持阻止默认事件) | Component does not support prevent function. |

## displayX

```TypeScript
displayX: double
```

X coordinate of the click relative to the upper left corner of the application screen.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-displayX: double--><!--Device-ClickEvent-displayX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: double
```

Y coordinate of the click relative to the upper left corner of the application screen.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-displayY: double--><!--Device-ClickEvent-displayY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: double
```

X coordinate of the point relative to the global display.

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-globalDisplayX?: double--><!--Device-ClickEvent-globalDisplayX?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: double
```

Y coordinate of the point relative to the global display.

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-globalDisplayY?: double--><!--Device-ClickEvent-globalDisplayY?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hand

```TypeScript
hand?: InteractionHand
```

Whether the event is triggered by a left-hand or right-hand tap.

**类型：** InteractionHand

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-hand?: InteractionHand--><!--Device-ClickEvent-hand?: InteractionHand-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: double
```

X coordinate of the click relative to the upper left corner of the application window.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-windowX: double--><!--Device-ClickEvent-windowX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: double
```

Y coordinate of the click relative to the upper left corner of the application window.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-windowY: double--><!--Device-ClickEvent-windowY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: double
```

X coordinate of the click point relative to the left edge of the clicked element.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-x: double--><!--Device-ClickEvent-x: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: double
```

Y coordinate of the click point relative to the left edge of the clicked element.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-y: double--><!--Device-ClickEvent-y: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

