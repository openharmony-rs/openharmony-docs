# ArcSwiper

Defines the ArcSwiper Component that can provide the ability for sub components to swipe and display.

## ArcSwiper

```TypeScript
ArcSwiper(controller?: ArcSwiperController)
```

Creates an **ArcSwiper** component.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSwiperInterface-(controller?: ArcSwiperController): ArcSwiperAttribute--><!--Device-ArcSwiperInterface-(controller?: ArcSwiperController): ArcSwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [ArcSwiperController](arkts-arkui-arcswiper-comp-arcswipercontroller-c.md) | No | Controller bound to the component for controlling page swiping. If this parameter is not passed, pages can still be switched by swiping gestures, but the page swiping method cannot be called through the controller. |

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arcswiper-comp-arcdotindicator-c.md) | Describes the properties and behavior of the arc dot navigation indicator. |
| [ArcSwiperController](arkts-arkui-arcswiper-comp-arcswipercontroller-c.md) | Implements the controller of the **ArcSwiper** component. You can bind this object to the **ArcSwiper** component and use it to control page switching. |

### Interfaces

| Name | Description |
| --- | --- |
| [SwiperContentAnimatedTransition](arkts-arkui-arcswiper-comp-swipercontentanimatedtransition-i.md) | Provides the information about the custom page transition animation. |
| [SwiperContentTransitionProxy](arkts-arkui-arcswiper-comp-swipercontenttransitionproxy-i.md) | Implements the proxy object returned during the execution of the custom page transition animation of the **ArcSwiper** component. You can use this object to obtain the page information in the custom animation viewport. You can also call the **finishTransition** API of this object to notify the **ArcSwiper** component that the custom animation has finished playing. |

### Types

| Name | Description |
| --- | --- |
| [AnimationEndHandler](arkts-arkui-arcswiper-comp-animationendhandler-t.md) | Defines the callback triggered when the page transition animation ends. |
| [AnimationStartHandler](arkts-arkui-arcswiper-comp-animationstarthandler-t.md) | Defines the callback triggered when the page transition animation starts. |
| [FinishAnimationHandler](arkts-arkui-arcswiper-comp-finishanimationhandler-t.md) | Defines the callback to notify the application when the animation stops playing. |
| [GestureSwipeHandler](arkts-arkui-arcswiper-comp-gestureswipehandler-t.md) | Defines the callback triggered on a frame-by-frame basis during a swipe-based page turn. |
| [IndexChangedHandler](arkts-arkui-arcswiper-comp-indexchangedhandler-t.md) | Notifies the app when the index of the currently displayed element changes. The index sequence starts from 0. |

### Enums

| Name | Description |
| --- | --- |
| [ArcDirection](arkts-arkui-arcswiper-comp-arcdirection-e.md) | Declare the direction of arc indicator. |

## Examples

### Example 1: Configuring the Basic Attributes of ArcSwiper

This example demonstrates the basic functionality of the component by configuring the basic attributes of ArcSwiper.



