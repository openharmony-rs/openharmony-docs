# AnimationStartHandler

```TypeScript
declare type AnimationStartHandler = (index: number, targetIndex: number, event: SwiperAnimationEvent) => void
```

切换动画开始时的回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type AnimationStartHandler = (index: number, targetIndex: number, event: SwiperAnimationEvent) => void--><!--Device-unnamed-declare type AnimationStartHandler = (index: number, targetIndex: number, event: SwiperAnimationEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 当前显示元素的索引，动画开始前的index值（不是最终结束动画的index值）。  |
| targetIndex | number | 是 | 切换动画目标元素的索引。  |
| event | [SwiperAnimationEvent](../arkts-components/arkts-arkui-swiperanimationevent-i.md) | 是 | 动画相关信息，包括主轴方向上当前显示元素和目标元素相对ArcSwiper起始位置的位移，以及离手速度。  |

