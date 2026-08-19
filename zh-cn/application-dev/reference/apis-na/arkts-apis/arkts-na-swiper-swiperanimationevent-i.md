# SwiperAnimationEvent

Provides an interface for swiper animation.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SwiperAnimationEvent--><!--Device-unnamed-export declare interface SwiperAnimationEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentOffset

```TypeScript
currentOffset: double
```

Swiper当前显示元素在主轴方向上，相对于Swiper起始位置的位移。 单位为： vp。

**类型：** double

**默认值：** 0.0 vp

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAnimationEvent-currentOffset: double--><!--Device-SwiperAnimationEvent-currentOffset: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetOffset

```TypeScript
targetOffset: double
```

Swiper动画目标元素在主轴方向上，相对于Swiper起始位置的位移。 单位为： vp。

**类型：** double

**默认值：** 0.0 vp

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAnimationEvent-targetOffset: double--><!--Device-SwiperAnimationEvent-targetOffset: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: double
```

Swiper离手动画开始时的离手速度。 单位为： vp。

**类型：** double

**默认值：** 0.0 vp/s

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAnimationEvent-velocity: double--><!--Device-SwiperAnimationEvent-velocity: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

