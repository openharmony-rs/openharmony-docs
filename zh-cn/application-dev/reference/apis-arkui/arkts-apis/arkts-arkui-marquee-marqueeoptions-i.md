# MarqueeOptions

Marquee初始化参数。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface MarqueeOptions--><!--Device-unnamed-export interface MarqueeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: int
```

设置每次滚动的时间间隔。 默认值：0 取值范围：[0, +∞)，设置的值小于0时等价于设置0。 单位：毫秒

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MarqueeOptions-delay?: int--><!--Device-MarqueeOptions-delay?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fromStart

```TypeScript
fromStart?: boolean
```

设置文本从头开始滚动或反向滚动。 true：表示从头开始滚动 false：表示反向滚动。 默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MarqueeOptions-fromStart?: boolean--><!--Device-MarqueeOptions-fromStart?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: int
```

设置重复滚动的次数，小于等于零时无限循环。 默认值：-1 **说明：** ArkTS卡片上该参数设置任意值都仅在可见时滚动一次。

**类型：** int

**默认值：** -1

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MarqueeOptions-loop?: int--><!--Device-MarqueeOptions-loop?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spacing

```TypeScript
spacing?: LengthMetrics
```

两轮跑马灯之间的间距。如果LengthMetrics的unit值是PERCENT，当前设置不生效，按默认值处理。 默认值：跑马灯组件宽度。

**类型：** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MarqueeOptions-spacing?: LengthMetrics--><!--Device-MarqueeOptions-spacing?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: string | undefined
```

需要滚动的文本。 默认值：'' 取值为undefined时，按默认值处理。

**类型：** string \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MarqueeOptions-src: string | undefined--><!--Device-MarqueeOptions-src: string | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: boolean | undefined
```

控制跑马灯是否进入播放状态。 true：播放；false：不播放。 默认值：false 取值为undefined时，按默认值处理。 **说明：** 有限的滚动次数播放完毕后，不可以通过改变start重置滚动次数重新开始播放。

**类型：** boolean \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MarqueeOptions-start: boolean | undefined--><!--Device-MarqueeOptions-start: boolean | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: double
```

滚动动画的文本步长。当step大于Marquee的文本宽度时，取默认值。 默认值：6 单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** double

**默认值：** 6

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MarqueeOptions-step?: double--><!--Device-MarqueeOptions-step?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

