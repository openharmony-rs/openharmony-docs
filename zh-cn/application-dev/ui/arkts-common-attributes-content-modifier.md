# 内容修改器 (ContentModifier)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

当开发者期望自定义组件的内容区时，比如Checkbox的内部显示一个五角星等场景时，可以使用此功能。

仅[Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)、[Checkbox](../reference/apis-arkui/arkui-ts/ts-basic-components-checkbox.md)、[DataPanel](../reference/apis-arkui/arkui-ts/ts-basic-components-datapanel.md)、[TextTimer](../reference/apis-arkui/arkui-ts/ts-basic-components-texttimer.md)、[Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md)、[Select](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md)、[Rating](../reference/apis-arkui/arkui-ts/ts-basic-components-rating.md)、[Radio](../reference/apis-arkui/arkui-ts/ts-basic-components-radio.md)、[Gauge](../reference/apis-arkui/arkui-ts/ts-basic-components-gauge.md)、[Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md)、[TextClock](../reference/apis-arkui/arkui-ts/ts-basic-components-textclock.md)组件支持该能力。

使用ContentModifier自定义Checkbox样式，用五边形Checkbox替换默认Checkbox。选中时，五边形内部显示红色三角图案，标题显示“选中”；取消选中时，红色三角图案消失，标题显示“非选中”。

 <!-- @[checkbox_demo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Modifier/entry/src/main/ets/pages/MyCheckboxStyle.ets) -->

![](figures/common_builder.gif)
