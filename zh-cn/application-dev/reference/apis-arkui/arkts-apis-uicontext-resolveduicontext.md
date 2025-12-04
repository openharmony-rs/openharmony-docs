# Class (ResolvedUIContext)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

ResolvedUIContext实例对象。

> **说明：**
>
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。
> - ResolvedUIContext继承自[UIContext](arkts-apis-uicontext-uicontext.md)，该类对象包含[UIContext](arkts-apis-uicontext-uicontext.md)实例和[UIContext](arkts-apis-uicontext-uicontext.md)的解析策略。

## 属性

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                                                      | 只读 | 可选 | 说明                                |
| --------- | --------------------------------------------------------- | ---- | ---- | ---------------------------------- |
| strategy      | [ResolveStrategy](./arkts-apis-uicontext-e.md#resolvestrategy23) | 否   | 否   | [UIContext](arkts-apis-uicontext-uicontext.md)的解析策略。             |
