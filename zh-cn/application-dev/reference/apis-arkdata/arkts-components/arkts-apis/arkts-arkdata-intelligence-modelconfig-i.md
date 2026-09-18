# ModelConfig

管理嵌入模型的配置信息。

@interface ModelConfig

**起始版本：** 15

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## 导入模块

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## cachePath

```TypeScript
cachePath?: string
```

如果使用NPU进行加速，则需要本地路径进行模型缓存。格式为/xxx/xxx/xxx，xxx为路径地址，例如"/data"。长度上限为512个字符。默认值为""。超出长度时抛出异常。

**类型：** string

**起始版本：** 15

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## isNpuAvailable

```TypeScript
isNpuAvailable: boolean
```

指示是否使用NPU加速向量化过程，true表示使用，false表示不使用。如果设备不支持NPU，调用加载模型会失败，并抛出错误码31300000。

**类型：** boolean

**起始版本：** 15

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## modelInfo

```TypeScript
modelInfo?: CloudModelInfo
```

云侧模型类型和版本信息，在使用文本向量模型时配置，通过[getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md)接口获取支持的模型信息，默认值为空。

**类型：** [CloudModelInfo](arkts-arkdata-intelligence-cloudmodelinfo-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## networkPolicy

```TypeScript
networkPolicy?: NetworkPolicy
```

下载云侧模型时使用的网络策略，默认值为WIFI_ONLY。此参数仅在使用文本嵌入模型时生效，在使用图像嵌入模型场景此参数不生效。

**类型：** [NetworkPolicy](arkts-arkdata-intelligence-networkpolicy-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## version

```TypeScript
version: ModelVersion
```

模型的版本。

**类型：** [ModelVersion](arkts-arkdata-intelligence-modelversion-e.md)

**起始版本：** 15

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core
