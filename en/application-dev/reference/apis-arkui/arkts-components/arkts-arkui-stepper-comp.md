# Stepper

The **Stepper** component provides a step navigator, suitable for guiding users through a step-by-step task completion process.

> **NOTE**

## Child Components

Only the child component StepperItem is supported.

## Stepper

```TypeScript
Stepper(value?: { index?: number })
```

Creates a **Stepper** component.

> **NOTE:** 

**Since:** 8

**Deprecated since:** 22

**Substitutes:** index

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { index?: number } | No | Index of the **StepperItem** that is currently displayed.<br>Default value: **0**<br> Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md). |

## Summary

## Examples

### Example 1: Using the Stepper Component

This example demonstrates how to use the Stepper component.



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
      // First step page
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
      // Second step page
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
      // Third step page
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
      // Fourth step page
      StepperItem() {
        Column() {
          Text('Page Four')
            .itemTextStyle()
        }.itemStyle()
      }
    }
    .backgroundColor('#F1F3F5')
    .onFinish(() => {
      // Define the processing logic for when Finish on the last page is clicked, for example, redirection.
      console.info('onFinish');
    })
    .onSkip(() => {
      // Define the processing logic for when Skip on the page is clicked, for example, dynamically changing the index of the Stepper to redirect to a specific step.
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

### Example 2: Using Swiper as a Substitute for Stepper

This example demonstrates how to use the Swiper component to achieve the functionality of the Stepper component. The resulting effect is the same as in Example 1.

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
        // First step page
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
        // Second step page
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
        // Third step page
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
        // Fourth step page
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
        this.nextLabel = this.currentIndex == 2? "Next" : "Next"
        this.prevLabel = this.currentIndex == 2? "Back" : "Previous";
      })
      // Bottom buttons
      Row() {
        if (this.currentIndex > 0) {
          Row() {
            SymbolGlyph($r("sys.symbol.chevron_left"))
              .fontSize(20)
              .margin({ right: 5 })
            Text(this.prevLabel)
            // Use onClick here to replace onPrevious of the original Stepper.
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
            Text("Start")
            // Use onClick here to replace onFinish of the original Stepper.
              .onClick(() => {
                console.info("Finish")
              })
          } else if (this.status == 0) {
            Text(this.nextLabel)
            // Use onClick here to replace onNext of the original Stepper.
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
            Text ("Skip")
            // Use onClick here to replace onSkip of the original Stepper.
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
