# FAQs About Buttons and Selection Components
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

This topic addresses frequently asked questions regarding buttons and selection components.

## How Are the Slider Thumb and Track of the Slider Component Aligned?

The **Slider** component supports three display styles defined by [SliderStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#sliderstyle). Both **SliderStyle.OutSet** and **SliderStyle.InSet** include visible slider thumbs. When the slider progress is at the minimum value, the alignment behavior differs between these two styles:

**SliderStyle.OutSet**: The thumb aligns with the track endpoint.

![OutSet](figures/SliderOutset.jpg)

**SliderStyle.InSet**: The slider thumb aligns with the track centerline (midpoint of the track endpoint height).

![InSet](figures/SliderInset.jpg)

**Example**
```
@Entry
@Component
struct Index {
  build() {
    Column() {
      Slider({
        style: SliderStyle.InSet
      })
        .blockSize({
          width: 20,
          height: 20
        })
        .trackThickness(50)
      Slider({
        style: SliderStyle.InSet
      })
        .blockSize({
          width: 20,
          height: 20
        })
        .trackThickness(50)
    }
    .height('100%')
    .width('100%')
  }
}
```