```TypeScript
// xxx.ets
import {
  CircleShape,
  ArcSwiper,
  ArcSwiperAttribute, 
  ArcDotIndicator,
  ArcDirection,
  ArcSwiperController
} from '@kit.ArkUI';
// Starting from API version 22, you do not need to manually import ArcSwiperAttribute. For details, refer to the Modules to Import section of the ArcSwiper reference document.

class MyDataSource implements IDataSource {
  private list: Color[] = [];

  constructor(list: Color[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): Color {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct TestNewInterface {
  @State itemSimpleColor: Color | number | string = '';
  @State selectedItemSimpleColor: Color | number | string = '';
  private wearableSwiperController: ArcSwiperController = new ArcSwiperController();
  private arcDotIndicator: ArcDotIndicator = new ArcDotIndicator();
  private data: MyDataSource = new MyDataSource([]);
  @State backgroundColors: Color[] =
    [Color.Green, Color.Blue, Color.Yellow, Color.Pink, Color.White, Color.Gray, Color.Orange, Color.Transparent];
  innerSelectedIndex: number = 0;

  aboutToAppear(): void {
    this.data = new MyDataSource(this.backgroundColors);
  }

  build() {
    Column() {
      Row() {
        ArcSwiper(this.wearableSwiperController) {
          LazyForEach(this.data, (backgroundColor: Color, index: number) => {
            Text(index.toString())
              .width(233)
              .height(233)
              .backgroundColor(backgroundColor)
              .textAlign(TextAlign.Center)
              .fontSize(30)
          })
        }
        .clipShape(new CircleShape({ width: 233, height: 233 }))
        .effectMode(EdgeEffect.None)
        .backgroundColor(Color.Transparent)
        .index(0)
        .duration(400)
        .vertical(false)
        .indicator(this.arcDotIndicator
          .arcDirection(ArcDirection.SIX_CLOCK_DIRECTION)
          .itemColor(this.itemSimpleColor)
          .selectedItemColor(this.selectedItemSimpleColor)
        )
        .disableSwipe(false)
        .digitalCrownSensitivity(CrownSensitivity.MEDIUM)
        .onChange((index: number) => {
          console.info('onChange:' + index.toString());
        })
        .onAnimationStart((index: number, targetIndex: number, extraInfo: SwiperAnimationEvent) => {
          this.innerSelectedIndex = targetIndex;
          console.info('index: ' + index);
          console.info('targetIndex: ' + targetIndex);
          console.info('current offset: ' + extraInfo.currentOffset);
          console.info('target offset: ' + extraInfo.targetOffset);
          console.info('velocity: ' + extraInfo.velocity);
        })
        .onGestureRecognizerJudgeBegin((event: BaseGestureEvent, current: GestureRecognizer,
          others: Array<GestureRecognizer>): GestureJudgeResult => { // When the implementation is about to succeed, set the recognizer enabling state based on the current component state.
          if (current) {
            let target = current.getEventTargetInfo();
            if (target && current.isBuiltIn() && current.getType() == GestureControl.GestureType.PAN_GESTURE) {
              // Check whether the ArcSwiper has scrolled to the beginning: swiperTarget.isBegin() or innerSelectedIndex === 0.
              let swiperTarget = target as ScrollableTargetInfo;
              if (swiperTarget instanceof ScrollableTargetInfo &&
                (swiperTarget.isBegin() || this.innerSelectedIndex === 0)) {
                let panEvent = event as PanGestureEvent;
                if (panEvent && panEvent.offsetX > 0 && (swiperTarget.isBegin() || this.innerSelectedIndex === 0)) {
                  return GestureJudgeResult.REJECT;
                }
              }
            }
          }
          return GestureJudgeResult.CONTINUE;
        })
        .onAnimationEnd((index: number, extraInfo: SwiperAnimationEvent) => {
          console.info('index: ' + index);
          console.info('current offset: ' + extraInfo.currentOffset);
        })
        .disableTransitionAnimation(false)
      }.height('100%')
    }.width('100%')
  }
}
```

### Example 2: Customizing a Page Transition Animation for ArcSwiper

In this example, the [customContentTransition](#customcontenttransition) API is used to define a custom switching animation for the ArcSwiper component.

```TypeScript
import { Decimal } from '@kit.ArkTS';
import { CircleShape, ArcSwiper, ArcSwiperAttribute } from '@kit.ArkUI';

// Starting from API version 22, you do not need to manually import ArcSwiperAttribute. For details, refer to the Modules to Import section of the ArcSwiper reference document.
@Entry
@Component
struct TestNewInterface {
  private backgroundColors: Color[] =
    [Color.Green, Color.Blue, Color.Yellow, Color.Pink, Color.White, Color.Gray, Color.Orange];
  @State scaleList: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < this.backgroundColors.length; i++) {
      this.scaleList.push(1.0);
    }
  }

  build() {
    Column() {
      Row() {
        ArcSwiper() {
          ForEach(this.backgroundColors, (backgroundColor: Color, index: number) => {
            Text(index.toString())
              .width(233)
              .height(233)
              .backgroundColor(backgroundColor)
              .textAlign(TextAlign.Center)
              .fontSize(30)
              .scale({ x: this.scaleList[index], y: this.scaleList[index] })
          })
        }
        .clipShape(new CircleShape({ width: 233, height: 233 }))
        .effectMode(EdgeEffect.None)
        .onChange((index: number) => {
          console.info('onChange:' + index.toString());
        })
        .customContentTransition({
          // The page is removed from the render tree when 1000 ms (timeout time) has elapsed.
          timeout: 1000,
          // Trigger the transition callback frame by frame for all pages within the viewport; modify the scale property value within the callback to implement a custom animation.
          transition: (proxy: SwiperContentTransitionProxy) => {
            if (proxy.position <= -1 || proxy.position >= 1) {
              // When a group of pages is completely scrolled out of the viewport, reset the attribute values.
              this.scaleList[proxy.index] = 1.0;
            } else {
              let position: number = Decimal.abs(proxy.position).toNumber();
              this.scaleList[proxy.index] = 1 - position;
            }
          }
        })
        .disableTransitionAnimation(false)
      }.height('100%')
    }.width('100%')
  }
}
```
