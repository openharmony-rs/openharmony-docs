# 隐私计算简介
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @xling_feng_qing-->
<!--Designer: @Pawn_loading-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 介绍

隐私计算提供隐私保护的数据比对与检索能力，包括隐私目标生成、隐私搜索、搜索结果检索。在不向对方透露原始数据与数据集内容的前提下，判断目标元素是否存在于对方数据集中，或检索匹配项的附加值。

隐私计算支持两类协议：

- **PSI协议**（隐私集合求交，Private Set Intersection）：判断目标元素是否存在于数据集中，而不显示元素或数据集内容。
- **PIR协议**（隐私信息检索，Private Information Retrieval）：用于检索与数据集中匹配的键，而不显示键或检索到的值。

一次完整的隐私计算包含三个步骤：

1. 发起端调用[genPrivacyTarget](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgenprivacytarget)生成隐私目标（目标元素的加密表示）。
2. 响应端调用[privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch)，根据隐私目标在数据集上执行隐私搜索，返回结果密文。
3. 发起端调用[getSearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgetsearchresult)解密结果密文，得到是否命中及匹配项的附加值。

具体的协议开发步骤，参见[使用PSI协议进行隐私集合求交](privacy-computation-psi.md)和[使用PIR协议进行隐私信息检索](privacy-computation-pir.md)。

## 基本概念

在开发隐私计算相关功能前，开发者需要先了解以下基本概念。

- **隐私目标**

  发起端对目标元素处理后生成的加密表示，可发送给响应端用于隐私搜索，不会泄露目标元素的原始数据。

- **隐私搜索**

  响应端在密文域上根据隐私目标对数据集执行的搜索操作，返回结果密文，搜索过程不暴露目标与数据集内容。

- **结果密文**

  隐私搜索生成的密文，需由发起端通过getSearchResult解密后才能得到最终匹配结果。

- **数据集大小**

  单个结果密文可以包含的比较次数，结果密文总数由elements.size/dataSetSize决定。根据隐私搜索中元素的数量与每个结果密文可接受的大小选择合适的取值。

## 约束与限制

- 本模块接口从API version 26.0.1开始支持。
- 本模块接口为原子化服务API，从API version 26.0.1开始支持在原子化服务中使用。
- 本模块接口可在FA模型和Stage模型下使用。

## 接口说明

隐私计算关键接口如下表所示，具体API说明详见[@ohos.security.privacyComputation](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md)。

**表1** 隐私计算接口

| 接口名 | 描述 |
| -------- | -------- |
| genPrivacyTarget(targetElement: TargetElement, privacyProtocol: PrivacyProtocol): Promise&lt;Uint8Array&gt; | 为给定元素生成隐私目标。 |
| privacySearch(privacyTarget: Uint8Array, elements: Element[], privacyProtocol: PrivacyProtocol): Promise&lt;PrivacySearchResult&gt; | 执行隐私保护搜索。 |
| getSearchResult(privacySearchResult: PrivacySearchResult, privacyProtocol: PrivacyProtocol): Promise&lt;SearchResult&gt; | 获取隐私搜索结果和最终搜索结果。 |
