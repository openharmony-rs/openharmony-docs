# @ohos.arkui.dialog (对话框)(系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

提供统一的Dialog类型声明，包含对话框选项、按钮配置、工作表项以及对话框控制器、对齐方式、状态等枚举。具体接口调用请使用UIContext中的[DialogPresenter](arkts-apis-uicontext-dialogpresenter.md)对象。

> **说明：**
>
> 本模块首批接口从API version 26.1.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.arkui.dialog (对话框)](js-apis-dialog.md)。

## 导入模块

```ts
import { dialog } from '@kit.ArkUI';
```

### DialogBaseOptions

所有Dialog类型共享的基本选项，定义对话框的背景、边框、对齐、蒙层、避让等通用属性。本节仅列出系统接口属性，其他公开属性参见[DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称           | 类型                                                         | 只读 | 可选 | 说明                                                         |
| -------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./arkui-ts/ts-appendix-enums-sys.md#distortionmode) | 否   | 是   | 设置对话框的变形动画模式。<br/>默认值：DistortionMode.DISTORTION_AUTO<br/>**系统接口：** 此接口为系统接口。 |
| edgeLightMode  | [EdgeLightMode](./arkui-ts/ts-appendix-enums-sys.md#edgelightmode) | 否   | 是   | 设置对话框的edgeLight动画模式。<br/>默认值：EdgeLightMode.EDGELIGHT_DISABLED<br/>**系统接口：** 此接口为系统接口。 |
