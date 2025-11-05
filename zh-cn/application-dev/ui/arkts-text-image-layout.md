# 图文混排
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

图文混排是指图片与文字混合排列，文字可展示于图片四周。此排列方式能够直观呈现页面信息，增强视觉冲击力，使页面展示效果更加多样化。

## 使用Span和ImageSpan实现图文混排

通过Text组件设置[textVerticalAlign](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#textverticalalign20)属性和ImageSpan设置verticalAlign为ImageSpanAlignment.FOLLOW_PARAGRAPH，实现商品价格优惠信息展示的应用场景。

<!-- @[textImage_component](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/textImageMixedLayout/TextImageComponent.ets) -->


![span_imagespan_composition](figures/span_imagespan_composition.png)

## 使用属性字符串实现图文混排

通过[ImageAttachment](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#imageattachment)添加图片，[TextStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#textstyle)设置多种文本样式，实现商品详情信息展示的应用场景。

<!-- @[textImage_attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/textImageMixedLayout/TextImageAttribute.ets) -->

![styledstring_composition](./figures/styledstring_composition.png)