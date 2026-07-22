# TouchEvent

继承于[BaseEvent](arkts-arkui-baseevent-i.md)。在非事件注入场景下，changedTouches是按屏幕刷新率重采样的点，而touches是按器件刷新率上报的点，因此changedTouches与touches的数据可能不同。

**继承/实现关系：** TouchEvent extends [BaseEvent](arkts-arkui-baseevent-i.md)

**起始版本：** 7

<!--Device-unnamed-declare interface TouchEvent extends BaseEvent--><!--Device-unnamed-declare interface TouchEvent extends BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getHistoricalPoints

```TypeScript
getHistoricalPoints(): Array<HistoricalPoint>
```

获取当前帧的所有历史点。不同设备每帧的触摸事件频率不同，且该接口仅能在[TouchEvent](arkts-arkui-touchevent-i.md)中调用，用于获取触发[onTouch](arkts-arkui-commonmethod-c.md#ontouch)时当前帧历史点的相关信息。[onTouch](arkts-arkui-commonmethod-c.md#ontouch)一帧通常只会调用一次，如果当前帧收到的[TouchEvent](arkts-arkui-touchevent-i.md)数目大于1，会将该帧最后一个点通过[onTouch](arkts-arkui-commonmethod-c.md#ontouch)返回，其余点作为历史点。如果多指在同一帧上报事件，可能触发多次onTouch。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchEvent-getHistoricalPoints(): Array<HistoricalPoint>--><!--Device-TouchEvent-getHistoricalPoints(): Array<HistoricalPoint>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;HistoricalPoint&gt; | 由历史点组成的数组。 |

## changedTouches

```TypeScript
changedTouches: TouchObject[]
```

发生变化而产生事件的手指信息。在使用该属性时，需要校验是否为空。

**类型：** TouchObject[]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchEvent-changedTouches: TouchObject[]--><!--Device-TouchEvent-changedTouches: TouchObject[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## eventHandleId

```TypeScript
eventHandleId?: number
```

用于事件处理的唯一标识。

取值范围：[0, +∞)

**说明：** 在使用[postInputEventWithStrategy](../arkts-apis/arkts-arkui-buildernode-c.md#postinputeventwithstrategy)接口分发事件时会使用该字段，事件每分发一次字段会增加100000。

多次使用相同的eventHandleId进行事件分发将导致事件响应异常。仅在构造事件的时候需要对此字段赋值，其余情况开发者无需处理。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TouchEvent-eventHandleId?: number--><!--Device-TouchEvent-eventHandleId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## preventDefault

```TypeScript
preventDefault: () => void
```

阻止默认事件。

**说明：** 该接口仅支持部分组件使用，当前支持组件：[Hyperlink](arkts-arkui-hyperlink.md)，不支持的组件在使用时会抛出异常。暂不支持异步调用和提供Modifier接口。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TouchEvent-preventDefault: () => void--><!--Device-TouchEvent-preventDefault: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation: () => void
```

阻塞[事件冒泡](../../../ui/arkts-interaction-basic-principles.md#事件冒泡)。

**类型：** () =&gt; void

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchEvent-stopPropagation: () => void--><!--Device-TouchEvent-stopPropagation: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## touches

```TypeScript
touches: TouchObject[]
```

全部屏幕触点（多指）的信息，每个元素代表一个触点。在使用该属性时，需要校验是否为空。

**类型：** TouchObject[]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchEvent-touches: TouchObject[]--><!--Device-TouchEvent-touches: TouchObject[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TouchType
```

触摸事件的类型。

**类型：** TouchType

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchEvent-type: TouchType--><!--Device-TouchEvent-type: TouchType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

