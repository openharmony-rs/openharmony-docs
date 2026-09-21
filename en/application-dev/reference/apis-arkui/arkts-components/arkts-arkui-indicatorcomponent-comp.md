# IndicatorComponent

Defines IndicatorComponent.

## IndicatorComponent

```TypeScript
IndicatorComponent(controller?: IndicatorComponentController)
```

Called when a indicator is set.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [IndicatorComponentController](arkts-arkui-indicatorcomponent-comp-indicatorcomponentcontroller-c.md) | No | indicator component controller. |

## Summary

## Examples

### Example 1: Using a Dot Indicator with a Swiper Component

This example binds the same [IndicatorComponentController](arkts-arkui-indicatorcomponent-comp-indicatorcomponentcontroller-c.md) object to both the [indicator](ts-container-swiper.md#indicator) API of the [Swiper](ts-container-swiper.md) component and the [IndicatorComponent](#indicatorcomponent) constructor, enabling interaction between the dot indicator and the Swiper component.



```TypeScript
@Entry
@Component
struct DotIndicatorDemo {
  private indicatorController: IndicatorComponentController = new IndicatorComponentController();
  private swiperController: SwiperController = new SwiperController();
  @State list: number[] = [];
  aboutToAppear(): void {
    for (let i = 1; i <= 6; i++) {
      this.list.push(i);
    }
  }

  build() {
    Column() {
      Swiper(this.swiperController) {
        ForEach(this.list, (item: number) => {
          Text(item.toString())
            .width('100%')
            .height(160)
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .cachedCount(2)
      .index(0)
      .autoPlay(true)
      .interval(2000)
      .indicator(this.indicatorController)
      .loop(true)
      .duration(1000)
      .itemSpace(0)
      .curve(Curve.Linear)
      .onChange((index: number) => {
        console.info(index.toString());
      })

      IndicatorComponent(this.indicatorController)
        .initialIndex(0)
        .style(
          new DotIndicator()
            .itemWidth(15)
            .itemHeight(15)
            .selectedItemWidth(15)
            .selectedItemHeight(15)
            .color(Color.Gray)
            .selectedColor(Color.Blue))
        .loop(true)
        .count(6)
        .vertical(true)
        .onChange((index: number) => {
          console.info('current index: ' + index);
        })
    }
  }
}
```

### Example 2: Using a Digit Indicator with a Swiper Component

This example binds the same [IndicatorComponentController](arkts-arkui-indicatorcomponent-comp-indicatorcomponentcontroller-c.md) object to both the [indicator](ts-container-swiper.md#indicator) API of the [Swiper](ts-container-swiper.md) component and the [IndicatorComponent](#indicatorcomponent) constructor, enabling interaction between the digit indicator and the Swiper component.

```TypeScript
@Entry
@Component
struct DigitIndicatorDemo {
  private indicatorController: IndicatorComponentController = new IndicatorComponentController();
  private swiperController: SwiperController = new SwiperController();
  @State list: number[] = [];
  aboutToAppear(): void {
    for (let i = 1; i <= 6; i++) {
      this.list.push(i);
    }
  }

  build() {
    Column() {
      Swiper(this.swiperController) {
        ForEach(this.list, (item: number) => {
          Text(item.toString())
            .width('100%')
            .height(160)
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: number) => item.toString())
      }
      .cachedCount(2)
      .index(0)
      .autoPlay(true)
      .interval(2000)
      .indicator(this.indicatorController)
      .loop(true)
      .duration(1000)
      .itemSpace(0)
      .curve(Curve.Linear)
      .onChange((index: number) => {
        console.info(index.toString());
      })

      IndicatorComponent(this.indicatorController)
        .initialIndex(0)
        .style(Indicator.digit()
          .fontColor(Color.Gray)
          .selectedFontColor(Color.Gray)
          .digitFont({ size: 20, weight: FontWeight.Bold })
          .selectedDigitFont({ size: 20, weight: FontWeight.Normal }))
        .loop(true)
        .count(6)
        .vertical(true)
        .onChange((index: number) => {
          console.info('current index: ' + index);
        })
    }
  }
}
```
