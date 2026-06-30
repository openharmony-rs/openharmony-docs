# Video (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @qianpinyi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

用于播放视频文件并控制其播放状态的组件。 

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[Video](ts-media-components-video.md)。

## 属性

### surfaceBackgroundColor<sup>15+</sup>

ArkTS-Dyn: surfaceBackgroundColor(color: ColorMetrics)

ArkTS-Sta: surfaceBackgroundColor(color: ColorMetrics | undefined)

设置Video组件中surfaceNode的背景色。

**系统接口：** 此接口为系统接口

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 |       类型    | 必填 |           说明                |
| ------ | ------------ | ---- | ---------------------------- |
| color  | ArkTS-Dyn: [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)<br/>ArkTS-Sta: [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) \| undefined | 是   | 设置Video组件中surfaceNode的背景色，仅支持黑色和透明色两种。其他颜色设置将默认为黑色。<br/>默认值：Color.Black<br/>取值为undefined时，按默认值处理。 |
