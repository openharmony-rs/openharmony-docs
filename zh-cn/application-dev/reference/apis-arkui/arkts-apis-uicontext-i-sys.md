# Interfaces (其他)(系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> 以下API需先使用ohos.window中的[getUIContext()](arkts-apis-window-Window.md#getuicontext10)方法获取UIContext实例，再通过此实例调用对应方法。或者可以通过自定义组件内置方法[getUIContext()](arkui-ts/ts-custom-component-api.md#getuicontext)获取。本文中UIContext对象以uiContext表示。
> 
> 当前页面仅包含本模块的系统接口，其他公开接口参见[Interfaces (其他)](arkts-apis-uicontext-i.md)。

## BackgroundLuminanceSamplingConfigs<sup>23+</sup>

背景取色参数配置。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型 | 只读  | 可选 | 说明                    |
| --------- | ---- | ----- | ---- | -----------------------|
| samplingInterval  | number | 否 | 是 | 取色间隔，单位为毫秒，最小值180ms。<br> 默认值：500   |
| brightThreshold     | number | 否 | 是 | 浅色亮度阈值：[0, 255]内的整数，设置的深色亮度阈值应小于浅色亮度阈值。<br> 默认值：220 |
| darkThreshold     | number | 否 | 是 | 深色亮度阈值：[0, 255]内的整数，设置的深色亮度阈值应小于浅色亮度阈值。<br> 默认值：150 |
| region     | [Edges](./js-apis-arkui-graphics.md#edgest12)\<[LengthMetrics](./js-apis-arkui-graphics.md#lengthmetrics12)\> | 否 | 是 | 相对组件的取色区域偏移，以组件自身的左上点为基准进行偏移计算。<br> 默认使用组件自身区域 |
