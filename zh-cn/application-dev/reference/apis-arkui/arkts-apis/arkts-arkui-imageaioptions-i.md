# ImageAIOptions

图像AI分析选项。

> **说明：**  
>  
> 该特性中的参数types优先级高于[ImageAnalyzerConfig](arkts-arkui-imageanalyzerconfig-i.md)中的参数types，两者同时设置时以该特性设置的值为准。  
>  
> 该特性依赖设备能力，且需要和对应组件的[enableAnalyzer](ImageAttribute#enableAnalyzer)接口  
> （例如[Image组件](./image)）搭配使用。

**起始版本：** 12

<!--Device-unnamed-declare interface ImageAIOptions--><!--Device-unnamed-declare interface ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aiController

```TypeScript
aiController?: ImageAnalyzerController
```

图像AI分析控制器。

**类型：** ImageAnalyzerController

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAIOptions-aiController?: ImageAnalyzerController--><!--Device-ImageAIOptions-aiController?: ImageAnalyzerController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## types

```TypeScript
types?: ImageAnalyzerType[]
```

图像AI分析类型。

**类型：** ImageAnalyzerType[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAIOptions-types?: ImageAnalyzerType[]--><!--Device-ImageAIOptions-types?: ImageAnalyzerType[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

