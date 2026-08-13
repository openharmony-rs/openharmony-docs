# ImageAIOptions

图像AI分析选项。 > **说明：** > > 该特性中的参数types优先级高于[ImageAnalyzerConfig](arkts-na-imagecommon-imageanalyzerconfig-i.md#ImageAnalyzerConfig)中的参数types，两者同时设置时以该特性设置的值为准。 > > 该特性依赖设备能力，且需要和对应组件的enableAnalyzer接口 > （例如Image组件）搭配使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ImageAIOptions--><!--Device-unnamed-export declare interface ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aiController

```TypeScript
aiController?: ImageAnalyzerController | ESValue
```

图像AI分析控制器，需要对应组件的enableAnalyzer接口（例如Image组件的enableAnalyzer 接口）设置为true才能生效。 目前只支持ESValue类型。

**类型：** [ImageAnalyzerController](arkts-na-imagecommon-imageanalyzercontroller-c.md) \| ESValue

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAIOptions-aiController?: ImageAnalyzerController | ESValue--><!--Device-ImageAIOptions-aiController?: ImageAnalyzerController | ESValue-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## types

```TypeScript
types?: ImageAnalyzerType[]
```

图像AI分析类型。

**类型：** [ImageAnalyzerType](arkts-na-imagecommon-imageanalyzertype-e.md)[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageAIOptions-types?: ImageAnalyzerType[]--><!--Device-ImageAIOptions-types?: ImageAnalyzerType[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

