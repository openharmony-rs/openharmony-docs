# Swiper

滑块视图容器，提供子组件滑动轮播显示的能力。适用于轮播图展示、图片浏览、引导页、卡片轮播等场景。
> **说明：**
> - Swiper组件通过内置的PanGesture拖动手势实现滑动轮播效果，将[disableSwipe](arkts-arkui-swiper-attribute.md#disableswipe)属性设为true > 时，会禁用该手势监听，从而阻止滑动操作。 > > - Swiper中复用NodeContainer时，禁止递归流程中子节点更新父节点状态变量。

## 子组件

可以包含子组件。

> **说明：**
> 
> - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和
> [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）。不建议子组件中混用懒加载组件（包括LazyForEach、Repeat
> ）和非懒加载组件，或者子组件中使用多个懒加载组件，否则可能导致懒加载组件预加载能力失效等问题。不建议在组件动画过程中对数据源进行操作，否则会导致布局出现异常。
> 
> - Swiper子组件的visibility属性设置为Visibility.None，且Swiper的displayCount属性设置为'auto'时，对应子组件在
> 视窗内不占位，但不影响导航点个数；visibility属性设置为Visibility.None或者Visibility.Hidden时，对应子组件不显示，但依然会在视窗内占位。
> 
> - 当Swiper子组件设置了offset属性时，会按照子组件的层级进行绘制，层级高的子组件会覆盖层级低的子组件。例如，Swiper包含3个子组件，其中第3个子组件设置了
> offset({ x : 100 })，那么在横向循环滑动中，第3个子组件会覆盖第1个子组件，此时可设置第1个子组件的zIndex属性值大于第3个子组件，使第1个子组件层级
> 高于第3个子组件。
> 
> - 在走焦到用户定义的子节点时，导航点、箭头会由于[焦点样式](../../../ui/arkts-common-events-focus-event.md#焦点样式)修改zIndex的行为被遮挡。
> 
> - 在包含大量子组件的场景中，建议采用懒加载、缓存数据、预加载数据和组件复用等方法，以优化Swiper的性能并减少内存占用。最佳实践请参考
> [优化Swiper组件加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-swiper_high_performance_development_guide)。 &gt;

## Swiper

```TypeScript
Swiper(controller?: SwiperController)
```

创建滑块视图容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [SwiperController](arkts-arkui-swipercontroller-c.md) | 否 | 给组件绑定一个控制器，用来控制组件翻页或者预加载指定子节点。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArrowStyle](arkts-arkui-arrowstyle-i.md) | 左右箭头属性。 |
| [AutoPlayOptions](arkts-arkui-autoplayoptions-i.md) | 自动播放属性。 |
| [CachedCountOptions](arkts-arkui-cachedcountoptions-i.md) | 预加载子组件的配置选项。 |
| [IndicatorIconInfo](arkts-arkui-indicatoriconinfo-i.md) | 为指定的导航点索引设置的图标。 |
| [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | 导航点样式。 |
| [SwiperAnimationEvent](arkts-arkui-swiperanimationevent-i.md) | Swiper组件动画相关信息集合。 |
| [SwiperAutoFill](arkts-arkui-swiperautofill-i.md) | 自适应属性。 |
| [SwiperContentAnimatedTransition](arkts-arkui-swipercontentanimatedtransition-i.md) | Swiper自定义切换动画相关信息。 |
| [SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md) | Swiper自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画视窗内的页面信息，同时，也可以通过调用该对象的finishTransition接口通知Swiper组件页面自定义动画已结束。 |
| [SwiperContentWillScrollResult](arkts-arkui-swipercontentwillscrollresult-i.md) | 滑动的相关信息，主要包括：当前页面对应的index、滑动方向上即将显示的页面index和此次滑动的位移。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ContentDidScrollCallback](arkts-arkui-contentdidscrollcallback-t.md) | Swiper滑动时触发的回调，参数可参考[SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md)中的说明。 |
| [ContentWillScrollCallback](arkts-arkui-contentwillscrollcallback-t.md) | Swiper即将滑动前触发的回调，返回值表示是否允许此次滑动。 |
| [OnSwiperAnimationEndCallback](arkts-arkui-onswiperanimationendcallback-t.md) | 切换动画结束时触发的回调。 |
| [OnSwiperAnimationStartCallback](arkts-arkui-onswiperanimationstartcallback-t.md) | 切换动画开始时触发的回调。 |
| [OnSwiperGestureSwipeCallback](arkts-arkui-onswipergestureswipecallback-t.md) | 在页面跟手滑动过程中，逐帧触发的回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SwiperAnimationMode](arkts-arkui-swiperanimationmode-e.md) | Swiper组件翻页至指定页面的动效模式。 |
| [SwiperDisplayMode](arkts-arkui-swiperdisplaymode-e.md) | Swiper在主轴上的尺寸大小模式枚举。 |
| [SwiperNestedScrollMode](arkts-arkui-swipernestedscrollmode-e.md) | Swiper组件和父组件的嵌套滚动模式枚举。 |

## 示例

从API version 20开始，新增onScrollStateChanged事件。

```TypeScript
// xxx.ets
class MyDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct SwiperExample {
  private swiperController: SwiperController = new SwiperController();
  private data: MyDataSource = new MyDataSource([]);

  aboutToAppear(): void {
    let list: number[] = [];
    for (let i = 1; i <= 10; i++) {
      list.push(i);
    }
    this.data = new MyDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        LazyForEach(this.data, (item: number) => {
          Text(item.toString())
            .width('90%')
            .height(160)
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .cachedCount(2)
      .index(1)
      .autoPlay(true)
      .interval(4000)
      .loop(true)
      .indicatorInteractive(true)
      .duration(1000)
      .itemSpace(5)
      .prevMargin(35)
      .nextMargin(35)
      .indicator( // 设置圆点导航点样式
        new DotIndicator()
          .itemWidth(15)
          .itemHeight(15)
          .selectedItemWidth(15)
          .selectedItemHeight(15)
          .color(Color.Gray)
          .selectedColor(Color.Blue))
      .displayArrow({ // 设置导航点箭头样式
        showBackground: true,
        isSidebarMiddle: true,
        backgroundSize: 24,
        backgroundColor: Color.White,
        arrowSize: 18,
        arrowColor: Color.Blue
      }, false)
      .curve(Curve.Linear)
      .onChange((index: number) => {
        console.info(index.toString());
      })
      .onScrollStateChanged((event: ScrollState) => {
        console.info('event: ' + event);
      })
      .onGestureSwipe((index: number, extraInfo: SwiperAnimationEvent) => {
        console.info('index: ' + index);
        console.info('current offset: ' + extraInfo.currentOffset);
      })
      .onAnimationStart((index: number, targetIndex: number, extraInfo: SwiperAnimationEvent) => {
        console.info('index: ' + index);
        console.info('targetIndex: ' + targetIndex);
        console.info('current offset: ' + extraInfo.currentOffset);
        console.info('target offset: ' + extraInfo.targetOffset);
        console.info('velocity: ' + extraInfo.velocity);
      })
      .onAnimationEnd((index: number, extraInfo: SwiperAnimationEvent) => {
        console.info('index: ' + index);
        console.info('current offset: ' + extraInfo.currentOffset);
      })

      Row({ space: 12 }) {
        Button('showPrevious')
          .onClick(() => {
            this.swiperController.showPrevious();
          })
        Button('showNext')
          .onClick(() => {
            this.swiperController.showNext();
          })
      }.margin(5)
      Row({ space: 5 }) {
        Button('FAST 0')
          .onClick(() => {
            // 控制器：跳转到索引0，使用快速动画模式
            this.swiperController.changeIndex(0, SwiperAnimationMode.FAST_ANIMATION);
          })
        Button('FAST 3')
          .onClick(() => {
            // 控制器：跳转到索引3，使用快速动画模式
            this.swiperController.changeIndex(3, SwiperAnimationMode.FAST_ANIMATION);
          })
        Button('FAST ' + 9)
          .onClick(() => {
            // 控制器：跳转到索引9，使用快速动画模式
            this.swiperController.changeIndex(9, SwiperAnimationMode.FAST_ANIMATION);
          })
      }.margin(5)
    }.width('100%')
    .margin({ top: 5 })
  }
}
```

该示例通过[DigitIndicator](arkts-arkui-digitindicator-c.md)接口，实现了数字指示器的效果和功能。

```TypeScript
// xxx.ets
class MyDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct SwiperExample {
  private swiperController: SwiperController = new SwiperController();
  private data: MyDataSource = new MyDataSource([]);

  aboutToAppear(): void {
    let list: number[] = [];
    for (let i = 1; i <= 10; i++) {
      list.push(i);
    }
    this.data = new MyDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        LazyForEach(this.data, (item: number) => {
          Text(item.toString())
            .width('90%')
            .height(160)
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .cachedCount(2)
      .index(1)
      .autoPlay(true)
      .interval(4000)
      .indicator(Indicator.digit() // 设置数字导航点样式
        .top(200)
        .fontColor(Color.Gray)
        .selectedFontColor(Color.Gray)
        .digitFont({ size: 20, weight: FontWeight.Bold })
        .selectedDigitFont({ size: 20, weight: FontWeight.Normal }))
      .loop(true)
      .duration(1000)
      .itemSpace(0)
      .displayArrow(true, false)

      Row({ space: 12 }) {
        Button('showNext')
          .onClick(() => {
            this.swiperController.showNext();
          })
        Button('showPrevious')
          .onClick(() => {
            this.swiperController.showPrevious();
          })
      }.margin(5)
    }.width('100%')
    .margin({ top: 5 })
  }
}
```

从API version 24开始，新增[CachedCountOptions](#cachedcountoptions24对象说明)参数，通过该参数实现缓存的节点个数和displayCount的按组显示数量解耦。

```TypeScript
// xxx.ets
class MyDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct SwiperExample {
  private swiperController: SwiperController = new SwiperController();
  private data: MyDataSource = new MyDataSource([]);

  aboutToAppear(): void {
    let list: number[] = [];
    for (let i = 1; i <= 10; i++) {
      list.push(i);
    }
    this.data = new MyDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        LazyForEach(this.data, (item: number) => {
          Text(item.toString())
            .width('90%')
            .height(160)
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .displayCount(3, true) // 开启按组翻页：每页显示3个轮播项，且翻页时整组切换
      .cachedCount(1, { independent: true }) // 从API version 24开始，新增CachedCountOptions.independent参数。在显示区域外各缓存一个子节点，和displayCount的按组显示数量解耦
      .autoPlay(true)
      .interval(4000)
      .loop(true)
      .duration(1000)
      .itemSpace(10)
      .indicator( // 设置圆点导航点样式
        new DotIndicator()
          .itemWidth(15)
          .itemHeight(15)
          .selectedItemWidth(15)
          .selectedItemHeight(15)
          .color(Color.Gray)
          .selectedColor(Color.Blue))

      Row({ space: 12 }) {
        Button('showNext')
          .onClick(() => {
            this.swiperController.showNext();
          })
        Button('showPrevious')
          .onClick(() => {
            this.swiperController.showPrevious();
          })
      }.margin(5)
    }.width('100%')
    .margin({ top: 5 })
  }
}
```

该示例通过[customContentTransition](#customcontenttransition12)接口，实现了自定义Swiper页面按组翻页动画效果。

```TypeScript
// EntryAbility.ets
import { Configuration, UIAbility } from '@kit.AbilityKit';
import { i18n } from '@kit.LocalizationKit';
import { CommonUtil } from '../common/CommonUtil';

export default class EntryAbility extends UIAbility {
  onConfigurationUpdate(newConfig: Configuration): void {
    // 监听系统配置变化
    if (newConfig.language) {
      CommonUtil.setIsRTL(i18n.isRTL(newConfig.language));
    }
  }
}
```

```TypeScript
// CommonUtil.ets
export class CommonUtil {
  private static isRTL: boolean = false;

  public static setIsRTL(isRTL: boolean): void {
    CommonUtil.isRTL = isRTL;
  }

  public static getIsRTL(): boolean {
    return CommonUtil.isRTL;
  }
}
```

```TypeScript
// xxx.ets
import { CommonUtil } from '../common/CommonUtil';

@Entry
@Component
struct SwiperCustomAnimationExample {
  private DISPLAY_COUNT: number = 2;
  private MIN_SCALE: number = 0.75;

  @State backgroundColors: Color[] = [Color.Green, Color.Blue, Color.Yellow, Color.Pink, Color.Gray, Color.Orange];
  @State opacityList: number[] = [];
  @State scaleList: number[] = [];
  @State translateList: number[] = [];
  @State zIndexList: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < this.backgroundColors.length; i++) {
      this.opacityList.push(1.0);
      this.scaleList.push(1.0);
      this.translateList.push(0.0);
      this.zIndexList.push(0);
    }
  }

  build() {
    Column() {
      Swiper() {
        ForEach(this.backgroundColors, (backgroundColor: Color, index: number) => {
          Text(index.toString()).width('100%').height('100%').fontSize(50).textAlign(TextAlign.Center)
            .backgroundColor(backgroundColor)
            // 自定义动画变化透明度、缩放页面、抵消系统默认位移、渲染层级等
            .opacity(this.opacityList[index])
            .scale({ x: this.scaleList[index], y: this.scaleList[index] })
            .translate({ x: this.translateList[index] })
            .zIndex(this.zIndexList[index])
        })
      }
      .height(300)
      .indicator(false)
      .displayCount(this.DISPLAY_COUNT, true)
      .customContentTransition({
        // 页面移除视窗时超时1000ms下渲染树
        timeout: 1000,
        // 对视窗内所有页面逐帧回调transition，在回调中修改opacity、scale、translate、zIndex等属性值，实现自定义动画
        transition: (proxy: SwiperContentTransitionProxy) => {
          if (!CommonUtil.getIsRTL()) {
            if (proxy.position <= proxy.index % this.DISPLAY_COUNT || proxy.position >= this.DISPLAY_COUNT + proxy.index % this.DISPLAY_COUNT) {
              // 同组页面往左滑或往右完全滑出视窗外时，重置属性值
              this.opacityList[proxy.index] = 1.0;
              this.scaleList[proxy.index] = 1.0;
              this.translateList[proxy.index] = 0.0;
              this.zIndexList[proxy.index] = 0;
            } else {
              // 同组页面往右滑且未滑出视窗外时，对同组中左右两个页面，逐帧根据position修改属性值，实现两个页面往Swiper中间靠拢并透明缩放的自定义切换动画
              if (proxy.index % this.DISPLAY_COUNT === 0) {
                this.opacityList[proxy.index] = 1 - proxy.position / this.DISPLAY_COUNT;
                this.scaleList[proxy.index] = this.MIN_SCALE + (1 - this.MIN_SCALE) * (1 - proxy.position / this.DISPLAY_COUNT);
                this.translateList[proxy.index] = -proxy.position * proxy.mainAxisLength + (1 - this.scaleList[proxy.index]) * proxy.mainAxisLength / 2.0;
              } else {
                this.opacityList[proxy.index] = 1 - (proxy.position - 1) / this.DISPLAY_COUNT;
                this.scaleList[proxy.index] = this.MIN_SCALE + (1 - this.MIN_SCALE) * (1 - (proxy.position - 1) / this.DISPLAY_COUNT);
                this.translateList[proxy.index] = -(proxy.position - 1) * proxy.mainAxisLength - (1 - this.scaleList[proxy.index]) * proxy.mainAxisLength / 2.0;
              }
              this.zIndexList[proxy.index] = -1;
            }
          } else {
            // 适配镜像
            if (proxy.position >= -proxy.index % this.DISPLAY_COUNT || proxy.position <= -this.DISPLAY_COUNT - proxy.index % this.DISPLAY_COUNT) {
              // 同组页面往右滑或往左完全滑出视窗外时，重置属性值
              this.opacityList[proxy.index] = 1.0;
              this.scaleList[proxy.index] = 1.0;
              this.translateList[proxy.index] = 0.0;
              this.zIndexList[proxy.index] = 0;
            } else {
              // 同组页面往左滑且未滑出视窗外时，对同组中左右两个页面，逐帧根据position修改属性值，实现两个页面往Swiper中间靠拢并透明缩放的自定义切换动画
              if (proxy.index % this.DISPLAY_COUNT === 0) {
                this.opacityList[proxy.index] = 1 + proxy.position / this.DISPLAY_COUNT;
                this.scaleList[proxy.index] = this.MIN_SCALE + (1 - this.MIN_SCALE) * (1 + proxy.position / this.DISPLAY_COUNT);
                this.translateList[proxy.index] = -proxy.position * proxy.mainAxisLength - (1 - this.scaleList[proxy.index]) * proxy.mainAxisLength / 2.0;
              } else {
                this.opacityList[proxy.index] = 1 + (proxy.position + 1) / this.DISPLAY_COUNT;
                this.scaleList[proxy.index] = this.MIN_SCALE + (1 - this.MIN_SCALE) * (1 + (proxy.position + 1) / this.DISPLAY_COUNT);
                this.translateList[proxy.index] = -(proxy.position + 1) * proxy.mainAxisLength + (1 - this.scaleList[proxy.index]) * proxy.mainAxisLength / 2.0;
              }
              this.zIndexList[proxy.index] = -1;
            }
          }
        }
      })
      .onContentDidScroll((selectedIndex: number, index: number, position: number, mainAxisLength: number) => {
        // 监听Swiper页面滑动事件，在该回调中可以实现自定义导航点切换动画等
        console.info('onContentDidScroll selectedIndex: ' + selectedIndex + ', index: ' + index + ', position: ' + position + ', mainAxisLength: ' + mainAxisLength);
      })
    }.width('100%')
  }
}
```

该示例通过DotIndicator接口的[maxDisplayCount](arkts-arkui-dotindicator-c.md#maxdisplaycount)属性，实现了圆点导航点超长显示动画效果。

```TypeScript
class MyDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct Index {
  private swiperController: SwiperController = new SwiperController();
  private data: MyDataSource = new MyDataSource([]);

  aboutToAppear(): void {
    let list: number[] = [];
    for (let i = 1; i <= 15; i++) {
      list.push(i);
    }
    this.data = new MyDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        LazyForEach(this.data, (item: number) => {
          Text(item.toString())
            .width('90%')
            .height(160)
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .cachedCount(2)
      .index(5)
      .autoPlay(true)
      .interval(4000)
      .loop(true)
      .duration(1000)
      .itemSpace(0)
      .indicator( // 设置圆点导航点样式
        new DotIndicator()
          .itemWidth(8)
          .itemHeight(8)
          .selectedItemWidth(16)
          .selectedItemHeight(8)
          .color(Color.Gray)
          .selectedColor(Color.Blue)
          .maxDisplayCount(9)) // 设置导航点最大显示数量为9个
      .displayArrow({ // 设置导航点箭头样式
        showBackground: true,
        isSidebarMiddle: true,
        backgroundSize: 24,
        backgroundColor: Color.White,
        arrowSize: 18,
        arrowColor: Color.Blue
      }, false)
      .curve(Curve.Linear)
      Row({ space: 12 }) {
        Button('showNext')
          .onClick(() => {
            this.swiperController.showNext();
          })
        Button('showPrevious')
          .onClick(() => {
            this.swiperController.showPrevious();
          })
      }.margin(5)
    }.width('100%')
    .margin({ top: 5 })
  }
}
```

该示例通过[preloadItems](#preloaditems18)接口实现了预加载指定子节点。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct SwiperPreloadItems {
  @State currentIndex: number = 1;
  private swiperController: SwiperController = new SwiperController();
  @State arr: string[] = ["0", "1", "2", "3", "4", "5"];

  build() {
    Column() {
      Swiper(this.swiperController) {
        ForEach(this.arr, (item: string) => {
          MyComponent({ txt: item })
        })
      }
      .cachedCount(1, true)
      .width("70%")
      .height("50%")


      Button('preload items: [2, 3]')
        .margin(5)
        .onClick(() => {
          // 预加载index=2和index=3的子节点
          try {
            this.swiperController.preloadItems([2, 3])
              .then(() => {
                console.info('preloadItems [2, 3] success.');
              })
              .catch((error: BusinessError) => {
                console.error(`Failed to preload items [2, 3]. Code: ${error.code}, message: ${error.message}`);
              })
          } catch (error) {
            console.error(`Failed to preload items [2, 3]. Code: ${error.code}, message: ${error.message}`);
          }

        })
    }
    .width("100%")
    .margin(5)
  }
}

@Component
struct MyComponent {
  private txt: string = "";

  aboutToAppear(): void {
    console.info('aboutToAppear txt:' + this.txt);
  }

  aboutToDisappear(): void {
    console.info('aboutToDisappear txt:' + this.txt);
  }

  build() {
    Text(this.txt)
      .textAlign(TextAlign.Center)
      .width('100%')
      .height('100%')
      .backgroundColor(0xAFEEEE)
  }
}
```

该示例通过[onSelected](#onselected18)接口，实现了[Tabs](ts-container-tabs.md)与Swiper联动切换。

```TypeScript
// xxx.ets
class MyDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct TabsSwiperExample {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  private list: number[] = [];
  private tabsController: TabsController = new TabsController();
  private swiperController: SwiperController = new SwiperController();
  private swiperData: MyDataSource = new MyDataSource([]);

  aboutToAppear(): void {
    for (let i = 0; i <= 9; i++) {
      this.list.push(i);
    }
    this.swiperData = new MyDataSource(this.list);
  }

  @Builder tabBuilder(index: number, name: string) {
    Column() {
      Text(name)
        .fontColor(this.currentIndex === index ? this.selectedFontColor : this.fontColor)
        .fontSize(16)
        .fontWeight(this.currentIndex === index ? 500 : 400)
        .lineHeight(22)
        .margin({ top: 17, bottom: 7 })
      Divider()
        .strokeWidth(2)
        .color('#007DFF')
        .opacity(this.currentIndex === index ? 1 : 0)
    }.width('20%')
  }

  build() {
    Column() {
      Tabs({ barPosition: BarPosition.Start, controller: this.tabsController }) {
        ForEach(this.list, (index: number) => {
          TabContent().tabBar(this.tabBuilder(index, '页签 ' + this.list[index]))
        })
      }
      // 点击页签时，同步更新选中索引并切换Swiper到对应页面
      .onTabBarClick((index: number) => {
        this.currentIndex = index;
        this.swiperController.changeIndex(index, true);
      })
      .barMode(BarMode.Scrollable)
      .backgroundColor('#F1F3F5')
      .height(56)
      .width('100%')

      Swiper(this.swiperController) {
        LazyForEach(this.swiperData, (item: number) => {
          Text(item.toString())
            .onAppear(()=>{
              console.info('onAppear ' + item.toString());
            })
            .onDisAppear(()=>{
              console.info('onDisAppear ' + item.toString());
            })
            .width('100%')
            .height('40%')
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .loop(false)
      // 选中/切换轮播项时触发
      .onSelected((index: number) => {
        console.info('onSelected:' + index);
        // 同步选中索引到currentIndex（更新页签选中态）
        this.currentIndex = index;
        // 控制Tabs切换到对应索引页签
        this.tabsController.changeIndex(index);
      })
    }
  }
}
```

该示例通过[onContentWillScroll](arkts-arkui-swiper-attribute.md#oncontentwillscroll)事件实现了单方向的滑动翻页，即只能滑动向前翻页，滑动向后翻页的行为会被拦截。

```TypeScript
// xxx.ets
class MyDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct SwiperExample {
  private swiperController: SwiperController = new SwiperController();
  private data: MyDataSource = new MyDataSource([]);
  private currentIndex: number = 4;

  aboutToAppear(): void {
    let list: number[] = [];
    for (let i = 1; i <= 10; i++) {
      list.push(i);
    }
    this.data = new MyDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        LazyForEach(this.data, (item: number) => {
          Text(item.toString())
            .width('90%')
            .height(160)
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .index(this.currentIndex)
      .loop(false)
      .onChange((index: number) => {
        this.currentIndex = index;
      })
      .onContentWillScroll((result: SwiperContentWillScrollResult) => {
        // result.comingIndex：即将要滑动到的目标索引
        // 拦截逻辑：
        // 1. 若目标索引 > 当前索引：返回false，拦截该滑动行为
        // 2. 若目标索引 < 当前索引：返回true，允许该滑动行为
        if (result.comingIndex > this.currentIndex) {
          return false;
        }
        return true;
      })

      Row({ space: 12 }) {
        Button('showNext')
          .onClick(() => {
            this.swiperController.showNext();
          })
        Button('showPrevious')
          .onClick(() => {
            this.swiperController.showPrevious();
          })
      }.margin(5)
    }.width('100%')
    .margin({ top: 5 })
  }
}
```

该示例通过[bottom](#bottom19)和[space](#space19)接口，实现了圆点导航点与底部间距为0的间距控制以及导航点之间的间距控制。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

// MyDataSource.ets
class MyDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

// SwiperExample.ets
@Entry
@Component
struct SwiperExample {

  @State space: LengthMetrics = LengthMetrics.vp(0);
  @State spacePool: LengthMetrics[] = [LengthMetrics.vp(0), LengthMetrics.px(3), LengthMetrics.vp(10)];
  @State spaceIndex: number = 0;

  @State ignoreSize: boolean = false;
  @State ignoreSizePool: boolean[] = [false, true];
  @State ignoreSizeIndex: number = 0;

  private swiperController1: SwiperController = new SwiperController();
  private data1: MyDataSource = new MyDataSource([]);

  aboutToAppear(): void {
    let list1: number[] = [];
    for (let i = 1; i <= 10; i++) {
      list1.push(i);
    }
    this.data1 = new MyDataSource(list1);
  }

  build() {
    Scroll() {
      Column({ space: 20 }) {
        Swiper(this.swiperController1) {
        LazyForEach(this.data1, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(120)
              .backgroundColor(0xAFEEEE)
              .textAlign(TextAlign.Center)
              .fontSize(30)
        }, (item: number) => item.toString())
        }
        .indicator(new DotIndicator()
          .space(this.space) // 控制导航点之间的间距
          .bottom(LengthMetrics.vp(0), this.ignoreSize) // 控制导航点与Swiper底部的间距
          .itemWidth(15)
          .itemHeight(15)
          .selectedItemWidth(15)
          .selectedItemHeight(15)
          .color(Color.Gray)
          .selectedColor(Color.Blue))
        .displayArrow({
          showBackground: true,
          isSidebarMiddle: true,
          backgroundSize: 24,
          backgroundColor: Color.White,
          arrowSize: 18,
          arrowColor: Color.Blue
        }, false)
        
        Column({ space: 4 }) {
          Button('spaceIndex:' + this.spaceIndex).onClick(() => {
            this.spaceIndex = (this.spaceIndex + 1) % this.spacePool.length;
            this.space = this.spacePool[this.spaceIndex];
          }).margin(10)

          Button('ignoreSizeIndex:' + this.ignoreSizeIndex).onClick(() => {
            this.ignoreSizeIndex = (this.ignoreSizeIndex + 1) % this.ignoreSizePool.length;
            this.ignoreSize = this.ignoreSizePool[this.ignoreSizeIndex];
          }).margin(10)
        }.margin(2)
      }.width('100%')
    }
  }
}
```

从API version 22开始，新增[displayCount](arkts-arkui-swiper-attribute.md#displaycount)接口，用于设置Swiper视窗内元素显示个数。

```TypeScript
class MyDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct SwiperExample {
  private data: MyDataSource = new MyDataSource([]);

  aboutToAppear(): void {
    let list: number[] = [];
    for (let i = 1; i <= 10; i++) {
      list.push(i);
    }
    this.data = new MyDataSource(list);
  }

  build() {
    Column() {
      Swiper() {
        LazyForEach(this.data, (item: number) => {
          Text(item.toString())
            .height(160)
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .width('100%')
      .displayCount({fillType:PresetFillType.BREAKPOINT_SM1MD2LG3}) // 按断点设置视窗内元素显示个数
    }
  }
}
```

从API version 23开始，新增[startFakeDrag](arkts-arkui-swipercontroller-c.md#startfakedrag)接口、[fakeDragBy](arkts-arkui-swipercontroller-c.md#fakedragby)接口、[stopFakeDrag](arkts-arkui-swipercontroller-c.md#stopfakedrag)接口、[isFakeDragging](arkts-arkui-swipercontroller-c.md#isfakedragging)接口，用于实现模拟拖拽。

```TypeScript
// SwiperFakeDragExample.ets
@Entry
@Component
struct SwiperFakeDragExample {
  private swiperController: SwiperController = new SwiperController();
  private baseDisplayX: number = 0;
  private panOption: PanGestureOptions = new PanGestureOptions({ direction: PanDirection.Left | PanDirection.Right });

  build() {
    Scroll() {
      Column({ space: 20 }) {
        Swiper(this.swiperController) {
          Column() {
            Text('可消费拖动事件的内层组件')
              .fontSize(20)
          }
          .justifyContent(FlexAlign.Center)
          .backgroundColor('#D5D5D5')
          .gesture(
            // 内层组件消费了拖拽事件，根据事件信息触发外层Swiper滚动。
            PanGesture(this.panOption)
              .onActionStart((event: GestureEvent) => {
                let ret = this.swiperController.isFakeDragging();
                if (ret) {
                  return;
                }
                ret = this.swiperController.startFakeDrag();
                console.info('startFakeDrag ret = ', ret);
                this.baseDisplayX = event.offsetX;
              })
              .onActionUpdate((event: GestureEvent) => {
                if (event) {
                  let ret = this.swiperController.fakeDragBy(event.offsetX - this.baseDisplayX);
                  console.info('fakeDragBy ret = ', ret);
                  this.baseDisplayX = event.offsetX;
                }
              })
              .onActionEnd((event: GestureEvent) => {
                let ret = this.swiperController.stopFakeDrag();
                console.info('stopFakeDrag ret = ', ret);
              })
          )

          Column()
            .backgroundColor('#E3F8F9')
        }
        .width('90%')
        .height('50%')
      }
      .width('100%')
    }
  }
}
```

从API版本26.0.0开始，新增[indicatorIcon](arkts-arkui-dotindicator-c.md#indicatoricon)接口。

```TypeScript
// swiperIndicatorIcon.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct SwiperIndicatorIconExample {
  private symbolModifier1: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_wifi'));
  @State arr: string[] = ['0', '1'];

  build() {
    Scroll() {
      Column({ space: 20 }) {
        Swiper() {
          ForEach(this.arr, (item: string) => {
            Text(item)
              .textAlign(TextAlign.Center)
              .width('100%')
              .height('100%')
              .backgroundColor(0xAFEEEE)
          })
        }
        .width('90%')
        .height('50%')
        .indicator( // 设置圆点导航点样式
          new DotIndicator()
            .itemWidth(20)
            .itemHeight(20)
            .selectedItemWidth(20)
            .selectedItemHeight(20)
            .indicatorIcon([{ index: 0, icon: this.symbolModifier1 },
              { index: 1, icon: $r('sys.media.ohos_ic_public_albums') }])) // 设置导航点图标
      }
      .width('100%')
    }
  }
}
```
