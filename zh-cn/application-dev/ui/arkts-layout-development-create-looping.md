# 创建轮播 (Swiper)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @jiangdayuan-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


[Swiper](../reference/apis-arkui/arkui-ts/ts-container-swiper.md)组件提供滑动轮播显示的能力。Swiper本身是一个容器组件，当设置了多个子组件后，可以对这些子组件进行轮播显示。通常，在一些应用首页显示推荐的内容时，需要用到轮播显示的能力。

针对复杂页面场景，可以使用 Swiper 组件的预加载机制，利用主线程的空闲时间来提前构建和布局绘制组件，优化滑动体验。<!--Del-->详细指导见[Swiper高性能开发指导](../performance/swiper_optimization.md)。<!--DelEnd-->


## 布局与约束

Swiper作为一个容器组件，如果设置了自身尺寸属性，则在轮播显示过程中均以该尺寸生效。如果自身尺寸属性未被设置，则分两种情况：如果设置了prevMargin或者nextMargin属性，则Swiper自身尺寸会跟随其父组件；如果未设置prevMargin或者nextMargin属性，则会自动根据子组件的大小设置自身的尺寸。


## 循环播放

通过loop属性控制是否循环播放，该属性默认值为true。

当loop为true时，在显示第一页或最后一页时，可以继续往前切换到前一页或者往后切换到后一页。如果loop为false，则在第一页或最后一页时，无法继续向前或者向后切换页面。

- loop为true

<!-- @[loop_with_true](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperLoop.ets) -->

``` TypeScript
  Swiper() {
    Text('0')
      .width('90%')
      .height('100%')
      .backgroundColor(Color.Gray)
      .textAlign(TextAlign.Center)
      .fontSize(30)

    Text('1')
      .width('90%')
      .height('100%')
      .backgroundColor(Color.Green)
      .textAlign(TextAlign.Center)
      .fontSize(30)

    Text('2')
      .width('90%')
      .height('100%')
      .backgroundColor(Color.Pink)
      .textAlign(TextAlign.Center)
      .fontSize(30)
  }
// ···
  .loop(true)
```

![loop_true](figures/loop_true.gif)

- loop为false

<!-- @[loop_with_false](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperLoop.ets) -->

![loop_false](figures/loop_false.gif)


## 自动轮播

Swiper通过设置autoPlay属性，控制是否自动轮播子组件。该属性默认值为false。

autoPlay为true时，会自动切换播放子组件，子组件与子组件之间的播放间隔通过interval属性设置。interval属性默认值为3000，单位毫秒。

<!-- @[autoplay_loop_true](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperAutoPlay.ets) -->

![autoPlay](figures/autoPlay.gif)


## 导航点样式

Swiper提供了默认的导航点样式和导航点箭头样式，导航点默认显示在Swiper下方居中位置，开发者也可以通过indicator属性自定义导航点的位置和样式，导航点箭头默认不显示。

通过indicator属性，开发者可以设置导航点相对于Swiper组件上下左右四个方位的位置，同时也可以设置每个导航点的尺寸、颜色、蒙层和被选中导航点的颜色。

- 导航点使用默认样式

<!-- @[default_navigation_point_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperIndicatorStyle.ets) -->

![indicator](figures/indicator.PNG)

- 自定义导航点样式

选中的导航点，直径设为30vp，且颜色为蓝色；未选中的导航点，直径设为15vp，颜色设为红色。

<!-- @[customize_navigation_point_styles](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperIndicatorStyle.ets) -->

![ind](figures/ind.PNG)

