# 文本滑动选择器弹窗 (TextPickerDialog) (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

根据指定的选择范围创建文本选择器，展示在弹窗上。

>  **说明：**
>
> - 该组件从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见[UIContext](../arkts-apis-uicontext-uicontext.md)说明。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[文本滑动选择器弹窗 (TextPickerDialog)](ts-methods-textpicker-dialog.md)。

## TextPickerDialogOptions

文本选择器弹窗的参数继承自[TextPickerOptions](ts-basic-components-textpicker.md#textpickeroptions对象说明)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 |  说明 |
| -------- | -------- | -------- |  -------- |  -------- |
| distortionMode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | 否 | 是 | 设置新材质下弹窗的非线性动画模式。<br/>**默认值：** DistortionMode.DISTORTION_AUTO <br/>**起始版本：** 26.0.0<br/>**系统接口：** 此接口为系统接口。<br/>**模型约束：** 此接口仅可在Stage模型下使用。<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。|
| edgeLightMode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode) | 否 | 是 | 设置新材质下弹窗的流光动画模式。<br/>**默认值：** EdgeLightMode.EDGELIGHT_AUTO <br/>**起始版本：** 26.0.0<br/>**系统接口：** 此接口为系统接口。<br/>**模型约束：** 此接口仅可在Stage模型下使用。<br/>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。 |
