# MouseEvent

The mouse click action triggers this method invocation.

**继承/实现关系：** MouseEvent extends [BaseEvent](arkts-na-common-baseevent-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface MouseEvent--><!--Device-unnamed-export declare interface MouseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition(): Coordinate2D
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MouseEvent-getCurrentLocalPosition(): Coordinate2D--><!--Device-MouseEvent-getCurrentLocalPosition(): Coordinate2D-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Coordinate2D](../../apis-arkui/arkts-apis/arkts-arkui-coordinate2d-i.md) |  |

## getHistoricalPoints

```TypeScript
getHistoricalPoints(): MouseHistoricalPoint[] | undefined
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-MouseEvent-getHistoricalPoints(): MouseHistoricalPoint[] | undefined--><!--Device-MouseEvent-getHistoricalPoints(): MouseHistoricalPoint[] | undefined-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MouseHistoricalPoint](arkts-na-common-mousehistoricalpoint-i.md)[] |  |

## stopPropagation

```TypeScript
stopPropagation(): void
```

Stops the event from bubbling upwards or downwards.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-stopPropagation(): void--><!--Device-MouseEvent-stopPropagation(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: MouseAction
```

Mouse action of the click event.

**类型：** [MouseAction](../../apis-arkui/arkts-apis/arkts-arkui-mouseaction-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-action: MouseAction--><!--Device-MouseEvent-action: MouseAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## button

```TypeScript
button: MouseButton
```

Mouse button of the click event.

**类型：** [MouseButton](../../apis-arkui/arkts-apis/arkts-arkui-mousebutton-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-button: MouseButton--><!--Device-MouseEvent-button: MouseButton-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## default

```TypeScript
default
```

Obtains all historical points of the current frame.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-default--><!--Device-MouseEvent-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: double
```

X coordinate of the mouse pointer relative to the upper left corner of the application screen.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-displayX: double--><!--Device-MouseEvent-displayX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: double
```

Y coordinate of the mouse pointer relative to the upper left corner of the application screen.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-displayY: double--><!--Device-MouseEvent-displayY: double-End-->

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

<!--Device-MouseEvent-eventHandleId?: int--><!--Device-MouseEvent-eventHandleId?: int-End-->

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

<!--Device-MouseEvent-globalDisplayX?: double--><!--Device-MouseEvent-globalDisplayX?: double-End-->

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

<!--Device-MouseEvent-globalDisplayY?: double--><!--Device-MouseEvent-globalDisplayY?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pressedButtons

```TypeScript
pressedButtons?: MouseButton[]
```

Array of all mouse buttons that are currently pressed.

**类型：** [MouseButton](../../apis-arkui/arkts-apis/arkts-arkui-mousebutton-e.md)[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-pressedButtons?: MouseButton[]--><!--Device-MouseEvent-pressedButtons?: MouseButton[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rawDeltaX

```TypeScript
rawDeltaX?: double
```

X axis offset relative to the previous reported mouse pointer position. When the mouse pointer is at the edge of the screen, the value may be less than the difference of the X coordinate reported twice.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-rawDeltaX?: double--><!--Device-MouseEvent-rawDeltaX?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rawDeltaY

```TypeScript
rawDeltaY?: double
```

Y axis offset relative to the previous reported mouse pointer position. When the mouse pointer is at the edge of the screen, the value may be less than the difference of the Y coordinate reported twice.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-rawDeltaY?: double--><!--Device-MouseEvent-rawDeltaY?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: double
```

X coordinate of the mouse pointer relative to the upper left corner of the application window.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-windowX: double--><!--Device-MouseEvent-windowX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: double
```

Y coordinate of the mouse pointer relative to the upper left corner of the application window.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-windowY: double--><!--Device-MouseEvent-windowY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: double
```

X coordinate of the mouse pointer relative to the upper left corner of the component being clicked.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-x: double--><!--Device-MouseEvent-x: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: double
```

Y coordinate of the mouse pointer relative to the upper left corner of the component being clicked.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseEvent-y: double--><!--Device-MouseEvent-y: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