Swiper通过设置[displayArrow](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#displayarrow10)属性，可以控制导航点箭头的大小、位置、颜色，底板的大小及颜色，以及鼠标悬停时是否显示箭头。

- 箭头使用默认样式

<!-- @[default_arrow_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperIndicatorStyle.ets) -->

![arrow1](figures/arrow1.gif)

- 自定义箭头样式

箭头显示在组件两侧，大小为18vp，导航点箭头颜色设为蓝色。

<!-- @[customize_the_arrow_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperIndicatorStyle.ets) -->

![arrow2](figures/arrow2.gif)

## 页面切换方式

Swiper支持手指滑动、点击导航点和通过控制器三种方式切换页面，以下示例展示通过控制器切换页面的方法。

<!-- @[switch_pages](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperPageSwitchMethod.ets) -->

![controll](figures/controll.gif)


## 轮播方向

Swiper支持水平和垂直方向上进行轮播，主要通过vertical属性控制。

当vertical为true时，表示在垂直方向上进行轮播；为false时，表示在水平方向上进行轮播。vertical默认值为false。


- 设置水平方向上轮播。

<!-- @[rotate_horizontally](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperDirection.ets) -->


![截图2](figures/截图2.PNG)


- 设置垂直方向轮播。

<!-- @[rotate_vertically](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperDirection.ets) -->


![截图3](figures/截图3.PNG)


## 每页显示多个子页面

Swiper支持在一个页面内同时显示多个子组件，通过[displayCount](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#displaycount8)属性设置。

<!-- @[each_page_displays_multiple_subpages](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperMultiPage.ets) -->

![two](figures/two.PNG)

## 自定义切换动画

Swiper支持通过[customContentTransition](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#customcontenttransition12)设置自定义切换动画，可以在回调中对视窗内所有页面逐帧设置透明度、缩放比例、位移、渲染层级等属性实现自定义切换动画。

<!-- @[customize_transition_animations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperCustomAnimation.ets) -->

![customAnimation](figures/swiper-custom-animation.gif)

## Swiper与Tabs联动

Swiper选中的元素改变时，会通过onSelected回调事件，将元素的索引值index返回。通过调用tabsController.changeIndex(index)方法来实现Tabs页签的切换。

<!-- @[swiper_tabs_linkage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperAndTabsLinkage.ets) -->
![Swiper与Tabs联动](figures/tabs_swiper.gif)

## 设置圆点导航点间距

针对圆点导航点，可以通过DotIndicator的space属性来设置圆点导航点的间距。

<!-- @[dot_indicator_space](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperIgnoreComponentSize.ets) -->

## 导航点忽略组件大小

当导航点的bottom设为0之后，导航点的底部与Swiper的底部还会有一定间距。如果希望消除该间距，可通过调用bottom(bottom, ignoreSize)属性来进行设置。将ignoreSize 设置为true，即可忽略导航点组件大小，达到消除该间距的目的。

- 圆点导航点忽略组件大小。

<!-- @[dot_indicator_bottom](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperIgnoreComponentSize.ets) -->

- 数字导航点忽略组件大小。

<!-- @[digit_indicator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperDigitIndicatorIgnoreComponentSize.ets) -->

圆点导航点设置间距及忽略组件大小完整示例代码如下：

<!-- @[dot_indicator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperIgnoreComponentSize.ets) -->

![controll](figures/indicator_space.gif)

## 保持可见内容位置不变

Swiper通过设置[maintainVisibleContentPosition](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#maintainvisiblecontentposition20)属性，可在使用LazyForEach懒加载数据时（如通过onDataAdd新增数据），保持当前可见内容位置不变，避免因数据增删导致的视图跳动。该属性默认值为false。

maintainVisibleContentPosition为true时，显示区域上方或前方插入或删除数据时可见内容位置不变。

关于数据[LazyForEach：懒加载](../ui/rendering-control/arkts-rendering-control-lazyforeach.md)的具体使用，可参考数据懒加载章节中的示例。

<!-- @[visible_content_position](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/swiper/SwiperVisibleContentPosition.ets) -->

![controll](figures/maintainVisibleContentPosition_true.gif)

## 相关实例

针对Swiper组件开发，有以下相关实例可供参考：

- [电子相册（ArkTS）（API9）](https://gitcode.com/openharmony/codelabs/tree/master/ETSUI/ElectronicAlbum)

- [Swiper的使用（ArkTS）（API9）](https://gitcode.com/openharmony/codelabs/tree/master/ETSUI/SwiperArkTS)
<!--RP1--><!--RP1End-->