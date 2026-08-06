# SwiperContentTransitionProxy

The proxy of SwiperContentAnimatedTransition.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SwiperContentTransitionProxy--><!--Device-unnamed-export declare interface SwiperContentTransitionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## finishTransition

```TypeScript
finishTransition(): void
```

通知Swiper组件，此页面的自定义动画已结束。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentTransitionProxy-finishTransition(): void--><!--Device-SwiperContentTransitionProxy-finishTransition(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: int
```

视窗内页面的索引。 取值范围为全体整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentTransitionProxy-index: int--><!--Device-SwiperContentTransitionProxy-index: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mainAxisLength

```TypeScript
mainAxisLength: double
```

index对应页面在主轴方向上的长度。 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentTransitionProxy-mainAxisLength: double--><!--Device-SwiperContentTransitionProxy-mainAxisLength: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position: double
```

index页面相对于Swiper主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentTransitionProxy-position: double--><!--Device-SwiperContentTransitionProxy-position: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex: int
```

当前选中页面的索引。 取值范围为全体整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentTransitionProxy-selectedIndex: int--><!--Device-SwiperContentTransitionProxy-selectedIndex: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

