# XComponent

提供用于图形绘制和媒体数据写入的Surface，XComponent负责将其嵌入到视图中，支持应用自定义Surface位置和大小。

> **说明：**
>
> 该组件从API Version 8 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[XComponent](ts-basic-components-xcomponent.md)。

## 接口

### XComponentOptions<sup>12+</sup>

定义XComponent的具体配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| screenId<sup>17+</sup> | number | 否 | 是 | 给组件设置关联屏幕ID，通过此项可在组件上显示关联屏幕画面。 **系统接口：** 此接口为系统接口。|

  > **说明：**
  >
  > 仅type为SURFACE时有效。
  >
  > 不支持[ArkUI NDK接口](../../../ui/ndk-build-ui-overview.md)创建的XComponent组件。

## 属性

### hdrBrightness<sup>14+</sup>

hdrBrightness(brightness: number)

用于调整组件播放HDR视频的亮度。

**系统API：** 从API version 14开始，该接口支持在系统中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型    | 必填 | 说明                   |
| -------- | ------- | ---- | ---------------------- |
| brightness | number | 是   | 用于调整组件播放HDR视频的亮度; brightness的取值范围为0.0~1.0; 小于0的值等价于0，大于1的值等价于1; 0 表示SDR视频的亮度，1 表示HDR视频的亮度。|

  > **说明：**
  >
  > 仅type为SURFACE时有效。
  >
  > 不支持[ArkUI NDK接口](../../../ui/ndk-build-ui-overview.md)创建的XComponent组件。

### enableTransparentLayer<sup>18+</sup>

enableTransparentLayer(enabled: boolean)

用于开启XComponent组件背景透明状态下的独立图层。

**系统API：** 从API version 18开始，该接口支持在系统中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型     | 必填 | 说明                   |
| ------- | ------- | ---- | ---------------------- |
| enabled | boolean | 是   | 是否开启组件背景透明状态下的独立图层。<br/>true：开启独立图层；false：关闭独立图层。<br/>默认值：false |

  > **说明：**
  >
  > 仅type为SURFACE时有效。
  >
  > 不支持[ArkUI NDK接口](../../../ui/ndk-build-ui-overview.md)创建的XComponent组件。
