# TouchEvent

Touch Action Function Parameters

**继承/实现关系：** TouchEvent extends [BaseEvent](arkts-na-common-baseevent-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TouchEvent--><!--Device-unnamed-export declare interface TouchEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getHistoricalPoints

```TypeScript
getHistoricalPoints(): Array<HistoricalPoint> | undefined
```

Obtains all historical points of the current frame.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchEvent-getHistoricalPoints(): Array<HistoricalPoint> | undefined--><!--Device-TouchEvent-getHistoricalPoints(): Array<HistoricalPoint> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[HistoricalPoint](arkts-na-common-historicalpoint-i.md)&gt; | return all historical points. Undefined will be returned if the internal runtime environment is broken. |

## preventDefault

```TypeScript
preventDefault(): void
```

Blocks the default event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchEvent-preventDefault(): void--><!--Device-TouchEvent-preventDefault(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100017](../../apis-arkui/errorcode-event.md#100017-组件不支持阻止默认事件) | Component does not support prevent function. |

## stopPropagation

```TypeScript
stopPropagation(): void
```

Stops the event from bubbling upwards or downwards.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchEvent-stopPropagation(): void--><!--Device-TouchEvent-stopPropagation(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## changedTouches

```TypeScript
changedTouches: TouchObject[]
```

Finger information changed.

**类型：** [TouchObject](arkts-na-common-touchobject-i.md)[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchEvent-changedTouches: TouchObject[]--><!--Device-TouchEvent-changedTouches: TouchObject[]-End-->

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

<!--Device-TouchEvent-eventHandleId?: int--><!--Device-TouchEvent-eventHandleId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## touches

```TypeScript
touches: TouchObject[]
```

All finger information.

**类型：** [TouchObject](arkts-na-common-touchobject-i.md)[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchEvent-touches: TouchObject[]--><!--Device-TouchEvent-touches: TouchObject[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TouchType
```

Type of the touch event.

**类型：** [TouchType](../../apis-arkui/arkts-apis/arkts-arkui-touchtype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchEvent-type: TouchType--><!--Device-TouchEvent-type: TouchType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

