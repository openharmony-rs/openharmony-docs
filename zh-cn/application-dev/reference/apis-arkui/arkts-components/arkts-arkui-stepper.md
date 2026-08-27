# Stepper

步骤导航器组件，适用于引导用户按照步骤完成任务的导航场景。
> **说明：**
> - 从API version 8开始支持，从API version 22开始废弃，建议使用Swiper替代。详细示例请参考 > 示例2。

## 子组件

仅能包含子组件StepperItem。

## Stepper

```TypeScript
Stepper(value?: { index?: number })
```

Called when the stepper component is used.

**起始版本：** 8

**废弃版本：** 22

**替代接口：** index

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { index?: number } | 否 | Index of the **StepperItem** that is currently displayed. Default value: **0**  Since API version 10, this parameter supports two-way binding through [\$\$](../../../ui/state-management/arkts-two-way-sync.md). |

## 汇总

## 示例

该示例主要演示如何使用步骤导航器组件。

```TypeScript
// xxx.ets
@Styles function itemStyle () {
  .width(336)
  .height(621)
  .margin({ top: 48, left: 12 })
  .borderRadius(24)
  .backgroundColor('#FFFFFF')
}

@Extend(Text) function itemTextStyle () {
  .fontColor('#182431')
  .fontSize(36)
  .fontWeight(500)
  .opacity(0.4)
  .margin({ top: 82, bottom: 40 })
}

@Entry
@Component
struct StepperExample {
  @State currentIndex: number = 0;
  @State firstState: ItemState = ItemState.Normal;
  @State secondState: ItemState = ItemState.Normal;
  @State thirdState: ItemState = ItemState.Normal;

  build() {
    Stepper({
      index: this.currentIndex
    }) {
      // 第一个步骤页
      StepperItem() {
        Column() {
          Text('Page One')
            .itemTextStyle()
          Button('change status:' + this.firstState)
            .backgroundColor('#007dFF')
            .onClick(() => {
              this.firstState = this.firstState === ItemState.Skip ? ItemState.Normal : ItemState.Skip;
            })
        }.itemStyle()
      }
      .nextLabel('Next')
      .status(this.firstState)
      // 第二个步骤页
      StepperItem() {
        Column() {
          Text('Page Two')
            .itemTextStyle()
          Button('change status:' + this.secondState)
            .backgroundColor('#007dFF')
            .onClick(() => {
              this.secondState = this.secondState === ItemState.Disabled ? ItemState.Normal : ItemState.Disabled;
            })
        }.itemStyle()
      }
      .nextLabel('Next')
      .prevLabel('Previous')
      .status(this.secondState)
      // 第三个步骤页
      StepperItem() {
        Column() {
          Text('Page Three')
            .itemTextStyle()
          Button('change status:' + this.thirdState)
            .backgroundColor('#007dFF')
            .onClick(() => {
              this.thirdState = this.thirdState === ItemState.Waiting ? ItemState.Normal : ItemState.Waiting;
            })
        }.itemStyle()
      }
      .status(this.thirdState)
      // 第四个步骤页
      StepperItem() {
        Column() {
          Text('Page Four')
            .itemTextStyle()
        }.itemStyle()
      }
    }
    .backgroundColor('#F1F3F5')
    .onFinish(() => {
      // 此处可处理点击最后一页的Finish时的逻辑，例如路由跳转等
      console.info('onFinish');
    })
    .onSkip(() => {
      // 此处可处理点击跳过时的逻辑，例如动态修改Stepper的index值使其跳转到某一步骤页等
      console.info('onSkip');
    })
    .onChange((prevIndex?: number, index?: number) => {
      if(index){
        this.currentIndex = index;
      }
    })
  }
}
```

该示例主要演示如何使用[Swiper](ts-container-swiper.md)组件实现Stepper组件的功能，示例效果图同示例1。

