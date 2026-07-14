# TextMarqueeOptions

Marquee初始化参数。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

设置每次滚动的时间间隔。

默认值：0

单位：毫秒

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fadeout

```TypeScript
fadeout?: boolean
```

设置文字超长时的渐隐效果。

true表示支持渐隐效果，false表示不支持渐隐效果。

当Text内容超出显示范围时，未完全展现的文字边缘将应用渐隐效果。若两端均有文字未完全显示，则两端同时应用渐隐效果。在渐隐效果开启状态下，clip属性将自动锁定为true，不允许设置为false。

默认值：false

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fromStart

```TypeScript
fromStart?: boolean
```

设置文本从头开始滚动或反向滚动。

true表示从头开始滚动，false表示反向滚动。

默认值：true

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: number
```

设置重复滚动的次数，小于等于零时无限循环。

默认值：-1

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marqueeStartPolicy

```TypeScript
marqueeStartPolicy?: MarqueeStartPolicy
```

设置跑马灯启动策略，该属性值生效需将start设置为true。

默认值：TV设备上默认值为MarqueeStartPolicy.ON_FOCUS，其他设备默认值为MarqueeStartPolicy.DEFAULT

**类型：** MarqueeStartPolicy

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marqueeUpdatePolicy

```TypeScript
marqueeUpdatePolicy?: MarqueeUpdatePolicy
```

跑马灯组件属性更新后，跑马灯的滚动策略。

当跑马灯为播放状态，且文本内容宽度超过跑马灯组件宽度时，该属性生效。

默认值：MarqueeUpdatePolicy.DEFAULT

**类型：** MarqueeUpdatePolicy

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spacing

```TypeScript
spacing?: LengthMetrics
```

两轮跑马灯之间的间距。如果LengthMetrics的unit值是PERCENT，当前设置不生效，按默认值处理。

默认值：48.0vp

**类型：** LengthMetrics

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: boolean
```

控制跑马灯进入播放状态。

true表示播放，false表示不播放。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

滚动动画文本滚动步长。

默认值：4.0vp

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

