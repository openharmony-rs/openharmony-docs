# 帧动画（ohos.animator）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

帧动画具备逐帧回调的特性，便于开发者在每一帧中处理需调整的属性。通过向应用提供onFrame逐帧回调，帧动画使开发者能够在应用的每一帧设置属性值，从而实现组件属性值变化的自然过渡，营造出动画效果。帧动画接口详情可参考[@ohos.animator (动画)](../reference/apis-arkui/js-apis-animator.md)。

与属性动画相比，帧动画能让开发者实时感知动画进程，即时调整UI值，具备事件即时响应和可暂停的优势，但在性能上略逊于属性动画。当属性动画能满足需求时，建议优先采用属性动画接口实现。属性动画接口可参考[实现属性动画](./arkts-attribute-animation-apis.md)。

| 名称 | 实现方式 | 事件响应方式 | 可暂停 | 性能 |
| -------- | -------- | -------- | -------- |-------- |
| 帧动画（ohos.animator） | 开发者可每帧修改UI侧属性值，UI侧属性实时更新 | 实时响应 | 是 | 较差 |
| 属性动画 | UI侧只计算动画最终状态，动画过程为渲染值在改变，UI侧一直为动画最终状态，不感知实时渲染值 | 按最终状态响应 | 否 | 较好 |

如图所示，帧动画在动画过程中即可实时响应，而属性动画按最终状态响应。

![Alt text](figures/ohos.animator.gif)

![Alt text](figures/animation.gif)

## 使用帧动画实现动画效果

使用如下步骤可以创建一个简单的animator，并且在每个帧回调中打印当前插值。

1. 引入相关依赖。

   <!-- @[animator_import_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/AnimatorPage.ets) -->
   
   ``` TypeScript
   import { AnimatorOptions, AnimatorResult } from '@kit.ArkUI';
   ```

2. 创建执行动画的对象。

   <!-- @[animator_options_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/AnimatorPage.ets) -->
   
   ``` TypeScript
   // 创建动画的初始参数
   let options: AnimatorOptions = {
     duration: 1500,
     easing: 'friction',
     delay: 0,
     fill: 'forwards',
     direction: 'normal',
     iterations: 2,
     // 动画onFrame 插值首帧值
     begin: 200.0,
     // 动画onFrame 插值尾帧值
     end: 400.0
   };
   let result: AnimatorResult | undefined = this.getUIContext().createAnimator(options);
   // 设置接收到帧时回调，动画播放过程中每帧会调用onFrame回调
   result.onFrame = (value: number) => {
     hilog.info(DOMAIN, TAG, 'current value is :' + value);
   
   }
   ```

3. 播放动画。

   <!-- @[animator_play_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/AnimatorPage.ets) -->
   
   ``` TypeScript
   // 播放动画
   result.play();
   ```

4. 动画执行完成后手动释放AnimatorResult对象。

   <!-- @[animator_result_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/AnimatorPage.ets) -->
   
   ``` TypeScript
   // 释放动画对象
   result = undefined;
   ```


## 使用帧动画实现小球抛物运动

1. 引入相关依赖。

   <!-- @[animator_template4_import_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/Index.ets) -->

2. 定义要做动画的组件。

   <!-- @[animator_template4_button_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/Index.ets) -->

3. 在onPageShow中创建AnimatorResult对象。

   <!-- @[animator_template4_show_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/Index.ets) -->

4. 定义动画播放，重置，暂停的按钮。

   <!-- @[animator_template4_buttons_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/Index.ets) -->

5. 在页面隐藏或销毁的生命周期中释放动画对象，避免内存泄漏。

   <!-- @[animator_template4_hide_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template4/Index.ets) -->

完整示例如下。

<!-- @[animator_template3_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animator/template3/Index.ets) -->

![zh-cn_image_0000001599958466](figures/animatorSimple.gif)