```TypeScript
@Styles
function itemStyle() {
  .width(336)
  .height(621)
  .margin({ top: 48, left: 12 })
  .borderRadius(24)
  .backgroundColor('#FFFFFF')
}

@Extend(Text)
function itemTextStyle() {
  .fontColor('#182431')
  .fontSize(36)
  .fontWeight(500)
  .opacity(0.4)
  .margin({ top: 82, bottom: 40 })
}

@Entry
@Component
struct StepperExample {
  @State currentIndex: number = 0;
  @State status: number = 0;
  @State nextLabel: string = "Next";
  @State prevLabel: string = "Previous";
  private swiperController: SwiperController = new SwiperController();

  build() {
    Column() {
      Swiper(this.swiperController) {
        // 第一个步骤页
        Column() {
          Text('Page One')
            .itemTextStyle()
          Button('change status:' + this.status)
            .backgroundColor('#007dFF')
            .onClick(() => {
              if (this.status < 3) {
                this.status += 1
              } else {
                this.status = 0
              }
            })
        }.itemStyle()
        // 第二个步骤页
        Column() {
          Text('Page Two')
            .itemTextStyle()
          Button('change status:' + this.status)
            .backgroundColor('#007dFF')
            .onClick(() => {
              if (this.status < 3) {
                this.status += 1
              } else {
                this.status = 0
              }
            })
        }.itemStyle()
        // 第三个步骤页
        Column() {
          Text('Page Three')
            .itemTextStyle()
          Button('change status:' + this.status)
            .backgroundColor('#007dFF')
            .onClick(() => {
              if (this.status < 3) {
                this.status += 1
              } else {
                this.status = 0
              }
            })
        }.itemStyle()
        // 第四个步骤页
        Column() {
          Text('Page Four')
            .itemTextStyle()
        }.itemStyle()
      }
      .index(this.currentIndex)
      .disableSwipe(true)
      .loop(false)
      .indicator(false)
      .backgroundColor('#fff5f2f2')
      .onChange((index) => {
        console.info("Changed")
        this.currentIndex = index
        this.nextLabel = this.currentIndex == 2 ? "下一步" : "Next"
        this.prevLabel = this.currentIndex == 2 ? "返回" : "Previous"
      })
      // 底部按钮
      Row() {
        if (this.currentIndex > 0) {
          Row() {
            SymbolGlyph($r("sys.symbol.chevron_left"))
              .fontSize(20)
              .margin({ right: 5 })
            Text(this.prevLabel)
            // 使用这里的onClick替代原Stepper的onPrevious
              .onClick(() => {
                this.swiperController.showPrevious()
              })
          }
          .justifyContent(FlexAlign.Start)
          .width(100)
          .height(20)
          .position({ left: 20 })
        }
        Row() {
          if (this.currentIndex == 3) {
            Text("开始")
            // 使用这里的onClick替代原Stepper的onFinish
              .onClick(() => {
                console.info("Finish")
              })
          } else if (this.status == 0) {
            Text(this.nextLabel)
            // 使用这里的onClick替代原Stepper的onNext
              .onClick(() => {
                this.swiperController.showNext()
              })
            SymbolGlyph($r("sys.symbol.chevron_right"))
              .fontSize(20)
              .margin({ left: 5 })
          } else if (this.status == 1) {
            Text(this.nextLabel)
              .fontColor('#ff818181')
            SymbolGlyph($r("sys.symbol.chevron_right"))
              .fontSize(20)
              .fontColor(['#ff818181'])
              .margin({ left: 5 })
          } else if (this.status == 2) {
            LoadingProgress()
              .width(25)
          } else if (this.status == 3) {
            Text("跳过")
            // 使用这里的onClick替代原Stepper的onSkip
              .onClick(() => {
                console.info("Skip")
              })
            SymbolGlyph($r("sys.symbol.chevron_right"))
              .fontSize(20)
              .margin({ left: 5 })
          }
        }
        .justifyContent(FlexAlign.End)
        .width(100)
        .height(20)
        .position({ right: 20 })
      }
      .backgroundColor('#fff5f2f2')
      .position({ bottom: 30 })
      .width("100%")
    }
    .backgroundColor('#fff5f2f2')
    .width("100%")
    .height("100%")
  }
}
```
