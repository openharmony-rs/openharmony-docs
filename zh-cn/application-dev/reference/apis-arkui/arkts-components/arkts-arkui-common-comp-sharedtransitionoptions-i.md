# sharedTransitionOptions

```TypeScript
declare interface sharedTransitionOptions
```

共享元素转场动效参数。

> **说明：** 
> 
> type为SharedTransitionEffectType.Exchange时motionPath才会生效。
> 
> type为SharedTransitionEffectType.Exchange时，效果为对匹配的共享元素产生位置、大小的过渡（可通过配置组件的border观察），不支持组件绘制内容的过渡效果（可通过为共享元素组件配置border
> 属性来观察位置和大小变化的过渡范围）。例如，Text组件在两个页面上使用不同的fontSize属性值，即绘制内容有大小差异，在sharedTransition动画结束后的最后一帧，Text的fontSize效果会突变为跳转目标页
> fontSize的效果。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

动画曲线。

推荐以Curve或ICurve形式指定。

当类型为string时，为动画插值曲线，取值参考[AnimateParam](arkts-arkui-common-comp-animateparam-i.md)的curve参数。

默认值：Curve.Linear

**类型：** Curve &#124; string &#124; [ICurve](arkts-arkui-common-comp-icurve-i.md)

**默认值：** Curve.Linear

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

延迟播放时间。

取值范围：[0, +∞)

默认值：0

单位：毫秒

**类型：** number

**默认值：** 0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

描述共享元素转场动效播放时长。

默认值：1000

单位：毫秒

取值范围：[0, +∞)

**类型：** number

**默认值：** 1000

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## motionPath

```TypeScript
motionPath?: MotionPathOptions
```

运动路径信息，用于定义共享元素转场时的运动轨迹。不设置时不启用运动路径效果。仅在type为SharedTransitionEffectType.Exchange时生效。

**类型：** [MotionPathOptions](arkts-arkui-common-comp-motionpathoptions-i.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: SharedTransitionEffectType
```

动画类型，决定共享元素转场时的过渡方式。Exchange类型产生位置、大小的过渡动画（不支持内容过渡效果），其他类型详见[SharedTransitionEffectType](../arkts-apis/arkts-arkui-sharedtransitioneffecttype-e.md)。

默认值：SharedTransitionEffectType.Exchange

**类型：** [SharedTransitionEffectType](../arkts-apis/arkts-arkui-sharedtransitioneffecttype-e.md)

**默认值：** SharedTransitionEffectType.Exchange

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## zIndex

```TypeScript
zIndex?: number
```

设置共享元素在转场动画期间的Z轴堆叠顺序。

取值范围：(-∞, +∞)

默认值：0

数值越大，该共享元素在转场过程中越靠前（显示在上层），越不容易被其他共享元素遮挡。此zIndex仅在共享元素转场动画期间生效，控制共享元素相对于其他同时参与转场的共享元素在Z轴上的堆叠顺序，不参与页面内普通组件的静态布局层级控制（页面内组件的静态布局层级由组件通用属性[zIndex](arkts-arkui-common-comp-commonmethod-c.md#zindex)控制）。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
