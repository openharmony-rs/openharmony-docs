# Rating

提供在给定范围内选择评分的组件，通常用于商品评价、内容打分等应用场景。
> **说明：**
> - 当Rating的父节点有指定宽高时，需为Rating组件指定宽高，或为父节点设置值为true的clip属性。

## 子组件

无

## 键盘走焦规格

| 按键 | 功能描述 | |------------|-----------------------------| | Tab | 组件间切换焦点。 | | 左右方向键 | 评分预览增加/减少（步长为stepSize），不改变实际分值。 | | Home | 移动到第一个星星， 不改变实际分值。 | | End | 移动到最后一个星星， 不改变实际分值。 | | Space/Enter | 将当前预览的评分值设置为实际评分。 |

## Rating

```TypeScript
Rating(options?: RatingOptions)
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RatingOptions](arkts-arkui-ratingoptions-i.md) | 否 | 设置评分组件。  未设置时，则按照RatingOptions中各参数的默认值配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RatingConfiguration](arkts-arkui-ratingconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [RatingOptions](arkts-arkui-ratingoptions-i.md) | 评分组件的信息。 |
| [StarStyleOptions](arkts-arkui-starstyleoptions-i.md) | 评分组件选中、未选中以及部分选中的星级样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnRatingChangeCallback](arkts-arkui-onratingchangecallback-t.md) | 当评分条的评分变化时触发该回调。 |

## 示例

以下示例展示了如何创建默认星型评分样式。

```TypeScript
// xxx.ets
@Entry
@Component
struct RatingExample {
  @State rating: number = 3.5;

  build() {
    Column() {
      Column() {
        // 创建评分组件，并设置初始评分与可交互模式
        Rating({ rating: this.rating, indicator: false })
          .stars(5)
          .stepSize(0.5)
          .margin({ top: 24 })
          .onChange((value: number) => {
            this.rating = value;
          })
        Text('current score is ' + this.rating)
          .fontSize(16)
          .fontColor('rgba(24,36,49,0.60)')
          .margin({ top: 16 })
      }.width(360).height(113).backgroundColor('#FFFFFF').margin({ top: 68 })

      Row() {
        Image('common/testImage.jpg')
          .width(40)
          .height(40)
          .borderRadius(20)
          .margin({ left: 24 })
        Column() {
          Text('Yue')
            .fontSize(16)
            .fontColor('#182431')
            .fontWeight(500)
          Row() {
            Rating({ rating: 3.5, indicator: false }).margin({ top: 1, right: 8 })
            Text('2021/06/02')
              .fontSize(10)
              .fontColor('#182431')
          }
        }.margin({ left: 12 }).alignItems(HorizontalAlign.Start)

        Text('1st Floor')
          .fontSize(10)
          .fontColor('#182431')
          .position({ x: 295, y: 8 })
      }.width(360).height(56).backgroundColor('#FFFFFF').margin({ top: 64 })
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```

以下示例实现自定义评分条，其中每个圆圈表示0.5分。ratingIndicator为true时，评分条作为指示器使用，不可改变评分。ratingStars用于设置评分总数，ratingStepSize用于设置评分步长。

```TypeScript
// xxx.ets
// 自定义评分样式类，实现ContentModifier接口，用于定制Rating组件内容区
class MyRatingStyle implements ContentModifier<RatingConfiguration> {
  name: string = "";
  style: number = 0;

  constructor(value1: string, value2: number) {
    this.name = value1;
    this.style = value2;
  }

  applyContent(): WrappedBuilder<[RatingConfiguration]> {
    return wrapBuilder(buildRating);
  }
}

@Builder
function buildRating(config: RatingConfiguration) {
  Column() {
    Row() {
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 0.4 ? Color.Black : Color.Red)
        // 非指示器模式下，根据步长触发对应的评分变化
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            if (config.stepSize === 0.5) {
              config.triggerChange(0.5);
              return
            }
            if (config.stepSize === 1.0) {
              config.triggerChange(1);
              return
            }
          }
        }).visibility(config.stars >= 1 ? Visibility.Visible : Visibility.Hidden)
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 0.9 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            config.triggerChange(1);
          }
        }).visibility(config.stars >= 1 ? Visibility.Visible : Visibility.Hidden)
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 1.4 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            if (config.stepSize === 0.5) {
              config.triggerChange(1.5);
              return
            }
            if (config.stepSize === 1.0) {
              config.triggerChange(2);
              return
            }
          }
        }).visibility(config.stars >= 2 ? Visibility.Visible : Visibility.Hidden).margin({ left: 10 })
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 1.9 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            config.triggerChange(2);
          }
        }).visibility(config.stars >= 2 ? Visibility.Visible : Visibility.Hidden)
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 2.4 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            if (config.stepSize === 0.5) {
              config.triggerChange(2.5);
              return
            }
            if (config.stepSize === 1.0) {
              config.triggerChange(3);
              return
            }
          }
        }).visibility(config.stars >= 3 ? Visibility.Visible : Visibility.Hidden).margin({ left: 10 })
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 2.9 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            config.triggerChange(3);
          }
        }).visibility(config.stars >= 3 ? Visibility.Visible : Visibility.Hidden)
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 3.4 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            if (config.stepSize === 0.5) {
              config.triggerChange(3.5);
              return
            }
            if (config.stepSize === 1.0) {
              config.triggerChange(4);
              return
            }
          }
        }).visibility(config.stars >= 4 ? Visibility.Visible : Visibility.Hidden).margin({ left: 10 })
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 3.9 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            config.triggerChange(4);
          }
        }).visibility(config.stars >= 4 ? Visibility.Visible : Visibility.Hidden)
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 4.4 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            if (config.stepSize === 0.5) {
              config.triggerChange(4.5);
              return
            }
            if (config.stepSize === 1.0) {
              config.triggerChange(5);
              return
            }
          }
        }).visibility(config.stars >= 5 ? Visibility.Visible : Visibility.Hidden).margin({ left: 10 })
      Circle({ width: 25, height: 25 })
        .fill(config.rating >= 4.9 ? Color.Black : Color.Red)
        .onClick((event: ClickEvent) => {
          if (!config.indicator) {
            config.triggerChange(5);
          }
        }).visibility(config.stars >= 5 ? Visibility.Visible : Visibility.Hidden)
    }

    Text("分值：" + config.rating)
  }
}

