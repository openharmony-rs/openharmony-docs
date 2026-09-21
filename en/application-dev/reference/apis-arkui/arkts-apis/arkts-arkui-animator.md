# @ohos.animator(Animator)

## Modules to Import

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Animator](arkts-arkui-animator-animator-c.md) | Creates an **Animator** object. |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Defines a simple animation parameter object. Unlike **AnimatorOptions**, this object comes with some default values for certain animation parameters, so you do not have to set them manually. |

### Interfaces

| Name | Description |
| --- | --- |
| [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | Animator options. |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Defines the animator result. |

## Examples

### JavaScript-compatible Web-like Development Paradigm

```TypeScript
<!-- hml -->
<div class="container">
  <div class="Animation" style="height: {{divHeight}}px; width: {{divWidth}}px; background-color: red;" onclick="Show">
  </div>
</div>
```



```TypeScript
import { Animator as animator, AnimatorResult, AnimatorOptions } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let DataTmp: Record<string, Animator> = {
  'divWidth': 200,
  'divHeight': 200,
  'animator': animator
}

class Tmp {
  data: animator = DataTmp
  onInit: Function = () => {
  }
  show: Function = () => {
  }
}

class AnimatorState {
  divWidth: number = 0
  divHeight: number = 0
  animator: AnimatorResult | null = null
}

(Fn: (v: Tmp) => void) => {
  Fn({
    data: DataTmp,
    onInit() {
      let options: AnimatorOptions = {
        duration: 1500,
        easing: "friction",
        delay: 0,
        fill: "forwards",
        direction: "normal",
        iterations: 2,
        begin: 200.0,
        end: 400.0
      };
      let animatorState: AnimatorState = {
        divWidth: 200,
        divHeight: 200,
        animator: null
      }
      animatorState.animator = animator.create(options);
    },
    show() {
      let resetOptions: AnimatorOptions = {
        duration: 1500,
        easing: "friction",
        delay: 0,
        fill: "forwards",
        direction: "normal",
        iterations: 2,
        begin: 0,
        end: 400.0,
      };
      let animatorState: AnimatorState = {
        divWidth: 200,
        divHeight: 200,
        animator: null
      }
      try {
        animatorState.animator = animator.create(resetOptions);
        animatorState.animator.reset(resetOptions);
      } catch (error) {
        let message = (error as BusinessError).message
        let code = (error as BusinessError).code
        console.error(`Animator reset failed. Code: ${code}, message: ${message}`);
      }
      let _this = animatorState;
      if (animatorState.animator) {
        animatorState.animator.onFrame = (value: number) => {
          _this.divWidth = value;
          _this.divHeight = value;
        };
        animatorState.animator.play();
      }
    }
  })
}
```

### ArkTS-based Declarative Development Paradigm

> NOTE
> 
> For precise UI context management, use the createAnimator API in [UIContext](arkts-apis-uicontext-uicontext.md) to specify the execution context.



```TypeScript
import { AnimatorResult } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private TAG: string = '[AnimatorTest]'
  private backAnimator: AnimatorResult | undefined = undefined
  private flag: boolean = false
  @State columnWidth: number = 100
  @State columnHeight: number = 100

  create() {
    this.backAnimator = this.getUIContext().createAnimator({
    // You are advised to use the this.getUIContext().createAnimator() API.
      duration: 2000,
      easing: "ease",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 1,
      begin: 100, // Start point of the animation interpolation.
      end: 200 // End point of the animation interpolation.
    })
    this.backAnimator.onFinish = () => {
      this.flag = true;
      console.info(this.TAG, 'backAnimator onFinish');
    }
    this.backAnimator.onRepeat = () => {
      console.info(this.TAG, 'backAnimator repeat');
    }
    this.backAnimator.onCancel = () => {
      console.info(this.TAG, 'backAnimator cancel');
    }
    this.backAnimator.onFrame = (value: number) => {
      this.columnWidth = value;
      this.columnHeight = value;
    }
  }

  aboutToDisappear() {
    // When the custom component disappears, call finish to end incomplete animations and prevent them from continuing.
    // backAnimator references this in onFrame, and this saves backAnimator.
    // set backAnimator stored in the custom component to undefined when the component disappears to avoid memory leak.
    this.backAnimator?.finish();
    this.backAnimator = undefined;
  }

  build() {
    Column() {
      Column() {
        Column()
          .width(this.columnWidth)
          .height(this.columnHeight)
          .backgroundColor(Color.Blue)
      }
      .width('100%')
      .height(300)

      Column() {
        Row() {
          Button('create')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              this.create()
            })
        }
        .padding(10)

        Row() {
          Button('play')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              this.flag = false
              if (this.backAnimator) {
                this.backAnimator.play()
              }
            })
        }
        .padding(10)

        Row() {
          Button('pause')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              if (this.backAnimator) {
                this.backAnimator.pause()
              }
            })
        }
        .padding(10)

        Row() {
          Button('finish')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              this.flag = true
              if (this.backAnimator) {
                this.backAnimator.finish()
              }
            })
        }
        .padding(10)

        Row() {
          Button('reverse')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              this.flag = false
              if (this.backAnimator) {
                this.backAnimator.reverse()
              }
            })
        }
        .padding(10)

        Row() {
          Button('cancel')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              if (this.backAnimator) {
                this.backAnimator.cancel()
              }
            })
        }
        .padding(10)

        Row() {
          Button('reset')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              if (this.flag) {
                this.flag = false
                if (this.backAnimator) {
                  this.backAnimator.reset({
                    duration: 3000,
                    easing: "ease-in",
                    delay: 0,
                    fill: "forwards",
                    direction: "alternate",
                    iterations: 3,
                    begin: 100,
                    end: 300
                  })
                }
              } else {
                console.info(this.TAG, 'Animation not ended')
              }
            })
        }
        .padding(10)
      }
    }
  }
}
```

### Example: Implementing a Translation Animation with Simple Parameters

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private TAG: string = '[AnimatorTest]'
  private backAnimator: AnimatorResult | undefined = undefined
  private flag: boolean = false
  @State translateX: number = 0

  create() {
    this.backAnimator = this.getUIContext()?.createAnimator(
      new SimpleAnimatorOptions(0, 100)
    )
    this.backAnimator.onFinish = () => {
      this.flag = true
      console.info(this.TAG, 'backAnimator onFinish')
    }
    this.backAnimator.onFrame = (value: number) => {
      this.translateX = value
    }
  }

  aboutToDisappear() {
    // When the custom component disappears, call finish to end incomplete animations and prevent them from continuing.
    // backAnimator references this in onFrame, and this saves backAnimator.
    // set backAnimator stored in the custom component to undefined when the component disappears to avoid memory leak.
    this.backAnimator?.finish();
    this.backAnimator = undefined;
  }

  build() {
    Column() {
      Column() {
        Column()
          .width(100)
          .height(100)
          .translate({x: this.translateX})
          .backgroundColor(Color.Green)
      }
      .width('100%')
      .height(300)

      Column() {
        Column() {
          Button('create')
            .fontSize(30)
            .fontColor(Color.White)
            .onClick(() => {
              this.create()
            })
        }
        .padding(10)

        Column() {
          Button('play')
            .fontSize(30)
            .fontColor(Color.White)
            .onClick(() => {
              this.flag = false
              if(this.backAnimator){
                this.backAnimator.play()
              }
            })
        }
        .padding(10)

        Column() {
          Button('reset')
            .fontSize(30)
            .fontColor(Color.White)
            .onClick(() => {
              if (this.flag) {
                this.flag = false
                if(this.backAnimator){
                  this.backAnimator.reset(
                    new SimpleAnimatorOptions(0, -100)
                      .duration(2000)
                      .easing("ease-in")
                      .fill(FillMode.Forwards)
                      .direction(PlayMode.Alternate)
                      .iterations(2)
                  )
                }
              } else {
                console.info(this.TAG, 'Animation not ended')
              }
            })
        }
        .padding(10)
      }
    }
  }
}
```
