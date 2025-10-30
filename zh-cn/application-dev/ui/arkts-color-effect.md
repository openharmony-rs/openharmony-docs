# 色彩
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


## 色彩

通过颜色渐变接口，可以设置组件的背景颜色渐变效果，实现在两个或多个指定的颜色之间进行平稳的过渡。

| 接口 | 说明 |
| -------- | -------- |
| [linearGradient](../reference/apis-arkui/arkui-ts/ts-universal-attributes-gradient-color.md#lineargradient) | 为当前组件添加线性渐变的颜色渐变效果。 |
| [sweepGradient](../reference/apis-arkui/arkui-ts/ts-universal-attributes-gradient-color.md#sweepgradient) | 为当前组件添加角度渐变的颜色渐变效果。 |
| [radialGradient](../reference/apis-arkui/arkui-ts/ts-universal-attributes-gradient-color.md#radialgradient) | 为当前组件添加径向渐变的颜色渐变效果。 |


## 为组件添加线性渐变效果


  <!-- @[Linear_Gradient_Effect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/GradientEffect/entry/src/main/ets/homePage/LinearGradientEffect.ets) -->
  
  ``` TypeScript
  @Entry
  @Component
  struct LinearGradientDemo {
    build() {
      Grid() {
        GridItem() {
          Column() {
            Text('angle: 180')
              .fontSize(15)
          }
          .width(100)
          .height(100)
          .justifyContent(FlexAlign.Center)
          .borderRadius(10)
          .linearGradient({
            // 0点方向顺时针旋转为正向角度，线性渐变起始角度的默认值为180°
            colors: [
              [0xf56c6c, 0.0], // 颜色断点1的颜色和比重，对应组件在180°方向上的起始位置
              [0xffffff, 1.0],// 颜色断点2的颜色和比重，对应组件在180°方向上的终点位置
            ]
          })
        }
  
        GridItem() {
          Column() {
            Text('angle: 45')
              .fontSize(15)
          }
          .width(100)
          .height(100)
          .justifyContent(FlexAlign.Center)
          .borderRadius(10)
          .linearGradient({
            angle: 45, // 设置颜色渐变起始角度为顺时针方向45°
            colors: [
              [0xf56c6c, 0.0],
              [0xffffff, 1.0],
            ]
          })
        }
  
        GridItem() {
          Column() {
            Text('repeat: true')
              .fontSize(15)
          }
          .width(100)
          .height(100)
          .justifyContent(FlexAlign.Center)
          .borderRadius(10)
          .linearGradient({
            repeating: true, // 在当前组件内0.3到1.0区域内重复0到0.3区域的颜色渐变效果
            colors: [
              [0xf56c6c, 0.0],
              [0xE6A23C, 0.3],
            ]
          })
        }
  
        GridItem() {
          Column() {
            Text('repeat: false')
              .fontSize(15)
          }
          .width(100)
          .height(100)
          .justifyContent(FlexAlign.Center)
          .borderRadius(10)
          .linearGradient({
            colors: [
              [0xf56c6c, 0.0], // repeating默认为false，此时组件内只有0到0.3区域内存在颜色渐变效果
              [0xE6A23C, 0.3],
            ]
          })
        }
      }
      .columnsGap(10)
      .rowsGap(10)
      .columnsTemplate('1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr')
      .width('100%')
      .height('100%')
    }
  }
  ```

![zh-cn_image_0000001641176829](figures/zh-cn_image_0000001641176829.png)


## 为组件添加角度渐变效果


  <!-- @[Direction_Gradient_Effect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/GradientEffect/entry/src/main/ets/homePage/DirectionGradientEffect.ets) -->
![zh-cn_image_0000001641177073](figures/zh-cn_image_0000001641177073.png)


## 为组件添加径向渐变效果


  <!-- @[Radial_Gradient_Effect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/GradientEffect/entry/src/main/ets/homePage/RadialGradientEffect.ets) -->
![zh-cn_image_0000001592904050](figures/zh-cn_image_0000001592904050.png)
