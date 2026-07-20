# ClickEvent

继承于[BaseEvent](arkts-arkui-baseevent-i.md)。

**继承/实现关系：** ClickEvent extends [BaseEvent](arkts-arkui-baseevent-i.md)

**起始版本：** 7

<!--Device-unnamed-declare interface ClickEvent extends BaseEvent--><!--Device-unnamed-declare interface ClickEvent extends BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="getcurrentlocalposition"></a>
## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

获取点击位置相对于当前组件实时位置的左上角坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-getCurrentLocalPosition?(): Coordinate2D--><!--Device-ClickEvent-getCurrentLocalPosition?(): Coordinate2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Coordinate2D](../arkts-apis/arkts-arkui-coordinate2d-i.md) | - 点击位置相对于当前组件实时位置的左上角坐标。 |

## displayX

```TypeScript
displayX: number
```

点击位置在当前应用屏幕坐标系中的X坐标。

单位：vp

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-displayX: number--><!--Device-ClickEvent-displayX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

点击位置在当前应用屏幕坐标系中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-displayY: number--><!--Device-ClickEvent-displayY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

点击位置在[全局坐标系](docroot://windowmanager/window-terminology.md#全局坐标系)中的X坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-globalDisplayX?: number--><!--Device-ClickEvent-globalDisplayX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

触摸点在[全局坐标系](docroot://windowmanager/window-terminology.md#全局坐标系)中的Y坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-globalDisplayY?: number--><!--Device-ClickEvent-globalDisplayY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hand

```TypeScript
hand?: InteractionHand
```

表示事件是由左手点击还是右手点击触发。

**类型：** InteractionHand

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-hand?: InteractionHand--><!--Device-ClickEvent-hand?: InteractionHand-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## preventDefault

```TypeScript
preventDefault: () => void
```

阻止默认事件。

**说明：** 该接口仅支持部分组件使用，当前支持组件：RichEditor、Hyperlink，不支持的组件使用时会抛出异常。暂不支持异步调用和提供Modifier接口。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-preventDefault: () => void--><!--Device-ClickEvent-preventDefault: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## screenX

```TypeScript
screenX: number
```

点击位置在当前应用窗口坐标系中的X坐标。

单位：vp

**类型：** number

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [windowX](arkts-arkui-clickevent-i.md#windowx)

<!--Device-ClickEvent-screenX: number--><!--Device-ClickEvent-screenX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## screenY

```TypeScript
screenY: number
```

点击位置在当前应用窗口坐标系中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [windowY](arkts-arkui-clickevent-i.md#windowy)

<!--Device-ClickEvent-screenY: number--><!--Device-ClickEvent-screenY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

点击位置在当前应用窗口坐标系中的X坐标。onClick的distanceThreshold设置后，点击位置为抬手点。

单位：vp

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-windowX: number--><!--Device-ClickEvent-windowX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

点击位置在当前应用窗口坐标系中的Y坐标。onClick的distanceThreshold设置后，点击位置为抬手点。

单位：vp

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ClickEvent-windowY: number--><!--Device-ClickEvent-windowY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

点击位置在被点击元素为基准的[组件坐标系](docroot://ui/arkui-glossary.md#组件坐标系)中的X坐标。onClick的[distanceThreshold](arkts-arkui-commonmethod-c.md#onclick-1)设置后，点击位置为抬手点。触发事件的是键盘或手柄时，点击位置为被点击元素的中心点。

单位：vp

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ClickEvent-x: number--><!--Device-ClickEvent-x: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

点击位置在被点击元素为基准的[组件坐标系](docroot://ui/arkui-glossary.md#组件坐标系)中的Y坐标。onClick的distanceThreshold设置后，点击位置为抬手点。触发事件的是键盘或手柄时，点击位置为被点击元素的中心点。

单位：vp

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ClickEvent-y: number--><!--Device-ClickEvent-y: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

