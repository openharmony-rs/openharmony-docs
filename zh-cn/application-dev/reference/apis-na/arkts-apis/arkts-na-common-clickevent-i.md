# ClickEvent

The tap action triggers this method invocation.

**继承/实现关系：** ClickEvent extends [BaseEvent](arkts-na-common-baseevent-i.md#BaseEvent)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ClickEvent--><!--Device-unnamed-export declare interface ClickEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition(): Coordinate2D
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ClickEvent-getCurrentLocalPosition(): Coordinate2D--><!--Device-ClickEvent-getCurrentLocalPosition(): Coordinate2D-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Coordinate2D](../../apis-arkui/arkts-apis/arkts-arkui-coordinate2d-i.md) |  |

## preventDefault

```TypeScript
preventDefault(): void
```

Prevent the default function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-preventDefault(): void--><!--Device-ClickEvent-preventDefault(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100017](../../apis-arkui/errorcode-event.md#100017-组件不支持阻止默认事件) | Component does not support prevent function. |

## default

```TypeScript
default
```

Gets the coordinates of the top-left corner of the current component based on its real-time position.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-default--><!--Device-ClickEvent-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: double
```

X coordinate of the click relative to the upper left corner of the application screen.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

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

**废弃版本：** -1

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

**废弃版本：** -1

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

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-globalDisplayY?: double--><!--Device-ClickEvent-globalDisplayY?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hand

```TypeScript
hand?: InteractionHand
```

Whether the event is triggered by a left-hand or right-hand tap.

**类型：** [InteractionHand](../../apis-arkui/arkts-apis/arkts-arkui-interactionhand-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

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

**废弃版本：** -1

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

**废弃版本：** -1

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

**废弃版本：** -1

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

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClickEvent-y: double--><!--Device-ClickEvent-y: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

