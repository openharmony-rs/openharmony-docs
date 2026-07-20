# SwiperContentTransitionProxy

ArcSwiper自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画视窗内的页面信息，同时，也可以通过调用该对象的finishTransition接口通知ArcSwiper组件页面自定义动画已结束。

> **说明：**

> - 假设当前选中的子组件的索引为0，从第0页切换到第1页的动画过程中，每帧都会对视窗内所有页面触发回调，当视窗内有第0页和第1页两页时，每帧会触发两次回调。其中第一次回调的selectedIndex为0，index为0，  
> position为当前帧第0页相对于动画开始前第0页的移动比例，mainAxisLength为主轴方向上第0页的长度；第二次回调的selectedIndex仍为0，index为1，position为当前帧第1页相对于动画开始前第0  
> 页的移动比例，mainAxisLength为主轴方向上第1页的长度。  
>  
> - 若动画曲线为弹簧插值曲线，从第0页切换到第1页的动画过程中，可能会因为离手时的位置和速度，先过滑到第2页，再回弹到第1页，该过程中每帧会对视窗内第1页和第2页触发回调。

**起始版本：** 18

<!--Device-unnamed-declare interface SwiperContentTransitionProxy--><!--Device-unnamed-declare interface SwiperContentTransitionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSwiperAttribute, ArcSwiper, ArcDirection, ArcSwiperController, ArcDotIndicator } from '@kit.ArkUI';
```

<a id="finishtransition"></a>
## finishTransition

```TypeScript
finishTransition(): void
```

通知ArcSwiper组件，此页面的自定义动画已结束。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentTransitionProxy-finishTransition(): void--><!--Device-SwiperContentTransitionProxy-finishTransition(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## index

```TypeScript
index: number
```

视窗内页面的索引。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentTransitionProxy-index: number--><!--Device-SwiperContentTransitionProxy-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## mainAxisLength

```TypeScript
mainAxisLength: number
```

index对应页面在主轴方向上的长度。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentTransitionProxy-mainAxisLength: number--><!--Device-SwiperContentTransitionProxy-mainAxisLength: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## position

```TypeScript
position: number
```

index页面相对于ArcSwiper主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentTransitionProxy-position: number--><!--Device-SwiperContentTransitionProxy-position: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## selectedIndex

```TypeScript
selectedIndex: number
```

当前选中页面的索引。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentTransitionProxy-selectedIndex: number--><!--Device-SwiperContentTransitionProxy-selectedIndex: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

