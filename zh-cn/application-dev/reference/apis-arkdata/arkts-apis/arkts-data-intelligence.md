# @ohos.data.intelligence(智慧数据平台)

智慧数据平台（ArkData Intelligence Platform，AIP）提供端侧数据智慧化构建，使应用数据向量化，通过嵌入模型将非结构化的文本、图像等多模态数据，转换成具有语义的向量。适用于智能检索、内容理解、相似度匹配等场 景，帮助开发者解决非结构化数据难以计算和比较的问题，提升应用在推荐系统、智能问答、图像识别等场景下的处理效率和准确性。

**起始版本：** 23

<!--Device-unnamed-declare namespace intelligence--><!--Device-unnamed-declare namespace intelligence-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## 导入模块

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getImageEmbeddingModel(智慧数据平台)](arkts-arkdata-intelligence-getimageembeddingmodel-f.md) | 获取图像嵌入模型。使用Promise异步回调。 |
| [getSupportedCloudModel(智慧数据平台)](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md) | 获取支持的云侧模型信息。使用Promise异步回调。 |
| [getTextEmbeddingModel(智慧数据平台)](arkts-arkdata-intelligence-gettextembeddingmodel-f.md) | 获取文本嵌入模型。使用Promise异步回调。 |
| [splitText(智慧数据平台)](arkts-arkdata-intelligence-splittext-f.md) | 获取文本的分块。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CloudModelInfo(智慧数据平台)](arkts-arkdata-intelligence-cloudmodelinfo-i.md) | 云侧模型的配置信息，在使用云侧文本向量模型时配置，可通过[getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md)接口获取当前设备支持的云侧模型信息。 |
| [ImageEmbedding(智慧数据平台)](arkts-arkdata-intelligence-imageembedding-i.md) | 描述多模态嵌入模型的图像嵌入函数。 下列接口都需先使用[intelligence.getImageEmbeddingModel](arkts-arkdata-intelligence-getimageembeddingmodel-f.md)获取到ImageEmbedding实例，再通过此实例 调用对应接口。 |
| [ModelConfig(智慧数据平台)](arkts-arkdata-intelligence-modelconfig-i.md) | 管理嵌入模型的配置信息。 |
| [SplitConfig(智慧数据平台)](arkts-arkdata-intelligence-splitconfig-i.md) | 管理文本分块的配置信息。 |
| [TextEmbedding(智慧数据平台)](arkts-arkdata-intelligence-textembedding-i.md) | 描述文本嵌入模型的文本嵌入函数。 下列接口都需先使用[intelligence.getTextEmbeddingModel](arkts-arkdata-intelligence-gettextembeddingmodel-f.md)获取到TextEmbedding实例，再通过此实例调用对 应接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ModelVersion(智慧数据平台)](arkts-arkdata-intelligence-modelversion-e.md) | 模型版本枚举。 |
| [NetworkPolicy(智慧数据平台)](arkts-arkdata-intelligence-networkpolicy-e.md) | 下载云侧模型的网络策略枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Image(智慧数据平台)](arkts-arkdata-intelligence-image-t.md) | 表示图片的URI地址，为string类型。 |

