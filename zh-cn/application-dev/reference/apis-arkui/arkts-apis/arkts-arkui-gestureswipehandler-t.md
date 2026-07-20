# GestureSwipeHandler

```TypeScript
declare type GestureSwipeHandler = (index: number, event: SwiperAnimationEvent) => void
```

在页面跟手滑动过程中，逐帧触发的回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type GestureSwipeHandler = (index: number, event: SwiperAnimationEvent) => void--><!--Device-unnamed-declare type GestureSwipeHandler = (index: number, event: SwiperAnimationEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 当前显示元素的索引。  |
| event | [SwiperAnimationEvent](../arkts-components/arkts-arkui-swiperanimationevent-i.md) | 是 | 动画相关信息，只返回主轴方向上当前显示元素相对于ArcSwiper起始位置的位移。  |

