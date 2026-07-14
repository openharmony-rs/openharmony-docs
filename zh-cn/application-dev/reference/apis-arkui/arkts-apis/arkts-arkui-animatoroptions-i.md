# AnimatorOptions

定义动画选项。

**起始版本：** 6

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## begin

```TypeScript
begin: number
```

动画插值起点。

**说明:** 会影响[onFrame](../../../../reference/apis-arkui/js-apis-animator.md#属性)回调的入参值。

默认值：0

**类型：** number

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay: number
```

动画延时播放时长，单位毫秒，设置为0时，表示不延时。设置为负数时动画提前播放，如果提前播放的时长大于动画总时长，动画直接过渡到终点。

默认值：0

**类型：** number

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: "normal" | "reverse" | "alternate" | "alternate-reverse"
```

动画播放模式。

'normal'： 动画正向循环播放。

'reverse'： 动画反向循环播放。

'alternate'：动画交替循环播放，奇数次正向播放，偶数次反向播放。

'alternate-reverse'：动画反向交替循环播放，奇数次反向播放，偶数次正向播放。

默认值：'normal'

**类型：** "normal" | "reverse" | "alternate" | "alternate-reverse"

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration: number
```

动画播放的时长，单位毫秒。

取值范围：[0, +∞)

默认值：0

**类型：** number

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## easing

```TypeScript
easing: string
```

动画插值曲线，支持的曲线类型可参考表1。

非法字符串时取:"ease"。

**类型：** string

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end: number
```

动画插值终点。

**说明:** 会影响[onFrame](../../../../reference/apis-arkui/js-apis-animator.md#属性)回调的入参值。

默认值：1

**类型：** number

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill: "none" | "forwards" | "backwards" | "both"
```

动画执行后是否恢复到初始状态，动画执行后，动画结束时的状态（在最后一个关键帧中定义）将保留。

'none'：在动画执行之前和之后都不会应用任何样式到目标上。

'forwards'：在动画结束后，目标将保留动画结束时的状态（在最后一个关键帧中定义）。

'backwards'：动画将在[AnimatorOptions](arkts-arkui-animatoroptions-i.md)中的delay期间应用第一个关键帧中定义的值。当
[AnimatorOptions](arkts-arkui-animatoroptions-i.md)中的direction为'normal'或'alternate'时应用from关键帧中的值，当
[AnimatorOptions](arkts-arkui-animatoroptions-i.md)中的direction为'reverse'或'alternate-reverse'时应用to关键帧中的值。

'both'：动画将遵循forwards和backwards的规则，从而在两个方向上扩展动画属性。

**类型：** "none" | "forwards" | "backwards" | "both"

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations: number
```

动画播放次数。设置为0时不播放，设置为-1时无限次播放，设置大于0时为播放次数。

**说明:** 设置为除-1外其他负数视为无效取值，无效取值动画默认播放1次。

**类型：** number

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