@Entry
@Component
struct RatingExample {
  @State rating: number = 0;
  @State ratingIndicator: boolean = true;
  @State ratingStars: number = 0;
  @State ratingStepSize: number = 0.5;

  build() {
    Row() {
      Column() {
        Rating({
          rating: 0,
          indicator: this.ratingIndicator
        })
          .stepSize(this.ratingStepSize)
          .stars(this.ratingStars)
          .backgroundColor(Color.Transparent)
          .width('100%')
          .height(50)
          .onChange((value: number) => {
            console.info('Rating change is' + value);
            this.rating = value;
          })
          .contentModifier(new MyRatingStyle("hello", 3))
        Button(this.ratingIndicator ? "ratingIndicator : true" : "ratingIndicator : false")
          .onClick((event) => {
            if (this.ratingIndicator) {
              this.ratingIndicator = false;
            } else {
              this.ratingIndicator = true;
            }
          }).margin({ top: 5 })

        Button(this.ratingStars < 5 ? "ratingStars + 1, ratingStars =" + this.ratingStars : "ratingStars最大值为5")
          .onClick((event) => {
            if (this.ratingStars < 5) {
              this.ratingStars += 1;
            }
          }).margin({ top: 5 })

        Button(this.ratingStars > 0 ? "ratingStars - 1, ratingStars =" + this.ratingStars :
          "ratingStars小于等于0时默认等于5")
          .onClick((event) => {
            if (this.ratingStars > 0) {
              this.ratingStars -= 1;
            }
          }).margin({ top: 5 })

        Button(this.ratingStepSize == 0.5 ? "ratingStepSize : 0.5" : "ratingStepSize : 1")
          .onClick((event) => {
            if (this.ratingStepSize == 0.5) {
              this.ratingStepSize = 1;
            } else {
              this.ratingStepSize = 0.5;
            }
          }).margin({ top: 5 })
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
    }
    .height('100%')
  }
}
```

该示例通过Resource资源配置starStyle，实现自定义星级图片链接，API version 20之后推荐使用该方法设置样式。

```TypeScript
// xxx.ets
@Entry
@Component
struct RatingExample {
  @State rating: number = 3.5;

  build() {
    Column() {
      // 创建评分组件，并通过Resource资源设置星级样式
      Rating({ rating: this.rating, indicator: false })
        .stars(5)
        .stepSize(0.5)
        .starStyle({
          // $r('app.media.xxx')需要替换为开发者所需的图像资源文件。
          backgroundUri: $r('app.media.image1'),
          foregroundUri: $r('app.media.image2'),
          secondaryUri: $r('app.media.image3')
        })
        .margin({ top: 24 })
        .onChange((value: number) => {
          this.rating = value;
        })
      Text('current score is ' + this.rating)
        .fontSize(16)
        .fontColor('rgba(24,36,49,0.60)')
        .margin({ top: 16 })
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```

此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2开始，新建工程或者模块时，默认创建的模块不会对非resources目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOptions > resOptions > copyCodeResource > enable设置为true，详见[resOptions](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)中相关介绍。

```TypeScript
// xxx.ets
@Entry
@Component
struct RatingExample {
  @State rating: number = 3.5;

  build() {
    Column() {
      // 创建评分组件，并通过本地图片路径设置星级样式
      Rating({ rating: this.rating, indicator: false })
        .stars(5)
        .stepSize(0.5)
        .starStyle({
          backgroundUri: '/common/image1.png', // common目录与pages同级
          foregroundUri: '/common/image2.png',
          secondaryUri: '/common/image3.png'
        })
        .margin({ top: 24 })
        .onChange((value: number) => {
          this.rating = value;
        })
      Text('current score is ' + this.rating)
        .fontSize(16)
        .fontColor('rgba(24,36,49,0.60)')
        .margin({ top: 16 })
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```
