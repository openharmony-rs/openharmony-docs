# Swiper属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：
> **说明：**
> Swiper组件通用属性[clip](arkts-arkui-commonmethod-c.md#clip)的默认值为true。

**继承/实现关系：** SwiperAttribute extends [CommonMethod<SwiperAttribute>](CommonMethod<SwiperAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class SwiperAttribute extends CommonMethod<SwiperAttribute>--><!--Device-unnamed-declare class SwiperAttribute extends CommonMethod<SwiperAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoPlay

```TypeScript
autoPlay(value: boolean)
```

设置子组件是否自动播放。轮播方向为索引从小到大。

[loop](SwiperAttribute#loop)为false时，自动轮播到最后一页时停止轮播。手势切换后不是最后一页时继续播放。当Swiper不可见时会停止轮播。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-autoPlay(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-autoPlay(value: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 子组件是否自动播放。<br/>true：自动播放；false：不自动播放。<br/>传入非法值时，按false处理。 |

## autoPlay

```TypeScript
autoPlay(autoPlay: boolean, options: AutoPlayOptions)
```

设置子组件是否自动播放。options入参控制手指或者鼠标等按下屏幕时子组件是否停止自动播放。

当[loop](SwiperAttribute#loop)设置为false时，自动轮播将在到达最后一页时停止。在通过手势切换且未处于最后一页的情况下，轮播将继续进行。Swiper在不可见时，轮播也将停止。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-autoPlay(autoPlay: boolean, options: AutoPlayOptions): SwiperAttribute--><!--Device-SwiperAttribute-autoPlay(autoPlay: boolean, options: AutoPlayOptions): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| autoPlay | boolean | 是 | 子组件是否自动播放。<br/>true：自动播放；false：不自动播放。<br/>传入非法值时，按false处理。 |
| options | [AutoPlayOptions](arkts-arkui-autoplayoptions-i.md) | 是 | 配置手指或者鼠标等按下屏幕时子组件是否停止自动播放。当stopWhenTouched设置为true时，多指按下场景中任意一个手指抬起后，将自动继续播放。<br/>默认值：{ stopWhenTouched: true }，停止自动播放。 |

## cachedCount

```TypeScript
cachedCount(value: number)
```

设置预加载子组件个数，以当前页面为基准，加载当前显示页面的前后个数。前面item删除，后面会向前补位。例如cachedCount=1时，会将当前显示的页面的前面一页和后面一页的子组件都预加载。如果设置为按组翻页，即displayCount的swipeByGroup参数设为true，预加载时会以组为基本单位。例如cachedCount=1，swipeByGroup=true时，会将当前组的前面一组和后面一组的子组件都预加载。
> **说明：**
> - 在连续滑动场景中，一屏显示一个Swiper子组件时，通常将cachedCount值设置为1或2即可。最佳实践请参考  
> [优化Swiper组件加载慢丢帧问题-缓存数据项](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-swiper_high_performance_development_guide#section143504547145)。  
>  
>  
> - 只在[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和开启了virtualScroll开关的  
> [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)中生效，生效后超出显示及缓存范围的子节点会被释放。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-cachedCount(value: number): SwiperAttribute--><!--Device-SwiperAttribute-cachedCount(value: number): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 预加载子组件个数。<br/>默认值：1<br/>取值范围：[0, +∞)，设置小于0的值时，按照默认值处理。 |

## cachedCount

```TypeScript
cachedCount(count: number, isShown: boolean)
```

设置预加载子组件个数。
> **说明：**
> - isShown值为true，且设置的count过大时，如果前后预加载范围内可加载的节点不足，循环场景下同一个可加载节点只会布局在一侧。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-cachedCount(count: number, isShown: boolean): SwiperAttribute--><!--Device-SwiperAttribute-cachedCount(count: number, isShown: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 预加载子组件个数。<br/>默认值：1<br/>取值范围：[0, +∞)，设置小于0的值时，按照默认值处理。 |
| isShown | boolean | 是 | 预加载范围内的节点是否进行绘制，不下渲染树。<br/>true：预加载范围内的节点进行绘制；false：预加载范围内的节点不进行绘制。<br/>传入非法值时，按false处理。 |

## cachedCount

```TypeScript
cachedCount(count: number, options: CachedCountOptions)
```

设置预加载子组件个数和配置选项。
> **说明：**
> - 当options的independent设置为true时，预加载子组件个数按count个数计算，与  
> [displayCount](SwiperAttribute#displayCount(value: number | string | SwiperAutoFill | ItemFillPolicy, swipeByGroup?: boolean))  
> 的分组swipeByGroup计算解耦。例如cachedCount的count为1时，会将当前显示子节点的前一个和后一个子组件预加载。  
>  
> - 当displayCount的swipeByGroup参数设为true，且options的independent为false（默认值）时，预加载子组件个数以组为基本单位。例如cachedCount的count为1，  
> displayCount的value为2，displayCount的swipeByGroup为true时，会将当前显示组的前一组和后一组的各两个子组件预加载。  
>  
> - 只在[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和开启了virtualScroll开关的  
> [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)中生效，生效后超出缓存范围的子节点会被释放。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-cachedCount(count: number, options: CachedCountOptions): SwiperAttribute--><!--Device-SwiperAttribute-cachedCount(count: number, options: CachedCountOptions): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 预加载子组件个数。<br/>。<br>取值范围：[0, +∞)。 |
| options | [CachedCountOptions](arkts-arkui-cachedcountoptions-i.md) | 是 | 预加载子组件的配置选项。 |

## curve

```TypeScript
curve(value: Curve | string | ICurve)
```

设置Swiper的动画曲线，默认为弹簧插值曲线，常用曲线参考[Curve](../arkts-apis/arkts-arkui-curve-e.md)，也可以通过[插值计算](../arkts-apis/arkts-curves.md)模块提供的接口创建自定义的插值曲线对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-curve(value: Curve | string | ICurve): SwiperAttribute--><!--Device-SwiperAttribute-curve(value: Curve | string | ICurve): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Curve](../arkts-apis/arkts-arkui-curve-e.md) \| string \| ICurve | 是 | Swiper的动画曲线。<br/>string类型来源[curves.init](../arkts-apis/arkts-arkui-curves-init-f.md#init)，[curves.steps](../arkts-apis/arkts-arkui-curves-steps-f.md#steps)，[curves.cubicBezier](../arkts-apis/arkts-arkui-curves-cubicbezier-f.md#cubicbezier)，[curves.spring](../arkts-apis/arkts-arkui-curves-spring-f.md#spring)函数从API version 9开始废弃，推荐使用Curve和ICurve类型。<br/>默认值：[interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md#interpolatingspring)(-1, 1, 328, 34)<br>**起始版本：** 8 - 9 |

## customContentTransition

```TypeScript
customContentTransition(transition: SwiperContentAnimatedTransition)
```

自定义Swiper页面切换动画。在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发回调，开发者可以在回调中设置透明度、缩放比例、位移等属性来自定义切换动画。

使用说明：

1、循环场景下，设置prevMargin和nextMargin属性，使得Swiper前后端显示同一页面时，该接口不生效。

2、在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发[SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md)回调。例如，当视窗内有下标为0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。

3、设置displayCount属性的swipeByGroup参数为true时，若同组中至少有一个页面在视窗内时，则会对同组中所有页面触发回调，若同组所有页面均不在视窗内时，则会一起下渲染树。

4、在页面跟手滑动和离手后执行切换动画的过程中，默认动画（页面滑动）依然会发生，若希望页面不滑动，可以设置主轴方向上负的位移（translate属性）来抵消页面滑动。例如：当displayCount属性值为2，视窗内有下标为0、1的两个页面时，页面水平滑动过程中，可以逐帧设置第0页的translate属性在x轴上的值为-position * mainAxisLength来抵消第0页的位移，设置第1页的translate属性在x轴上的值为-(position  
- 1) * mainAxisLength来抵消第1页的位移。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-customContentTransition(transition: SwiperContentAnimatedTransition): SwiperAttribute--><!--Device-SwiperAttribute-customContentTransition(transition: SwiperContentAnimatedTransition): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | [SwiperContentAnimatedTransition](arkts-arkui-swipercontentanimatedtransition-i.md) | 是 | Swiper自定义切换动画相关信息。 |

## disableSwipe

```TypeScript
disableSwipe(value: boolean)
```

设置禁用组件滑动切换功能。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-disableSwipe(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-disableSwipe(value: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 禁用组件滑动切换功能。设置为true禁用，false不禁用。<br/>默认值：false |

## displayArrow

```TypeScript
displayArrow(value: ArrowStyle | boolean, isHoverShow?: boolean)
```

设置导航点箭头样式。
> **说明：**
> Swiper视窗内显示所有子节点时，只显示一屏，无法翻页，左右翻页箭头均不显示。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAttribute-displayArrow(value: ArrowStyle | boolean, isHoverShow?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-displayArrow(value: ArrowStyle | boolean, isHoverShow?: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ArrowStyle](arkts-arkui-arrowstyle-i.md) \| boolean | 是 | 支持设置箭头和底板样式，异常场景使用ArrowStyle对象中的默认值。设置为false不显示箭头和底板，true显示默认的箭头和底板样式。<br/>默认值：false |
| isHoverShow | boolean | 否 | 设置鼠标悬停时是否显示箭头。<br/>默认值：false<br/>**说明：**<br/>1. isHoverShow为false时，常驻显示箭头。<br/>2.isHoverShow为true时，有导航点时鼠标悬停在导航点和箭头范围内显示箭头，无导航点时鼠标悬停在Swiper显示范围内显示箭头。<br/>3. 箭头显示时，支持点击翻页。 |

## displayCount

```TypeScript
displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean)
```

设置Swiper视窗内元素显示个数。

使用number类型时，子元素主轴宽度会基于Swiper主轴宽度适应。子组件按照主轴均分Swiper宽度（减去displayCount-1个itemSpace）的方式进行主轴拉伸（收缩）布局，设置为小于等于0的值时，按默认值1显示。

使用string类型时，根据子元素的主轴宽度线性布局，不再适应Swiper主轴宽度。此时value值仅支持设置为'auto'，设置[customContentTransition](SwiperAttribute#customContentTransition)和[onContentDidScroll](SwiperAttribute#onContentDidScroll)事件不生效。

使用SwiperAutoFill类型时，子元素主轴宽度会基于Swiper主轴宽度适应。通过设置一个子组件最小宽度值minSize，会根据Swiper当前宽度和minSize值自动计算并更改一页内元素显示个数。当minSize为空或者小于等于0时，Swiper显示1列。
> **说明：**
> - 按组进行翻页时，判定翻页的拖拽距离阈值将调整为Swiper宽度的50%（若按子元素翻页，该阈值为子元素宽度的50%）。若最后一组的子元素数量少于displayCount，将利用占位子元素进行填充，占位子元素仅用于布局定位，  
> 不显示任何内容，其位置将直接显示Swiper的背景样式。  
>  
> - displayCount设置为'auto'，并且设置loop属性的值为false时，选中导航点的位置与视窗内首个页面的位置保持一致。如果翻页完成后，视窗内首个页面仅部分显示在视窗内，选中导航点亦与页面的位置保持一致，位于两  
> 个未选中的导航点之间。在此情况下，建议开发者隐藏导航点。  
>  
> - 导航点样式设定为圆形导航点，视窗内显示子元素数量等于1时（单页场景）或者 displayCount设置为'auto'时，显示导航点数量等于子元素数量。  
>  
> - displayCount设置为'auto'时，若设置swipeByGroup为true，则单个子元素按组翻页，一次只能翻一页。在此情况下，建议开发者不设置swipeByGroup或者设置swipeByGroup为  
> false。  
>  
> - 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

当导航点样式设定为圆形导航点，视窗内显示子元素数量大于1（多页场景）<!--RP1--><!--RP1End-->，显示导航点数量情况如下表：

| 子元素总数量是否大于视窗内显示的子元素数量 | 是否按组翻页 | 是否循环 | 圆形导航点显示数量 | 说明 |  
| ------------------------------------------ | ------------ | --------------- | ------------------------------------------------------------ | ---------------------------------------- |  
| 是 | 是 | loop设置为true | 圆形导航点的数量将与组数相等（组数计算方式为子元素总数量除以视窗内显示的子元素数量，若除不尽，则向上取整） | 该效果在displayCount设置为'auto'时不生效 |  
| 是 | 是 | loop设置为false | 圆形导航点的数量将与组数相等（组数计算方式为子元素总数量除以视窗内显示的子元素数量，若除不尽，则向上取整） | 该效果在displayCount设置为'auto'时不生效 |  
| 是 | 否 | loop设置为true | 圆形导航点的数量将与实际可翻页次数一致（显示导航点的数量等于子元素总数量） | —— |  
| 是 | 否 | loop设置为false | 圆形导航点的数量将与实际可翻页次数一致（计算方式是子元素的总数量减去视窗内显示的子元素数量+1个） | 该效果在displayCount设置为'auto'时不生效 |  
| 否（同时子元素的总数量大于0） | —— | —— | 显示1个圆形导航点 | 该效果在displayCount设置为'auto'时不生效 |  
| 否（同时子元素的总数量等于0） | —— | —— | 显示0个圆形导航点 | —— |

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| SwiperAutoFill | 是 | 视窗内显示的子元素个数。<br/> 默认值：1<br/>取值范围：(0, +∞)，设置小于等于0的值时，按照默认值处理。<br>**起始版本：** 8 - 9 |
| swipeByGroup | boolean | 否 | 是否按组进行翻页。如果设为true，在翻页时会按组进行翻页，每组内子元素的数量为displayCount value的值；如果为false，则为默认翻页行为，即按照子元素进行翻页。<br/> 默认值：false<br>**起始版本：** 11 |

## displayCount

```TypeScript
displayCount(value: number | string | SwiperAutoFill | ItemFillPolicy, swipeByGroup?: boolean)
```

设置Swiper视窗内元素显示个数。

使用number类型时，子元素主轴宽度会基于Swiper主轴宽度适应。子组件按照主轴均分Swiper宽度（减去displayCount-1个itemSpace）的方式进行主轴拉伸（收缩）布局，设置为小于等于0的值时，按默认值1显示。

使用string类型时，根据子元素的主轴宽度线性布局，不再适应Swiper主轴宽度。此时value值仅支持设置为'auto'，设置[customContentTransition](SwiperAttribute#customContentTransition)和[onContentDidScroll](SwiperAttribute#onContentDidScroll)事件不生效。

使用SwiperAutoFill类型时，子元素主轴宽度会基于Swiper主轴宽度适应。通过设置一个子组件最小宽度值minSize，会根据Swiper当前宽度和minSize值自动计算并更改一页内元素显示个数。当minSize为空或者小于等于0时，Swiper显示1列。

使用ItemFillPolicy类型时，子元素主轴宽度会基于Swiper主轴宽度适应。将根据Swiper组件宽度对应断点类型确定显示个数。例如，设置断点类型为ItemFillPolicy.BREAKPOINT_DEFAULT时，在组件宽度相当于sm及更小断点区间时显示1列，相当于md断点区间时显示2列，相当于lg及更大断点区间时显示3列。

参数说明参考[displayCount](SwiperAttribute#displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean))。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-displayCount(value: number | string | SwiperAutoFill | ItemFillPolicy, swipeByGroup?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-displayCount(value: number | string | SwiperAutoFill | ItemFillPolicy, swipeByGroup?: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| SwiperAutoFill \| ItemFillPolicy | 是 | 视窗内显示的子元素个数。<br/> 取值范围：(0, +∞)，设置小于等于0的值时，按照1处理。 |
| swipeByGroup | boolean | 否 | 是否按组进行翻页。如果设为true，在翻页时会按组进行翻页，每组内子元素的数量为displayCount的值；如果为false，则为默认翻页行为，即按照子元素进行翻页。<br/> 默认值：false |

## displayMode

```TypeScript
displayMode(value: SwiperDisplayMode)
```

设置主轴方向上元素排列的模式，优先以[displayCount](SwiperAttribute#displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean))设置的个数显示，displayCount未设置时本属性生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-displayMode(value: SwiperDisplayMode): SwiperAttribute--><!--Device-SwiperAttribute-displayMode(value: SwiperDisplayMode): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SwiperDisplayMode](arkts-arkui-swiperdisplaymode-e.md) | 是 | 主轴方向上元素排列的模式。<br/>默认值：SwiperDisplayMode.STRETCH |

## duration

```TypeScript
duration(value: number)
```

设置子组件切换的动画时长。

duration需要和[curve](SwiperAttribute#curve)一起使用。

curve默认曲线为[interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md#interpolatingspring)，此时动画时长只受曲线自身参数影响，不再受duration的控制。不受duration控制的曲线可以查阅[插值计算](../arkts-apis/arkts-curves.md)模块，比如，[springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md#springmotion)、[responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md#responsivespringmotion)和interpolatingSpring类型的曲线不受duration控制。如果希望动画时长受到duration控制，需要给curve设置其他曲线。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAttribute-duration(value: number): SwiperAttribute--><!--Device-SwiperAttribute-duration(value: number): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 子组件切换的动画时长。<br/>默认值：400<br/>单位：毫秒<br/>取值范围：[0, +∞)，设置小于0的值时，按照默认值处理。 |

## effectMode

```TypeScript
effectMode(value: EdgeEffect)
```

设置边缘滑动效果，[loop](SwiperAttribute#loop)为false或Swiper视窗内一屏显示所有子节点时生效。调用[SwiperController.changeIndex()](arkts-arkui-swipercontroller-c.md#changeindex)、[SwiperController.showNext()](arkts-arkui-swipercontroller-c.md#shownext)和[SwiperController.showPrevious()](arkts-arkui-swipercontroller-c.md#showprevious)接口跳转至首尾页时不生效回弹。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-effectMode(value: EdgeEffect): SwiperAttribute--><!--Device-SwiperAttribute-effectMode(value: EdgeEffect): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | 是 | 边缘滑动效果。<br/>默认值：EdgeEffect.Spring |

## index

```TypeScript
index(value: number)
```

设置当前在容器中显示的子组件的索引值。

从API version 10开始，该属性支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-index(value: number): SwiperAttribute--><!--Device-SwiperAttribute-index(value: number): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前在容器中显示的子组件的索引值。<br/>默认值：0 <br/>**说明：** <br/>设置的值小于0或大于最大页面索引时，取0。 |

## indicator

```TypeScript
indicator(value: DotIndicator | DigitIndicator | boolean)
```

设置可选导航点指示器样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-indicator(value: DotIndicator | DigitIndicator | boolean): SwiperAttribute--><!--Device-SwiperAttribute-indicator(value: DotIndicator | DigitIndicator | boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DotIndicator](arkts-arkui-dotindicator-c.md) \| DigitIndicator \| boolean | 是 | 可选导航点指示器样式。<br/> - DotIndicator：圆点指示器样式。<br/> - DigitIndicator：数字指示器样式。<br/> - boolean：是否启用导航点指示器。设置为true启用，false不启用。<br/>默认值：true<br/>默认类型：DotIndicator<br>**起始版本：** 7 - 9 |

## indicator

```TypeScript
indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean)
```

设置外部绑定的导航点组件控制器。
> **说明：**
> 设置外部绑定的导航点组件控制器后，可以和外部导航点结合使用。外部导航点支持自定义设置显示位置和大小。详细介绍可参看[Indicator](arkts-arkui-indicatorcomponent.md)。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean): SwiperAttribute--><!--Device-SwiperAttribute-indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indicator | [IndicatorComponentController](arkts-arkui-indicatorcomponentcontroller-c.md) \| DotIndicator \| DigitIndicator \| boolean | 是 | 可选导航点指示器样式。<br/>-IndicatorComponentController：单独导航点指示器控制器。当使用单独导航点指示器控制器时，可以与外部单独导航点进行绑定，但是绑定的单独导航点和内置导航点不能同时存在。<br/> -DotIndicator：圆点指示器样式。<br/> - DigitIndicator：数字指示器样式。<br/> - boolean：是否启用导航点指示器。设置为true启用，false不启用。<br/>默认值：true<br/>默认类型：DotIndicator |

## indicatorInteractive

```TypeScript
indicatorInteractive(value: boolean)
```

设置禁用组件导航点交互功能。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAttribute-indicatorInteractive(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-indicatorInteractive(value: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 导航点是否可交互。<br/>true：导航点可交互；false：导航点不可交互。<br/>传入参数非法时，按true处理。 |

## indicatorStyle

```TypeScript
indicatorStyle(value?: IndicatorStyle)
```

设置导航点样式。
> **说明：**
> 从API version 8开始支持，从API version 10开始废弃，建议使用  
> [indicator](SwiperAttribute#indicator(value: DotIndicator | DigitIndicator | boolean))替代。

**起始版本：** 8

**废弃版本：** 10

**替代接口：** indicator(value:

<!--Device-SwiperAttribute-indicatorStyle(value?: IndicatorStyle): SwiperAttribute--><!--Device-SwiperAttribute-indicatorStyle(value?: IndicatorStyle): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | 否 | 导航点样式。 |

## interval

```TypeScript
interval(value: number)
```

设置使用自动播放时播放的时间间隔。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-interval(value: number): SwiperAttribute--><!--Device-SwiperAttribute-interval(value: number): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 自动播放时播放的时间间隔。当该值小于[duration](SwiperAttribute#duration)属性值时，翻页完成后会立即开始下一次轮播。<br/>默认值：3000<br/>单位：毫秒<br/>取值范围：[0, +∞)，设置小于0的值时，按照默认值处理。 |

## itemSpace

```TypeScript
itemSpace(value: number | string)
```

设置子组件与子组件之间间隙。不支持设置百分比。

类型为number时，默认单位vp。类型为string时，需要显式指定像素单位，如'10px'；未指定像素单位时，如'10'，单位为vp。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-itemSpace(value: number | string): SwiperAttribute--><!--Device-SwiperAttribute-itemSpace(value: number | string): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 子组件与子组件之间间隙。<br/>默认值：0<br/>取值范围：[0, +∞)，当设置数值小于0或超出Swiper组件宽度范围时，按照默认值处理。 |

## loop

```TypeScript
loop(value: boolean)
```

设置是否开启循环。在LazyForEach懒循环加载模式下，加载的组件数量建议大于5个。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-loop(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-loop(value: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启循环。<br/>true：开启循环；false：不开启循环。<br/>传入参数非法时，按true处理。 |

## maintainVisibleContentPosition

```TypeScript
maintainVisibleContentPosition(enabled: boolean)
```

设置显示区域上方或前方插入或删除数据时是否保持可见内容位置不变。适用于使用单一[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)作为Swiper子节点的情况，通过LazyForEach的[onDataAdd](arkts-arkui-datachangelistener-i.md#ondataadd)、[onDataDelete](arkts-arkui-datachangelistener-i.md#ondatadelete)等接口修改数据源。其他场景下，显示区域上方或前方插入或删除数据，可见内容位置会变化。

在[displayCount](SwiperAttribute#displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean))属性的swipeByGroup参数设置为true，即按组翻页生效时，一次在显示区域上方或前方插入或删除数据，且插入或删除的是一组节点数量倍数的数据量时，才能保持可见内容位置不变，否则可见内容位置可能会随每组数据重新分组改变。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-maintainVisibleContentPosition(enabled: boolean): SwiperAttribute--><!--Device-SwiperAttribute-maintainVisibleContentPosition(enabled: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置显示区域上方或前方插入或删除数据时是否要保持可见内容位置不变。<br/>默认值：false，显示区域上方或前方插入或删除数据时可见内容位置会跟随变化。 true：显示区域上方或前方插入或删除数据时可见内容位置不变。如果改变数据源是在动画过程中，由于目标索引变化会导致动画停止。 |

## nestedScroll

```TypeScript
nestedScroll(value: SwiperNestedScrollMode)
```

设置Swiper组件和父组件的嵌套滚动模式。[loop](SwiperAttribute#loop)为true时Swiper组件没有边缘，不会触发父组件嵌套滚动。
> **说明：**
> 由于Swiper的抛滑动画逻辑和其它滚动类组件不同（Swiper一次只能滑动一页，抛滑时做翻页动画），当Swiper内嵌套其它滚动组件时，如果Swiper的翻页动画已经启动，将无法接受子节点上传的滚动偏移量。这时Swiper的  
> 翻页动画和子节点的边缘效果动画会同时执行。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAttribute-nestedScroll(value: SwiperNestedScrollMode): SwiperAttribute--><!--Device-SwiperAttribute-nestedScroll(value: SwiperNestedScrollMode): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SwiperNestedScrollMode](arkts-arkui-swipernestedscrollmode-e.md) | 是 | Swiper组件和父组件的嵌套滚动模式。<br/>传入非法值时，按SwiperNestedScrollMode.SELF_ONLY处理。 |

## nextMargin

```TypeScript
nextMargin(value: Length, ignoreBlank?: boolean)
```

设置后边距，用于露出后一项的一小部分，使用效果可以参考[示例1设置导航点交互及翻页动效](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#示例1设置导航点交互及翻页动效)。仅当Swiper子组件的布局方式为拉伸时生效，主要包括两种场景：1、displayMode属性设置为SwiperDisplayMode.STRETCH；2、displayCount属性设置为number类型。

当主轴方向为横向布局时，nextMargin或prevMargin中任意一个大于子组件测算的宽度，nextMargin和prevMargin均不显示。

当主轴方向为纵向布局时，nextMargin或prevMargin中任意一个大于子组件测算的高度，nextMargin和prevMargin均不显示。

使用nextMargin/prevMargin接口时，不要对子组件进行[尺寸范围限制](arkts-arkui-commonmethod-c.md#constraintsize)，否则子节点主轴将不会被拉伸到预期长度，边距失去效果。
> **说明：**
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAttribute-nextMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-nextMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 后边距。不支持设置百分比。<br/>默认值：0 |
| ignoreBlank | boolean | 否 | 非loop场景下尾页不显示nextMargin。在非loop场景下，设置为true时，尾页不显示空白的nextMargin，尾页的右边缘与Swiper视窗右边缘对齐；设置false时，尾页显示空白nextMargin，尾页的右边缘与Swiper视窗右边缘的距离为nextMargin。<br/>默认值：false <br/>**说明：**<br/>尾页场景下，prevMargin和nextMargin的值相加作为左边边距显示前一个页面。<br>**起始版本：** 12 |

## onAnimationEnd

```TypeScript
onAnimationEnd(event: OnSwiperAnimationEndCallback)
```

切换动画结束时触发该回调。

当Swiper切换动效结束时触发，包括动画过程中手势中断，通过SwiperController调用finishAnimation。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-onAnimationEnd(event: OnSwiperAnimationEndCallback): SwiperAttribute--><!--Device-SwiperAttribute-onAnimationEnd(event: OnSwiperAnimationEndCallback): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnSwiperAnimationEndCallback](arkts-arkui-onswiperanimationendcallback-t.md) | 是 | 切换动画结束时触发的回调。<br>**起始版本：** 18 |

## onAnimationStart

```TypeScript
onAnimationStart(event: OnSwiperAnimationStartCallback)
```

切换动画开始时触发该回调。
> **说明：**
> - 调用此回调后，切换动画的逻辑将在渲染线程中执行，从而使处于空闲状态的主线程能够充分利用这段时间来加载子组件所需资源，减少后续在cachedCount范围内节点的预加载时间。最佳实践请参考  
> [优化Swiper组件加载慢丢帧问题-提前加载数据](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-swiper_high_performance_development_guide#section8783121513246)。  
>  
>  
> - 当翻页动画时长为0时，只有以下场景会触发该回调：滑动翻页、自动轮播、调用SwiperController.showNext()和SwiperController.showPrevious()接口以及手指点击导航点翻页。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-onAnimationStart(event: OnSwiperAnimationStartCallback): SwiperAttribute--><!--Device-SwiperAttribute-onAnimationStart(event: OnSwiperAnimationStartCallback): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnSwiperAnimationStartCallback](arkts-arkui-onswiperanimationstartcallback-t.md) | 是 | 切换动画开始时触发的回调。<br>**起始版本：** 18 |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

当前显示元素索引变化时触发该事件，返回值为当前显示元素的索引值。

Swiper组件结合LazyForEach使用时，不能在onChange事件里触发子页面UI的刷新。
> **说明：**
> 如果是动画引起的索引变化，回调在动画结束时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-onChange(event: Callback<number>): SwiperAttribute--><!--Device-SwiperAttribute-onChange(event: Callback<number>): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 当前显示元素的索引。<br>**起始版本：** 18 |

## onContentDidScroll

```TypeScript
onContentDidScroll(handler: ContentDidScrollCallback)
```

监听Swiper页面滑动事件。

使用说明：

1、循环场景下，设置prevMargin和nextMargin属性，使得Swiper前后端显示同一页面时，该接口不生效。

2、在页面滑动过程中，会对视窗内所有页面逐帧触发[ContentDidScrollCallback](arkts-arkui-contentdidscrollcallback-t.md)回调。例如，当视窗内有下标为0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。

3、设置displayCount属性的swipeByGroup参数为true时，若同组中至少有一个页面在视窗内时，则会对同组中所有页面触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAttribute-onContentDidScroll(handler: ContentDidScrollCallback): SwiperAttribute--><!--Device-SwiperAttribute-onContentDidScroll(handler: ContentDidScrollCallback): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [ContentDidScrollCallback](arkts-arkui-contentdidscrollcallback-t.md) | 是 | Swiper滑动时触发的回调。 |

## onContentWillScroll

```TypeScript
onContentWillScroll(handler: ContentWillScrollCallback)
```

Swiper滑动行为拦截事件，在滑动前触发。Swiper会依据该事件的返回值来决定是否允许此次滑动行为。若返回true，表示允许此次滑动行为，Swiper页面将跟随滑动。若返回false，表示不允许此次滑动，页面将保持静止。

1. 触发该事件的场景仅限于手势操作，具体包括手指滑动、滚动鼠标滚轮以及使用键盘方向键进行焦点移动。

2. 在手指滑动的过程中，每帧都将触发该事件，系统会依据事件的返回值判断是否对每帧的滑动做出响应。

3. 对于滚动鼠标滚轮和使用键盘方向键进行焦点移动的场景，每次翻页操作都会触发一次该事件，翻页是否被允许将根据事件的返回值来决定。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-onContentWillScroll(handler: ContentWillScrollCallback): SwiperAttribute--><!--Device-SwiperAttribute-onContentWillScroll(handler: ContentWillScrollCallback): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [ContentWillScrollCallback](arkts-arkui-contentwillscrollcallback-t.md) | 是 | Swiper滑动时触发的回调。 |

## onGestureSwipe

```TypeScript
onGestureSwipe(event: OnSwiperGestureSwipeCallback)
```

在页面跟手滑动过程中，逐帧触发该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAttribute-onGestureSwipe(event: OnSwiperGestureSwipeCallback): SwiperAttribute--><!--Device-SwiperAttribute-onGestureSwipe(event: OnSwiperGestureSwipeCallback): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnSwiperGestureSwipeCallback](arkts-arkui-onswipergestureswipecallback-t.md) | 是 | 在页面跟手滑动过程中，逐帧触发的回调。onGestureSwipe回调触发时机在onTouch之后，如果需要在离手后执行操作建议使用[onAnimationStart](SwiperAttribute#onAnimationStart)。<br>**起始版本：** 18 |

## onScrollStateChanged

```TypeScript
onScrollStateChanged(event: Callback<ScrollState>)
```

Swiper滑动状态变化事件回调，在跟手滑动、离手动画、停止三种滑动状态变化时触发，返回值为当前滑动状态。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-onScrollStateChanged(event: Callback<ScrollState>): SwiperAttribute--><!--Device-SwiperAttribute-onScrollStateChanged(event: Callback<ScrollState>): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ScrollState&gt; | 是 | 滑动状态变化的回调。 |

## onSelected

```TypeScript
onSelected(event: Callback<number>)
```

当选中元素改变时触发该回调，返回值为当前选中的元素的索引值。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-onSelected(event: Callback<number>): SwiperAttribute--><!--Device-SwiperAttribute-onSelected(event: Callback<number>): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 当前选中元素的索引。 |

## onUnselected

```TypeScript
onUnselected(event: Callback<number>)
```

当选中元素改变时触发该回调，返回值为将要隐藏的元素的索引值。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-onUnselected(event: Callback<number>): SwiperAttribute--><!--Device-SwiperAttribute-onUnselected(event: Callback<number>): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 将要隐藏元素的索引。 |

## pageFlipMode

```TypeScript
pageFlipMode(mode: Optional<PageFlipMode>)
```

设置鼠标滚轮翻页模式。未通过该接口设置时，默认为连续翻页模式，取值为PageFlipMode.CONTINUOUS。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-pageFlipMode(mode: Optional<PageFlipMode>): SwiperAttribute--><!--Device-SwiperAttribute-pageFlipMode(mode: Optional<PageFlipMode>): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;PageFlipMode&gt; | 是 | 鼠标滚轮翻页模式。<br/>取undefined时，按取值为PageFlipMode.CONTINUOUS处理。 |

## prevMargin

```TypeScript
prevMargin(value: Length, ignoreBlank?: boolean)
```

设置前边距，用于露出前一项的一小部分，使用效果可以参考[示例1设置导航点交互及翻页动效](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#示例1设置导航点交互及翻页动效)。仅当Swiper子组件的布局方式为拉伸时生效，主要包括两种场景：1、displayMode属性设置为SwiperDisplayMode.STRETCH；2、displayCount属性设置为number类型。

当主轴方向为横向布局时，nextMargin/prevMargin中任意一个大于子组件测算的宽度，nextMargin和prevMargin均不显示。

当主轴方向为纵向布局时，nextMargin/prevMargin中任意一个大于子组件测算的高度，nextMargin和prevMargin均不显示。

使用nextMargin/prevMargin接口时，不要对子组件进行[尺寸范围限制](arkts-arkui-commonmethod-c.md#constraintsize)，否则子节点主轴将不会被拉伸到预期长度，边距失去效果。
> **说明：**
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperAttribute-prevMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-prevMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 前边距。不支持设置百分比。<br/>默认值：0 |
| ignoreBlank | boolean | 否 | 非loop场景下首页不显示prevMargin。在非loop场景下，设置为true时，首页不显示空白的prevMargin，首页的左边缘与Swiper视窗左边缘对齐；设置false时，首页显示空白prevMargin，首页的左边缘与Swiper视窗左边缘的距离为prevMargin。<br/>默认值：false <br/>**说明：**<br/>首页场景下，prevMargin和nextMargin的值相加作为右边边距显示后一个页面。<br>**起始版本：** 12 |

## vertical

```TypeScript
vertical(value: boolean)
```

设置是否为纵向滑动。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperAttribute-vertical(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-vertical(value: boolean): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否为纵向滑动。true为纵向滑动，false为横向滑动。<br/>默认值：false |

