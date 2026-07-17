# SwiperController

Swiper容器组件的控制器，可以将此对象绑定至Swiper组件，实现控制Swiper翻页等功能。

**起始版本：** 7

<!--Device-unnamed-declare class SwiperController--><!--Device-unnamed-declare class SwiperController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(index: number, useAnimation?: boolean)
```

翻至指定页面。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-changeIndex(index: number, useAnimation?: boolean)--><!--Device-SwiperController-changeIndex(index: number, useAnimation?: boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定页面在Swiper中的索引值。<br/>**说明：** <br/>设置的值小于0或大于最大页面索引时，取0。 |
| useAnimation | boolean | 否 | 设置翻至指定页面时是否有动效，true表示有动效，false表示没有动效。<br/>默认值：false。 |

## changeIndex

```TypeScript
changeIndex(index: number, animationMode?: SwiperAnimationMode | boolean)
```

翻页至指定页面。

> **说明：**

> 该接口本身提供了不带动画跳转页面的能力（animationMode设置为false或者SwiperAnimationMode.NO_ANIMATION），不建议使用changeIndex接口启动动画后，直接使用  
> finishAnimation接口打断来实现页面不带动画跳转。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-changeIndex(index: number, animationMode?: SwiperAnimationMode | boolean)--><!--Device-SwiperController-changeIndex(index: number, animationMode?: SwiperAnimationMode | boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定页面在Swiper中的索引值。<br/>**说明：** <br/>设置的值小于0或大于最大页面索引时，取0。 |
| animationMode | SwiperAnimationMode \| boolean | 否 | 设置翻页至指定页面时的动效模式。<br/>默认值：SwiperAnimationMode.NO_ANIMATION<br/> **说明：** <br/>当传入true时有动效，等同于SwiperAnimationMode.DEFAULT_ANIMATION；当传入false时无动效，等同于SwiperAnimationMode.NO_ANIMATION。 |

## constructor

```TypeScript
constructor()
```

SwiperController的构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-constructor()--><!--Device-SwiperController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fakeDragBy

```TypeScript
fakeDragBy(offset: number): boolean
```

设置模拟拖拽的拖拽距离。

> **说明：**

> - 模拟拖拽的距离需要依赖布局体现，建议接口在布局前调用，拖拽效果可以在当前帧布局后体现。如果在未布局前调用了多次该接口，当前帧布局时只生效最后一次调用传入的拖拽距离。  
>  
> - 在[loop](SwiperAttribute#loop)设置为true的循环场景下，如果设置的模拟拖拽的距离大于布局总长度，此时模拟拖拽距离会被调整为拖拽到刚好显示第一个子节点（向布局起点拖拽）或者最后一个子  
> 节点（向布局终点方向拖拽）的距离。  
>  
> - [onGestureSwipe](SwiperAttribute#onGestureSwipe)事件、  
> [onContentWillScroll](SwiperAttribute#onContentWillScroll)事件在拖拽过程中不触发。  
> [customContentTransition](SwiperAttribute#customContentTransition)会在布局前触发，由于真实的拖拽距离可能在布局时被调整，在传入拖拽距离过大时，触发事  
> 件时的返回的节点显示信息可能与布局结果不一致。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-fakeDragBy(offset: number): boolean--><!--Device-SwiperController-fakeDragBy(offset: number): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 需要模拟拖拽的拖拽距离。<br/>正数表示向布局起点拖拽；负数表示向布局终点方向拖拽。<br>单位为：vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否消费传入的拖拽距离。<br/>true表示消费任意传入的拖拽距离；false表示当前没有在模拟拖拽中，或者已经拖拽到边界，没有消费传入的拖拽距离。<br/>设置0为不可消费的拖拽距离。 |

## finishAnimation

```TypeScript
finishAnimation(callback?: VoidCallback)
```

停止播放动画。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-finishAnimation(callback?: VoidCallback)--><!--Device-SwiperController-finishAnimation(callback?: VoidCallback)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 否 | 动画结束的回调。<br>**起始版本：** 18 |

## isFakeDragging

```TypeScript
isFakeDragging(): boolean
```

获取是否在模拟拖拽中的状态。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-isFakeDragging(): boolean--><!--Device-SwiperController-isFakeDragging(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否处在模拟拖拽状态。<br/>true表示当前处在模拟拖拽状态；false表示当前不处在模拟拖拽状态。 |

## preloadItems

```TypeScript
preloadItems(indices: Optional<Array<number>>): Promise<void>
```

控制Swiper预加载指定子节点。调用该接口后会一次性加载所有指定的子节点，因此为了性能考虑，建议分批加载子节点。使用Promise异步回调。

如果SwiperController对象未绑定任何Swiper组件，直接调用该接口，会抛出JS异常，并返回错误码100004。因此使用该接口时，建议通过try-catch捕获异常。

与[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和自定义组件结合使用时，由于[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)只会保留缓存范围内的自定义组件，在缓存范围外的会被删除，因此需要开发者保证通过该接口预加载的节点index在缓存范围内。

> **说明：**

> Swiper的preloadItems需要在Swiper创建之后去调用，首次预加载推荐在Swiper的[onAppear](arkts-arkui-common-commonmethod-c.md#onappear-1)生命周期中去控制。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-preloadItems(indices: Optional<Array<number>>): Promise<void>--><!--Device-SwiperController-preloadItems(indices: Optional<Array<number>>): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indices | [Optional](arkts-arkui-optional-t.md)<Array<number>> | 是 | 需预加载的子节点的下标数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter invalid. Possible causes:<br> 1. The parameter type is not Array&lt;number&gt;.<br> 2. The parameter is an empty array.<br> 3. The parameter contains an invalid index. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to component. |

## showNext

```TypeScript
showNext()
```

翻至下一页。翻页带动效切换过程，时长通过Swiper的[duration](SwiperAttribute#duration)属性设置。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-showNext()--><!--Device-SwiperController-showNext()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showPrevious

```TypeScript
showPrevious()
```

翻至上一页。翻页带动效切换过程，时长通过Swiper的[duration](SwiperAttribute#duration)属性设置。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-showPrevious()--><!--Device-SwiperController-showPrevious()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startFakeDrag

```TypeScript
startFakeDrag(): boolean
```

开启模拟拖拽功能。

> **说明：**

> - Swiper已经处在真实手势拖拽中，或者已经开启了模拟拖拽，调用接口会返回false表示操作失败。  
>  
> - 模拟拖拽无法触发嵌套滚动。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-startFakeDrag(): boolean--><!--Device-SwiperController-startFakeDrag(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否开启模拟拖拽功能。<br/>true表示开启模拟拖拽功能成功；false表示开启模拟拖拽功能失败。 |

## stopFakeDrag

```TypeScript
stopFakeDrag(): boolean
```

关闭模拟拖拽功能。

> **说明：**

> 在开启模拟拖拽后，如果接收到真实拖拽手势，模拟拖拽会结束。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperController-stopFakeDrag(): boolean--><!--Device-SwiperController-stopFakeDrag(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否关闭模拟拖拽功能。<br/>true表示关闭模拟拖拽功能成功；false表示关闭模拟拖拽功能失败。 |

