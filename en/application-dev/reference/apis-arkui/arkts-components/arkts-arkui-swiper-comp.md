# Swiper

The **Swiper** component is able to display child components in a carousel-like manner.

> **NOTE**

> - The **Swiper** component implements the scrolling carousel effect through the built-in > PanGesture gesture. When the [disableSwipe](arkts-arkui-swiper-comp-attribute.md#disableswipe) attribute is set > to **true**, the gesture listening is disabled, thereby preventing the scrolling operation. > > - When NodeContainer is reused in the **Swiper** component, recursive updates of parent > component state variables by child nodes are prohibited.

## Child Components

Supported

> **NOTE:** 
> 
> - Allowed child component types: built-in and custom components, including rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md),[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)). To maximize the benefits of lazy loading, avoid mixing lazy loading components (including **LazyForEach** and **Repeat**) and non-lazy loading components, and exercise caution when using multiple lazy loading components. Avoid modifying the data source while an animation is in progress, as doing so can lead to layout issues.
> 
> - If a child component has its [visibility](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-visibility.md#visibility) attribute set to **Visibility.None** and the **Swiper** component has its **displayCount** attribute set to **'auto'**, the child component does not take up space in the viewport, but does not affect the number of navigation points. If a child component has its **visibility** attribute set to **Visibility.None** or **Visibility.Hidden**, it takes up space in the viewport, but is not displayed.
> 
> - Child components of the **Swiper** component are drawn based on their level if they have the [offset](arkts-arkui-common-comp-commonmethod-c.md#offset) attribute set. A child component with a higher level overwrites one with a lower level. For example, if the **Swiper** contains three child components and **offset({ x: 100 })** is set for the third child component, the third child component overwrites the first child component during horizontal loop playback. To prevent the first child component from being overwritten, set its [zIndex](arkts-arkui-common-comp-commonmethod-c.md#zindex)attribute to a value greater than that of the third child component.
> 
> - When focus is moved to a custom child node, navigation indicators and arrows may be obscured by [focus styles](../../../ui/arkts-common-events-focus-event.md#focus-style) modifications that change **zIndex**.
> 
> - For a **Swiper** component with many child components, you can optimize the performance and reduce memory consumption by using lazy loading, data caching, preloading, and component reuse techniques. For best practices,see [Optimizing Frame Loss During Swiper Component Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-swiper_high_performance_development_guide). &gt;

## Swiper

```TypeScript
Swiper(controller?: SwiperController)
```

Creates a **Swiper** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [SwiperController](arkts-arkui-swiper-comp-swipercontroller-c.md) | No | Controller to bind to the component to manage page switching and preload specific child components. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ArrowStyle](arkts-arkui-swiper-comp-arrowstyle-i.md) | Describes the left and right arrow attributes. |
| [AutoPlayOptions](arkts-arkui-swiper-comp-autoplayoptions-i.md) | Defines the properties for controlling the automatic playback behavior. |
| [CachedCountOptions](arkts-arkui-swiper-comp-cachedcountoptions-i.md) | Describes the configuration options for child components to be preloaded. |
| [IndicatorIconInfo](arkts-arkui-swiper-comp-indicatoriconinfo-i.md) | Set the indicator item's icon for a specified index. |
| [IndicatorStyle](arkts-arkui-swiper-comp-indicatorstyle-i.md) | Defines the style of the navigation indicator. |
| [SwiperAnimationEvent](arkts-arkui-swiper-comp-swiperanimationevent-i.md) | Describes the animation information of the **Swiper** component. |
| [SwiperAutoFill](arkts-arkui-swiper-comp-swiperautofill-i.md) | Describes the auto-fill attribute. |
| [SwiperContentAnimatedTransition](arkts-arkui-swiper-comp-swipercontentanimatedtransition-i.md) | Provides the information about the custom page transition animation. |
| [SwiperContentTransitionProxy](arkts-arkui-swiper-comp-swipercontenttransitionproxy-i.md) | Implements the proxy object returned during the execution of the custom page transition animation of the **Swiper** component. You can use this object to obtain the page information in the custom animation viewport. You can also call the **finishTransition** API of this object to notify the **Swiper** component that the custom animation has finished playing. |
| [SwiperContentWillScrollResult](arkts-arkui-swiper-comp-swipercontentwillscrollresult-i.md) | Provides information related to the upcoming scroll action, including the index of the current page, the index of the page that will be displayed in the scroll direction, and the displacement of the scroll action. |

### Types

| Name | Description |
| --- | --- |
| [ContentDidScrollCallback](arkts-arkui-swiper-comp-contentdidscrollcallback-t.md) | Triggered during the swipe action of the **Swiper** component. For details about the parameters, see [SwiperContentTransitionProxy](arkts-arkui-swiper-comp-swipercontenttransitionproxy-i.md). |
| [ContentWillScrollCallback](arkts-arkui-swiper-comp-contentwillscrollcallback-t.md) | Defines the callback triggered when the **Swiper** component is about to scroll. The return value indicates whether the scroll action is allowed. |
| [OnSwiperAnimationEndCallback](arkts-arkui-swiper-comp-onswiperanimationendcallback-t.md) | Defines the callback triggered when the page transition animation ends. |
| [OnSwiperAnimationStartCallback](arkts-arkui-swiper-comp-onswiperanimationstartcallback-t.md) | Defines the callback triggered when the page transition animation starts. |
| [OnSwiperGestureSwipeCallback](arkts-arkui-swiper-comp-onswipergestureswipecallback-t.md) | Defines the callback triggered on a frame-by-frame basis when the page is turned by a swipe. |

### Enums

| Name | Description |
| --- | --- |
| [SwiperAnimationMode](arkts-arkui-swiper-comp-swiperanimationmode-e.md) | Enumerates the animation mode for moving to a specific page in the **Swiper** component. |
| [SwiperDisplayMode](arkts-arkui-swiper-comp-swiperdisplaymode-e.md) | Enumerates the modes in which elements are displayed along the main axis. |
| [SwiperNestedScrollMode](arkts-arkui-swiper-comp-swipernestedscrollmode-e.md) | Enumerates the nested scrolling modes of the **Swiper** component and its parent container. |

## Examples

### Example 1: Setting the Navigation Indicator Interaction and Page Turning Effect

In this example, the [changeIndex](#changeindex15) API is used to set the [SwiperAnimationMode](arkts-arkui-swiper-comp-swiperanimationmode-e.md) animation effect to jump to a specified page, and the [onScrollStateChanged](arkts-arkui-swiper-comp-attribute.md#onscrollstatechanged) callback is used to listen for the scrolling state changes.

The onScrollStateChanged event is supported since API version 20.



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
      .indicator ( // Set the dot-style navigation indicator.
        new DotIndicator()
          .itemWidth(15)
          .itemHeight(15)
          .selectedItemWidth(15)
          .selectedItemHeight(15)
          .color(Color.Gray)
          .selectedColor(Color.Blue))
      .displayArrow({ // Set the arrow-style navigation indicator.
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
            // Controller: Jump to index 0 and use the fast animation mode.
            this.swiperController.changeIndex(0, SwiperAnimationMode.FAST_ANIMATION);
          })
        Button('FAST 3')
          .onClick(() => {
            // Controller: Jump to index 3 and use the fast animation mode.
            this.swiperController.changeIndex(3, SwiperAnimationMode.FAST_ANIMATION);
          })
        Button('FAST ' + 9)
          .onClick(() => {
            // Controller: Jump to index 9 and use the fast animation mode.
            this.swiperController.changeIndex(9, SwiperAnimationMode.FAST_ANIMATION);
          })
      }.margin(5)
    }.width('100%')
    .margin({ top: 5 })
  }
}
```

### Example 2: Implementing a Digit Indicator

This example uses the [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) API to implement a digit-style indicator.



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
      .indicator(Indicator.digit() // Set the digit-style navigation indicator.
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

### Example 3: Setting the Page Turning by Group

This example demonstrates how to implement the group-based page turning effect using the [displayCount](arkts-arkui-swiper-comp-attribute.md#displaycount) attribute.

Since API version 24, the [CachedCountOptions](arkts-arkui-swiper-comp-cachedcountoptions-i.md) parameter is added to decouple the number of cached nodes from the number of nodes displayed by group in the displayCount attribute.



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
      .displayCount (3, true) // Enable the function of turning pages by group. Three carousel items are displayed on each page, and the entire group is switched during page turning.
      .cachedCount(1, { independent: true }) // Since API version 24, the CachedCountOptions.independent parameter is added for caching a child node outside the visible content position, which is decoupled from displayCount.
      .autoPlay(true)
      .interval(4000)
      .loop(true)
      .duration(1000)
      .itemSpace(10)
      .indicator ( // Set the dot-style navigation indicator.
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

### Example 4: Customizing the Page Transition Animation

This example presents how to implement a custom page transition animation for the Swiper component through the [customContentTransition](#customcontenttransition12) API.

```TypeScript
// EntryAbility.ets
import { Configuration, UIAbility } from '@kit.AbilityKit';
import { i18n } from '@kit.LocalizationKit';
import { CommonUtil } from '../common/CommonUtil';

