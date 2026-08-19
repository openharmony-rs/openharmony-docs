# CloudModelInfo(智慧数据平台)

云侧模型的配置信息，在使用云侧文本向量模型时配置，可通过[getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md)接口获取当前设备支持的云侧模型信息。

**起始版本：** 26.0.0

<!--Device-intelligence-interface CloudModelInfo--><!--Device-intelligence-interface CloudModelInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## 导入模块

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## modelType

```TypeScript
modelType: string
```

模型类型名称，如"arkdata_text_embedding"表示云侧文本向量模型。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudModelInfo-modelType: string--><!--Device-CloudModelInfo-modelType: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## modelVersionCode

```TypeScript
modelVersionCode?: string
```

模型版本，默认值为空。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudModelInfo-modelVersionCode?: string--><!--Device-CloudModelInfo-modelVersionCode?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

