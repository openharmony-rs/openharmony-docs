# @ohos.arkui.dialog (弹出框)(系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

弹出框是应用与用户交互的重要方式之一，用于在关键操作场景中向用户展示提示信息、获取用户确认或选择。该模块提供统一的`Dialog`类型声明，包含弹出框选项、按钮配置、工作表项以及弹出框控制器、对齐方式、状态等枚举。具体接口调用请使用`UIContext`中的[DialogPresenter](arkts-apis-uicontext-dialogpresenter.md)对象。

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.arkui.dialog (弹出框)](js-apis-dialog.md)。

**起始版本：** 26.1.0

## 导入模块

```ts
import { dialog } from '@kit.ArkUI';
```

## DialogBaseOptions

所有弹出框共享的基本选项，定义弹出框的背景、边框、对齐、蒙层、避让等通用属性。本节仅列出系统接口属性，其他公开属性参见[DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称           | 类型                                                         | 只读 | 可选 | 说明                                                         |
| -------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./arkui-ts/ts-appendix-enums-sys.md#distortionmode) | 否   | 是   | 设置系统材质下弹出框的非线性动画模式。<br/>默认值：DistortionMode.DISTORTION_AUTO<br/>**系统接口：** 此接口为系统接口。 |
| edgeLightMode  | [EdgeLightMode](./arkui-ts/ts-appendix-enums-sys.md#edgelightmode) | 否   | 是   | 设置系统材质下弹出框的流光动画模式。<br/>默认值：EdgeLightMode.EDGELIGHT_AUTO<br/>**系统接口：** 此接口为系统接口。 |

