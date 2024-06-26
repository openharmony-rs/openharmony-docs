# Show/Hide Event

The show/hide event is triggered when a component is mounted or unmounted from the component tree. A component appears when mounted to the component tree and disappears when unmounted from the component tree.

> **NOTE**
>
> The APIs of this module are supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.

## onAppear

onAppear(event: () => void): T

Triggered when the component is displayed.

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

**Widget capability**: Since API version 9, this feature is supported in ArkTS widgets.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## onDisAppear

onDisAppear(event: () => void): T

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

Triggered when the component is hidden.

**Widget capability**: Since API version 9, this feature is supported in ArkTS widgets.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


## Example

```ts
// xxx.ets
import promptAction from '@ohos.promptAction'

@Entry
@Component
struct AppearExample {
  @State isShow: boolean = true
  @State changeAppear: string = 'Show/Hide'
  private myText: string = 'Text for onAppear'

  build() {
    Column() {
      Button(this.changeAppear)
        .onClick(() => {
          this.isShow = !this.isShow
        }).margin(15)
      if (this.isShow) {
        Text(this.myText).fontSize(26).fontWeight(FontWeight.Bold)
          .onAppear(() => {
            promptAction.showToast({
              message: 'Text shown.',
              duration: 2000
            })
          })
          .onDisAppear(() => {
            promptAction.showToast({
              message: 'Text hidden.',
              duration: 2000
            })
          })
      }
    }.padding(30).width('100%')
  }
}
```

![en-us_image_0000001219864151](figures/en-us_image_0000001219864151.gif)
