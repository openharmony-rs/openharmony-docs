# OnSwiperGestureSwipeCallback

```TypeScript
declare type OnSwiperGestureSwipeCallback = (index: number, extraInfo: SwiperAnimationEvent) => void
```

在页面跟手滑动过程中，逐帧触发的回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnSwiperGestureSwipeCallback = (index: number, extraInfo: SwiperAnimationEvent) => void--><!--Device-unnamed-declare type OnSwiperGestureSwipeCallback = (index: number, extraInfo: SwiperAnimationEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 当前显示元素的索引。多列Swiper时，index为最左侧组件的索引。  |
| extraInfo | [SwiperAnimationEvent](arkts-arkui-swiperanimationevent-i.md) | 是 | 动画相关信息，只返回主轴方向上当前显示元素相对于Swiper起始位置的位移。  |

