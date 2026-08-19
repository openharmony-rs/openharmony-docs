# GestureSwipeHandler

```TypeScript
export type GestureSwipeHandler = (index: int, event: SwiperAnimationEvent) => void
```

在页面跟手滑动过程中，逐帧触发的回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type GestureSwipeHandler = (index: int, event: SwiperAnimationEvent) => void--><!--Device-unnamed-export type GestureSwipeHandler = (index: int, event: SwiperAnimationEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 当前显示元素的索引。 |
| event | SwiperAnimationEvent | 是 | 动画相关信息，只返回主轴方向上当前显示元素相对于ArcSwiper起始位置的位移。 |

