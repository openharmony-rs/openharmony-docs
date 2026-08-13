# @ohos.data.intelligence(智慧数据平台)

/*
 Copyright (c) 2024 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace intelligence--><!--Device-unnamed-declare namespace intelligence-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getImageEmbeddingModel](arkts-arkdata-intelligence-getimageembeddingmodel-f.md#getImageEmbeddingModel) | 获取图像嵌入模型。使用Promise异步回调。 |
| [getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md#getSupportedCloudModel) | 获取支持的云侧模型信息。使用Promise异步回调。 |
| [getTextEmbeddingModel](arkts-arkdata-intelligence-gettextembeddingmodel-f.md#getTextEmbeddingModel) | 获取文本嵌入模型。使用Promise异步回调。 |
| [splitText](arkts-arkdata-intelligence-splittext-f.md#splitText) | 获取文本的分块。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CloudModelInfo](arkts-arkdata-intelligence-cloudmodelinfo-i.md) | 云侧模型的配置信息，在使用云侧文本向量模型时配置，可通过[getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md#getSupportedCloudModel)接口获取当前设备支持的云侧模型信息。 |
| [ImageEmbedding](arkts-arkdata-intelligence-imageembedding-i.md) | 描述多模态嵌入模型的图像嵌入函数。 下列接口都需先使用[intelligence.getImageEmbeddingModel](arkts-arkdata-intelligence-getimageembeddingmodel-f.md#getImageEmbeddingModel)获取到ImageEmbedding实例，再通过此实例 调用对应接口。 |
| [ModelConfig](arkts-arkdata-intelligence-modelconfig-i.md) | 管理嵌入模型的配置信息。 |
| [SplitConfig](arkts-arkdata-intelligence-splitconfig-i.md) | 管理文本分块的配置信息。 |
| [TextEmbedding](arkts-arkdata-intelligence-textembedding-i.md) | 描述文本嵌入模型的文本嵌入函数。 下列接口都需先使用[intelligence.getTextEmbeddingModel](arkts-arkdata-intelligence-gettextembeddingmodel-f.md#getTextEmbeddingModel)获取到TextEmbedding实例，再通过此实例调用对 应接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ModelVersion](arkts-arkdata-intelligence-modelversion-e.md) | 模型版本枚举。 |
| [NetworkPolicy](arkts-arkdata-intelligence-networkpolicy-e.md) | 下载云侧模型的网络策略枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Image](arkts-arkdata-intelligence-image-t.md) | 表示图片的URI地址，为string类型。 |

