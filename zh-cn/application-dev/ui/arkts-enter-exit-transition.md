# 出现/消失转场
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


[transition](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md)是基础的组件转场接口，用于实现一个组件出现或者消失时的动画效果。可以通过[TransitionEffect对象](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)的组合使用，定义出各式效果。


  **表1** 转场效果接口

| 转场效果 | 说明 | 动画 |
| -------- | -------- | -------- |
| IDENTITY | 禁用转场效果。 | 无。 |
| OPACITY | 默认的转场效果，透明度转场。 | 出现时透明度从0到1，消失时透明度从1到0。 |
| SLIDE | 滑动转场效果。 | 出现时从窗口左侧滑入，消失时从窗口右侧滑出。 |
| translate | 通过设置组件平移创建转场效果。 | 出现时为translate接口设置的值到默认值0，消失时为默认值0到translate接口设置的值。 |
| rotate | 通过设置组件旋转创建转场效果。 | 出现时为rotate接口设置的值到默认值0，消失时为默认值0到rotate接口设置的值。 |
| opacity | 通过设置透明度参数创建转场效果。 | 出现时为opacity设置的值到默认透明度1，消失时为默认透明度1到opacity设置的值。 |
| move | 通过[TransitionEdge](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitionedge10)创建从窗口哪条边缘出来的效果。 | 出现时从TransitionEdge方向滑入，消失时滑出到TransitionEdge方向。 |
| asymmetric | 通过此方法组合非对称的出现消失转场效果。<br/>- appear:出现转场的效果。<br/>- disappear：消失转场的效果。 | 出现时采用appear设置的TransitionEffect出现效果，消失时采用disappear设置的TransitionEffect消失效果。 |
| combine | 组合其他TransitionEffect。 | 组合其他TransitionEffect，一起生效。 |
| animation | 定义转场效果的动画参数：<br/>-&nbsp;如果不定义会跟随animateTo的动画参数。<br/>-&nbsp;不支持通过控件的animation接口配置动画参数。<br/>-&nbsp;TransitionEffect中animation的onFinish不生效。 | 调用顺序时从上往下，上面TransitionEffect的animation也会作用到下面TransitionEffect。 |


1. 创建TransitionEffect。
  
   <!-- @[transition_animation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/compTransition/template6/Index.ets) -->

2. 将转场效果通过[transition](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md)接口设置到组件。
  
   ```ts
   Text('test')
     .transition(this.effect)
   ```

3. 新增或者删除组件触发转场。
  
   ```ts
   @State isPresent: boolean = true;
   // ...
   if (this.isPresent) {
     Text('test')
       .transition(this.effect)
   }
   // ...
   // 控制新增或者删除组件
   // 方式一：将控制变量放到animateTo闭包内，未通过animation接口定义动画参数的TransitionEffect将跟随animateTo的动画参数
   this.getUIContext()?.animateTo({ curve: curves.springMotion() }, () => {
     this.isPresent = false;
   })
   
   // 方式二：直接控制删除或者新增组件，动画参数由TransitionEffect的animation接口配置
   this.isPresent = false;
   ```


 完整的示例代码和效果如下，示例中采用直接删除或新增组件的方式触发转场，也可以替换为在animateTo闭包内改变控制变量触发转场。

   <!-- @[transition_effectExample4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/compTransition/template4/Index.ets) -->



![zh-cn_image_0000001599818064](figures/zh-cn_image_0000001599818064.gif)


对多个组件添加转场效果时，可以在animation动画参数中配置不同的delay值，实现组件渐次出现消失的效果：

   <!-- @[transition_effectExample5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/compTransition/template5/Index.ets) -->

![zh-cn_image_0000001599818064](figures/zh-cn_image_0000001599818065.gif)