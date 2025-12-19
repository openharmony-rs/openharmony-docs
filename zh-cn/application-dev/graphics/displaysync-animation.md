# 请求动画绘制帧率
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hudi33-->
<!--Designer: @hudi33-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

在应用开发中，[属性动画](../reference/apis-arkui/arkui-ts/ts-animatorproperty.md)和[显式动画](../reference/apis-arkui/arkui-ts/ts-explicit-animation.md)能够使用可选参数[ExpectedFrameRateRange](../reference/apis-arkui/arkui-ts/ts-explicit-animation.md#expectedframeraterange11)，为不同的动画配置不同的期望绘制帧率。

## 请求属性动画的绘制帧率
定义文本组件的属性动画，请求绘制帧率为60，范例如下：
<!-- @[display_sync_property_animation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/PropertyAnimationDisplaySync.ets) -->

``` TypeScript
Text('60')
  // ...
  .animation({
    duration: 1200,
    iterations: 10,
    // ...
    expectedFrameRateRange: {
      expected: 60,
      min: 0,
      max: 120,
    },
  })
```

## 请求显式动画的绘制帧率
定义按钮组件的显式动画，请求绘制帧率为30，范例如下：
<!-- @[display_sync_explicit_animation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/PropertyAnimationDisplaySync.ets) -->

``` TypeScript
Button('Start')
  // ...
  .onClick(() => {
    // ...

    this.uiContext?.animateTo({
      duration: 1200,
      iterations: 10,
      // ...
      expectedFrameRateRange: {
        expected: 30,
        min: 0,
        max: 120,
      },
    }, () => {
      // ...
    })

    // ...
  })
```

<!--RP1-->
## 相关实例

- [DisplaySync (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/DisplaySync)
<!--RP1End-->