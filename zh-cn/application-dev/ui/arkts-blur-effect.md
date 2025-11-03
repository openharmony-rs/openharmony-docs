# 模糊
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

动画效果可以丰富界面的细节，提升UI界面的真实感和品质感。例如，模糊和阴影效果可以让物体看起来更加立体，使得动画更加生动。ArkUI提供了丰富的效果接口，开发者可快速打造出精致、个性化的效果。本章中主要对常用的模糊、阴影和色彩效果等接口进行了介绍。


模糊可以用来体现界面空间的纵深感，区分前后元素的层级关系。


| 接口                                                         | 说明                                         |
| ------------------------------------------------------------ | -------------------------------------------- |
| [backdropBlur](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backdropblur) | 为当前组件添加背景模糊效果，入参为模糊半径。 |
| [blur](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#blur) | 为当前组件添加内容模糊效果，入参为模糊半径。 |
| [backgroundBlurStyle](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundblurstyle9) | 为当前组件添加背景模糊效果，入参为模糊样式。 |
| [foregroundBlurStyle](../reference/apis-arkui/arkui-ts/ts-universal-attributes-foreground-blur-style.md#foregroundblurstyle) | 为当前组件添加内容模糊效果，入参为模糊样式。 |
| [motionBlur](../reference/apis-arkui/arkui-ts/ts-universal-attributes-motionBlur.md#motionblur) | 为当前组件添加由缩放大小或位移变化引起的运动过程中的动态模糊效果，入参为模糊半径和锚点坐标。 |

>  **说明：**
>
>  以上接口均为实时模糊接口，每帧执行实时渲染，性能负载较大。当模糊内容与模糊半径均无需变动时，推荐采用静态模糊接口[blur](../reference/apis-arkgraphics2d/js-apis-effectKit.md#blur)。最佳实践请参考：[图像模糊动效优化-使用场景](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-fuzzy-scene-performance-optimization#section4945532519)。

## 使用backdropBlur为组件添加背景模糊

<!-- @[animationBlur_template1_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animationBlur/template1/BlurEffectsExample.ets) -->


![zh-cn_image_0000001599812870](figures/zh-cn_image_0000001599812870.png)


## 使用blur为组件添加内容模糊

<!-- @[animationBlur_template2_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animationBlur/template2/Index.ets) -->


![zh-cn_image_0000001599813588](figures/zh-cn_image_0000001599813588.gif)


## 使用backgroundBlurStyle为组件添加背景模糊效果

<!-- @[animationBlur_template3_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animationBlur/template3/BackDropBlurStyleDemo.ets) -->


![zh-cn_image_0000001649455517](figures/zh-cn_image_0000001649455517.png)



## 使用foregroundBlurStyle为组件添加内容模糊效果

<!-- @[animationBlur_template4_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animationBlur/template4/ForegroundBlurStyleDemo.ets) -->


![zh-cn_image_0000001599658168](figures/zh-cn_image_0000001599658168.png)


## 使用motionBlur为组件添加运动模糊效果

<!-- @[animationBlur_template5_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animationBlur/template5/MotionBlurTest.ets) -->



![motionBlurTest](figures/motionBlur.gif)