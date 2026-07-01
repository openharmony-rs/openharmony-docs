# Image (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

Image为图片组件，常用于在应用中显示图片。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[Image](ts-basic-components-image.md)。

## 属性

### analyzerConfig<sup>11+</sup>

ArkTS-Dyn: analyzerConfig(config: ImageAnalyzerConfig)

ArkTS-Sta: analyzerConfig(config: ImageAnalyzerConfig | undefined)

设置AI分析类型，包括主体识别和文字识别功能，默认全部开启。分析类型不支持动态修改。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                          | 必填 | 说明         |
| ------ | --------------------------------------------- | ---- | ------------ |
| config | ArkTS-Dyn: [ImageAnalyzerConfig](ts-image-common.md#imageanalyzerconfig12)<br/>ArkTS-Sta: [ImageAnalyzerConfig](ts-image-common.md#imageanalyzerconfig12) \| undefined | 是   | AI分析类型。设置undefined时，按默认值处理。 |

### edgeAntialiasing<sup>11+</sup>

ArkTS-Dyn: edgeAntialiasing(value: number)

ArkTS-Sta: edgeAntialiasing(value: double | undefined)

设置SVG图源边缘抗锯齿效果，仅对SVG图源生效。取值范围为$(0.333, 1.333]$，有效数字保留小数点后3位。

适用于超低分辨率设备（PPI低于200的设备）的SVG图源的锯齿优化，存在一定的性能影响，请谨慎使用。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型   | 必填 | 说明                                |
| ------ | ------ | ---- | ----------------------------------- |
| value  | ArkTS-Dyn: number<br/>ArkTS-Sta: double \| undefined | 是   | SVG图源边缘抗锯齿效果。<br/>设置undefined时，按默认值处理。<br/>默认值：0.0 |

### pointLight<sup>11+</sup>

ArkTS-Dyn: pointLight(value: PointLightStyle)

ArkTS-Sta: pointLight(value: PointLightStyle | undefined)

设置点光源样式。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明         |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | ArkTS-Dyn: [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle)<br/>ArkTS-Sta: [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) \| undefined | 是   | 点光源样式。设置undefined时，按默认值处理。 |

### enhancedImageQuality<sup>12+</sup>

ArkTS-Dyn: enhancedImageQuality(imageQuality: ResolutionQuality)

ArkTS-Sta: enhancedImageQuality(imageQuality: ResolutionQuality | undefined)

设置增强的图像解码分辨率选项。

该属性不支持 svg、[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)和[DrawableDescriptor](../js-apis-arkui-drawableDescriptor.md#drawabledescriptor) 等非解码图片类型。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                             |
| ------ | --------------------------------------- | ---- | -------------------------------- |
| imageQuality | ArkTS-Dyn: [ResolutionQuality](#resolutionquality12)<br/>ArkTS-Sta: [ResolutionQuality](#resolutionquality12) \| undefined | 是   | 图像解码分辨率质量。<br/>设置undefined时，按默认值处理。<br/>默认值：ResolutionQuality.Low |

## ResolutionQuality<sup>12+</sup>

ArkTS-Dyn: type ResolutionQuality = import('../api/@ohos.multimedia.image').default.ResolutionQuality

ArkTS-Sta: type ResolutionQuality = image.ResolutionQuality;

分辨率质量等级类型。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 类型     | 说明       |
| ------ | ---------- |
| ArkTS-Dyn: import('../api/@ohos.multimedia.image').default.[ResolutionQuality](../../apis-image-kit/js-apis-image-sys.md#resolutionquality12)<br/>ArkTS-Sta: image.[ResolutionQuality](../../apis-image-kit/js-apis-image-sys.md#resolutionquality12) | 分辨率质量等级类型。 |