export default class EntryAbility extends UIAbility {
  onConfigurationUpdate(newConfig: Configuration): void {
    // Listen for system configuration changes.
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
            // Customize how the opacity, scale, translate, and other properties change during the custom page transition animation.
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
        // The page is removed from the render tree when 1000 ms (timeout time) has elapsed.
        timeout: 1000,
        // Called on a frame-by-frame basis for all pages in the viewport. You can change the values of attributes such as opacity, scale, translate, and zIndex in the callback to implement a custom animation.
        transition: (proxy: SwiperContentTransitionProxy) => {
          if (!CommonUtil.getIsRTL()) {
            if (proxy.position <= proxy.index % this.DISPLAY_COUNT || proxy.position >= this.DISPLAY_COUNT + proxy.index % this.DISPLAY_COUNT) {
              // Reset the attribute values when a page in the same group is swiped left or is swiped right to be completely out of the viewport.
              this.opacityList[proxy.index] = 1.0;
              this.scaleList[proxy.index] = 1.0;
              this.translateList[proxy.index] = 0.0;
              this.zIndexList[proxy.index] = 0;
            } else {
              // When a page in the same group is swiped right but is still within the viewport, the attribute values of the left and right pages in the same group are changed frame by frame based on the position. The changes implement the custom page transition animation in which the two pages move close to the middle of the <Swiper> and are transparently scaled in or out.
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
            // Layout adaptation for right-to-left scripts
            if (proxy.position >= -proxy.index % this.DISPLAY_COUNT || proxy.position <= -this.DISPLAY_COUNT - proxy.index % this.DISPLAY_COUNT) {
              // Reset the properties when a page in the same group is swiped out of the viewport.
              this.opacityList[proxy.index] = 1.0;
              this.scaleList[proxy.index] = 1.0;
              this.translateList[proxy.index] = 0.0;
              this.zIndexList[proxy.index] = 0;
            } else {
              // When a page in the same group is swiped left but is still within the viewport, modify property values frame by frame based on the position for the left and right pages in the group to achieve a custom transition animation where the two pages move toward the center of the Swiper with opacity and scaling effects.
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
        // Listen for Swiper page scroll events. In this callback, you can customize the navigation indicator animation.
        console.info('onContentDidScroll selectedIndex: ' + selectedIndex + ', index: ' + index + ', position: ' + position + ', mainAxisLength: ' + mainAxisLength);
      })
    }.width('100%')
  }
}
```

### Example 5: Configuring Overflow for the Dot-Style Indicator

This example demonstrates how to implement an animation for the overflow effect when the number of navigation dots exceeds the limit set through the [maxDisplayCount](arkts-arkui-swiper-comp-dotindicator-c.md#maxdisplaycount) property of the DotIndicator API.



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
      .indicator ( // Set the dot-style navigation indicator.
        new DotIndicator()
          .itemWidth(8)
          .itemHeight(8)
          .selectedItemWidth(16)
          .selectedItemHeight(8)
          .color(Color.Gray)
          .selectedColor(Color.Blue)
          .maxDisplayCount(9)) // Set the maximum number of navigation indicators to 9.
      .displayArrow({ // Set the arrow-style navigation indicator.
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

### Example 6: Preloading Child Nodes

This example demonstrates how to use the [preloadItems](#preloaditems18) API to preload specified child nodes.

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
          // Preload child nodes with index=2 and index=3.
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

### Example 7: Implementing Synchronized Switching Between the Tabs and Swiper Components

This example associates [Tabs](ts-container-tabs.md) with the Swiper component through the [onSelected](#onselected18) API.



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
          TabContent().tabBar(this.tabBuilder(index, 'Tab ' + this.list[index]))
        })
      }
      // Tap the tab to update the selected index synchronously and switch the Swiper to the corresponding page.
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
      // Triggered when a tab is selected or switched.
      .onSelected((index: number) => {
        console.info('onSelected:' + index);
        // Synchronize the selected index to currentIndex (update the selected tab).
        this.currentIndex = index;
        // Control the Tabs component to switch to the tab with the specified index.
        this.tabsController.changeIndex(index);
      })
    }
  }
}
```

### Example 8: Intercepting the Scrolling Behavior

This example demonstrates how to use the [onContentWillScroll](arkts-arkui-swiper-comp-attribute.md#oncontentwillscroll) event to allow only forward scrolling and intercept backward scrolling.



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
        // result.comingIndex: target index that is about to be swiped to.
        // Interception logic:
        // 1. If the target index is greater than the current index, return false to intercept the scrolling behavior.
        // 2. If the target index is less than the current index, return true to allow the scrolling behavior.
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

### Example 9: Using the space and bottom APIs on the Navigation Indicator

This example uses the [bottom](#bottom19) and [space](#space19) APIs to achieve zero spacing control between the dot-style navigation indicators and the bottom, as well as spacing control between navigation indicators.



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
          .space (this.space) // Control the spacing between navigation indicators.
          .bottom(LengthMetrics.vp(0), this.ignoreSize) // Control the spacing between the navigation indicators and the bottom of the Swiper component.
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

### Example 10: Displaying the Number of Elements Displayed in the Swiper Component Based on Breakpoints

This example demonstrates how to set the number of elements displayed in the Swiper viewport based on breakpoints.

Since API version 22, the [displaycount](arkts-arkui-swiper-comp-attribute.md#displaycount) API is added to set the number of elements displayed in the Swiper viewport.

When the Swiper width falls within the [sm](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) and smaller breakpoint range, one column is displayed.



When the Swiper width falls within the [md](../../../ui/arkts-layout-development-grid-layout.md#breakpoints), two columns are displayed.



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
      .displayCount({fillType:PresetFillType.BREAKPOINT_SM1MD2LG3}) // Set the number of elements to be displayed in a viewport based on breakpoints.
    }
  }
}
```

### Example 11: Implementing Drag Simulation Using the Swiper Component

This example shows how to implement drag simulation using the Swiper component. If the component itself does not respond to the drag event, the child component Column invokes the Swiper API based on the touch event information to implement a similar effect to that of dragging.

Since API version 23, the [startFakeDrag](arkts-arkui-swiper-comp-swipercontroller-c.md#startfakedrag), [fakeDragBy](arkts-arkui-swiper-comp-swipercontroller-c.md#fakedragby), [stopFakeDrag](arkts-arkui-swiper-comp-swipercontroller-c.md#stopfakedrag), and [isFakeDragging](arkts-arkui-swiper-comp-swipercontroller-c.md#isfakedragging) APIs are added to implement drag simulation.



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
            Text('Inner component that can consume the drag event')
              .fontSize(20)
          }
          .justifyContent(FlexAlign.Center)
          .backgroundColor('#D5D5D5')
          .gesture(
            // The inner component consumes the drag event and triggers the outer Swiper scrolling based on the event information.
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

### Example 12: Configuring the Navigation Dot Icon of the Swiper Component

This example shows how to configure the navigation dot icon of the Swiper component by setting the indicatorIcon API.

Since API version 26.0.0, the [indicatorIcon](arkts-arkui-swiper-comp-dotindicator-c.md#indicatoricon) API is added.

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
        .indicator( // Set the dot indicator style.
          new DotIndicator()
            .itemWidth(20)
            .itemHeight(20)
            .selectedItemWidth(20)
            .selectedItemHeight(20)
            .indicatorIcon([{ index: 0, icon: this.symbolModifier1 },
              { index: 1, icon: $r('sys.media.ohos_ic_public_albums') }])) // Set the indicator icon.
      }
      .width('100%')
    }
  }
}
```
