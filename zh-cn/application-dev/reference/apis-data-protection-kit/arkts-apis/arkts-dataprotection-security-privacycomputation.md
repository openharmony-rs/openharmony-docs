# @ohos.security.privacyComputation(Declares the APIs for privacy-preserving computation, including privacy target generation,)

privateComputation的命名空间，提供隐私保护的计算能力。如隐私目标生成、隐私搜索、搜索结果检索等。

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [genPrivacyTarget](arkts-dataprotection-privacycomputation-genprivacytarget-f.md) | 为给定元素生成隐私目标。隐私目标是加密的表示的搜索元素，可以用于保护隐私的搜索，而不会泄露原始数据。 |
| [getSearchResult](arkts-dataprotection-privacycomputation-getsearchresult-f.md) | 获取隐私搜索结果和最终搜索结果。解密搜索结果密文privateSearch返回，获取最终匹配结果和可选的附加值。 |
| [privacySearch](arkts-dataprotection-privacycomputation-privacysearch-f.md) | 执行隐私保护搜索。根据加密的隐私目标搜索给定的数据集元素而不向对方透露目标或数据集内容。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Element](arkts-dataprotection-privacycomputation-element-i.md) | 定义隐私搜索使用的数据集元素。每个元素包含一个用于匹配的键。可选的哈希算法，以及用于PIR协议检索的可选值。 |
| [PrivacyProtocol](arkts-dataprotection-privacycomputation-privacyprotocol-i.md) | 定义隐私协议配置，包括数据集大小、协议类型等。用于隐私保护计算。 |
| [PrivacySearchResult](arkts-dataprotection-privacycomputation-privacysearchresult-i.md) | 定义隐私搜索操作的结果，包含结果的密文。和可选值密文。 |
| [SearchResult](arkts-dataprotection-privacycomputation-searchresult-i.md) | 定义解密后的最终搜索结果，指示是否找到匹配项以及与匹配元素关联的可选附加值。 |
| [TargetElement](arkts-dataprotection-privacycomputation-targetelement-i.md) | 定义隐私计算的目标元素，包括原始元素数据和可选的哈希算法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataSetSize](arkts-dataprotection-privacycomputation-datasetsize-e.md) | 枚举隐私协议支持的数据集大小。数据集大小定义单个结果密文可以包含的比较次数。的总数生成的结果密文由element.size/dataSetSize决定。选择一个根据隐私搜索中元素的数量和可接受的每个结果密文的大小。 |
| [HashAlg](arkts-dataprotection-privacycomputation-hashalg-e.md) | 定义用于隐私保护计算的哈希算法。 |
| [ProtocolType](arkts-dataprotection-privacycomputation-protocoltype-e.md) | 枚举隐私协议类型。协议类型决定隐私保护用于搜索操作的计算方法。 |
