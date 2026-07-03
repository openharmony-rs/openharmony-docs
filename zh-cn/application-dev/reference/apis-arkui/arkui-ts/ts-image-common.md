# 图像类型定义
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

>**说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## PixelMap

ArkTS-Dyn: type PixelMap = import('../api/@ohos.multimedia.image').default.PixelMap

ArkTS-Sta: type PixelMap = image.PixelMap

图像像素类，用于读取或写入图像数据以及获取图像信息。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                                       |
| ------------------------------------------------------------ | ------------------------------------------ |
| ArkTS-Dyn: import('../api/@ohos.multimedia.image').default.[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)<br/>ArkTS-Sta: image.[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) | 图像像素类，用于读取或写入图像数据以及获取图像信息。 |

## ImageAnalyzerConfig<sup>12+</sup>

图像AI分析配置项。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称     | 类型                | 只读 | 可选 | 说明                   |
| ------ | ----------------- | ---- | -------------------- | -------------------- |
| types | [ImageAnalyzerType](#imageanalyzertype12)[] | 否 | 否 | 图像AI分析类型。|

## ImageAnalyzerType<sup>12+</sup>

图像AI分析类型，未设置时默认开启主体识别和文字识别功能。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称     | 值    | 说明           |
| -------- | ----- | -------- |
| SUBJECT | 0  | 主体识别功能。 |
| TEXT | 1  | 文字识别功能。 |
| OBJECT_LOOKUP | 2  | 对象查找功能。 |

## ImageAIOptions<sup>12+</sup>

图像AI分析选项。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称     | 类型                | 只读 | 可选 | 说明                   |
| ------ | ----------------- | ---- | -------------------- | -------------------- |
| types | [ImageAnalyzerType](#imageanalyzertype12)[] | 否 | 是 | 图像AI分析类型。 |
| aiController | ArkTS-Dyn: [ImageAnalyzerController](#imageanalyzercontroller12)<br>ArkTS-Sta: [ImageAnalyzerController](#imageanalyzercontroller12) \| ESValue | 否 | 是 | 图像AI分析控制器，需要对应组件的enableAnalyzer接口（例如Image组件的[enableAnalyzer](ts-basic-components-image.md#enableanalyzer11)接口）设置为true才能生效。<br>ArkTS-Sta：目前只支持ESValue类型。 |

> **说明：**
>
> 该特性中的参数types优先级高于[ImageAnalyzerConfig](#imageanalyzerconfig12)中的参数types，两者同时设置时以该特性设置的值为准。
>
> 该特性依赖设备能力，且需要和对应组件的[enableAnalyzer](ts-basic-components-image.md#enableanalyzer11)接口（例如[Image组件](ts-basic-components-image.md)）搭配使用。

## ImageAnalyzerController<sup>12+</sup>

图像AI分析控制器。可以将此对象绑定至支持的组件，通过控制器来调用支持的方法。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

### constructor<sup>12+</sup>

constructor()

构造函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

### getImageAnalyzerSupportTypes<sup>12+</sup>

getImageAnalyzerSupportTypes(): ImageAnalyzerType[]

获取对应组件支持的AI分析类型。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值:**

| 类型     | 说明                      |
| ------ | ----------------------- |
| [ImageAnalyzerType](#imageanalyzertype12)[] | 对应组件支持的AI分析类型。 |

## ContentTransitionEffect<sup>21+</sup>对象说明

定义内容切换时的过渡效果。

**原子化服务API（仅ArkTS-Dyn）：** 从 API version 21开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 21

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 |说明 |
| -------- | ---------- | -------- | -------- | -------- | 
| IDENTITY | [ContentTransitionEffect](#contenttransitioneffect21对象说明) | 是 | 否 | 内容切换时无过渡动画效果。 |
| OPACITY | [ContentTransitionEffect](#contenttransitioneffect21对象说明) | 是 | 否 | 内容切换时采用淡入淡出过渡动画。 |
