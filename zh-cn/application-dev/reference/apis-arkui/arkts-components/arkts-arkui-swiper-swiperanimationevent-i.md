# SwiperAnimationEvent

Swiper组件动画相关信息集合。

**起始版本：** 10

<!--Device-unnamed-declare interface SwiperAnimationEvent--><!--Device-unnamed-declare interface SwiperAnimationEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentOffset

```TypeScript
currentOffset: number
```

Swiper当前显示元素在主轴方向上，相对于Swiper起始位置的位移。单位VP，默认值为0。

**类型：** number

**默认值：** 0.0 vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAnimationEvent-currentOffset: number--><!--Device-SwiperAnimationEvent-currentOffset: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetOffset

```TypeScript
targetOffset: number
```

Swiper动画目标元素在主轴方向上，相对于Swiper起始位置的位移。单位VP，默认值为0。

**类型：** number

**默认值：** 0.0 vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAnimationEvent-targetOffset: number--><!--Device-SwiperAnimationEvent-targetOffset: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: number
```

Swiper离手动画开始时的离手速度。单位VP/S，默认值为0。

**类型：** number

**默认值：** 0.0 vp/s

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAnimationEvent-velocity: number--><!--Device-SwiperAnimationEvent-velocity: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

