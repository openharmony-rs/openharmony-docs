# IndicatorComponent

Defines IndicatorComponent.

## IndicatorComponent

```TypeScript
IndicatorComponent(controller?: IndicatorComponentController)
```

Called when a indicator is set.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [IndicatorComponentController](arkts-arkui-indicatorcomponent-comp-indicatorcomponentcontroller-c.md) | 否 | indicator component controller. |

## 汇总

## 示例

### 示例1（圆点单独导航点与Swiper绑定使用）

该示例通过[Swiper](ts-container-swiper.md)组件的[indicator](ts-container-swiper.md#indicator)接口与[IndicatorComponent](#indicatorcomponent)的构造函数绑定同一[IndicatorComponentController](arkts-arkui-indicatorcomponent-comp-indicatorcomponentcontroller-c.md)对象，实现了圆点单独导航点与Swiper的交互。



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

### 示例2（数字单独导航点与Swiper绑定使用）

该示例通过[Swiper](ts-container-swiper.md)组件的[indicator](ts-container-swiper.md#indicator)接口与[IndicatorComponent](#indicatorcomponent)的构造函数绑定同一[IndicatorComponentController](arkts-arkui-indicatorcomponent-comp-indicatorcomponentcontroller-c.md)对象，实现了数字单独导航点与Swiper的交互。

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
