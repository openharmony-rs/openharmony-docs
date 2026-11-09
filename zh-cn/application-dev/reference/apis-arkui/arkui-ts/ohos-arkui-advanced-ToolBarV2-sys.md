# ToolBarV2 (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->

工具栏用于展示针对当前界面内容的操作选项，适用于需要为用户提供快速操作入口的场景。

> **说明：**
>
> - 该组件从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[ToolBarV2](ohos-arkui-advanced-ToolBarV2.md)。

## ToolbarV2StyleOptions

用于构建[ToolbarV2StyleConfigs](ohos-arkui-advanced-ToolBarV2.md#toolbarv2styleconfigs)对象。本页仅说明其中的系统接口字段，其他公开字段参见[ToolbarV2StyleOptions](ohos-arkui-advanced-ToolBarV2.md#toolbarv2styleoptions)。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                   | 类型                                            | 只读 | 可选 | 说明                                                                                                                                      |
| :--------------------- | :---------------------------------------------- | :--- | :--- | :---------------------------------------------------------------------------------------------------------------------------------------- |
| systemBackgroundMaterial | [uiMaterial.Material](../arkts-apis-uimaterial.md#material)  | 否   | 是   | 工具栏背景材质。设置系统样式材质效果，会影响工具栏的backgroundColor、border、shadow等视觉属性。<br />默认值：undefined。<br />值为undefined时，不设置系统材质效果。 |

## ToolbarV2StyleConfigs

工具栏样式配置。本页仅说明其中的系统接口字段，其他公开字段参见[ToolbarV2StyleConfigs](ohos-arkui-advanced-ToolBarV2.md#toolbarv2styleconfigs)。

**起始版本：** 26.1.0

**装饰器类型：** @ObservedV2

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### 属性

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称                   | 类型                                            | 只读 | 可选 | 说明                                                                                                                                      |
| :--------------------- | :---------------------------------------------- | :--- | :--- | :---------------------------------------------------------------------------------------------------------------------------------------- |
| systemBackgroundMaterial | [uiMaterial.Material](../arkts-apis-uimaterial.md#material)  | 否   | 是   | 工具栏背景材质。设置系统样式材质效果，会影响工具栏的backgroundColor、border、shadow等视觉属性。<br />默认值：undefined。<br />值为undefined时，不设置系统材质效果。<br />装饰器类型：@Trace |
