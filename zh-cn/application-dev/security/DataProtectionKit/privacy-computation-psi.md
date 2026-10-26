# 使用PSI协议进行隐私集合求交
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @xling_feng_qing-->
<!--Designer: @Pawn_loading-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 场景介绍

PSI协议（隐私集合求交，Private Set Intersection）用于在不显示元素或数据集内容的前提下，判断目标元素是否存在于对方数据集中。适用于两方不可交换明文集合的情况，例如联系人匹配、好友推荐等。

通过PSI协议进行隐私集合求交，包含生成隐私目标[genPrivacyTarget](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgenprivacytarget)、隐私搜索[privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch)、获取搜索结果[getSearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgetsearchresult)三个步骤。PSI协议仅返回是否命中，不返回附加值；如需检索匹配项的附加值，请使用[PIR协议](privacy-computation-pir.md)。

## 开发步骤

1. 接口所需模块导入。

   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/psi.ets) -->
   
   ``` TypeScript
   import { privacyComputation } from '@kit.DataProtectionKit';
   ```

2. 发起端生成隐私目标。

   构造[TargetElement](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#targetelement)（目标元素原始数据与哈希算法）和[PrivacyProtocol](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacyprotocol)（协议类型设为PSI_PROTOCOL），调用[genPrivacyTarget](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgenprivacytarget)生成隐私目标。

   <!-- @[genPrivacyTarget](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/psi.ets) -->
   
   ``` TypeScript
   const targetElement: privacyComputation.TargetElement = {
     elemData: new Uint8Array([0x01, 0x02, 0x03]),
     hashAlg: privacyComputation.HashAlg.SHA256
   };
   const privacyProtocol: privacyComputation.PrivacyProtocol = {
     dataSetSize: privacyComputation.DataSetSize.SIZE_512,
     protocolType: privacyComputation.ProtocolType.PSI_PROTOCOL
   };
   const privacyTarget: Uint8Array = await privacyComputation.genPrivacyTarget(targetElement, privacyProtocol);
   ```

3. 响应端执行隐私搜索。

   构造[Element](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#element)数组（数据集元素，包含键与哈希算法），连同隐私目标和协议配置，调用[privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch)执行隐私搜索。

   <!-- @[privacySearch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/psi.ets) -->
   
   ``` TypeScript
   const elements: privacyComputation.Element[] = [
     { elemKey: new Uint8Array([0x01, 0x02, 0x03]), hashAlg: privacyComputation.HashAlg.SHA256 },
     { elemKey: new Uint8Array([0x07, 0x08, 0x09]), hashAlg: privacyComputation.HashAlg.SHA256 }
   ];
   const searchResult: privacyComputation.PrivacySearchResult =
     await privacyComputation.privacySearch(privacyTarget, elements, privacyProtocol);
   ```

4. 发起端获取最终结果。

   将[privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch)返回的结果传入[getSearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgetsearchresult)，解密得到[SearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#searchresult)。matchedResult指示目标元素是否存在于数据集中。

   <!-- @[getSearchResult](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/psi.ets) -->
   
   ``` TypeScript
   const result: privacyComputation.SearchResult =
     await privacyComputation.getSearchResult(searchResult, privacyProtocol);
   console.info('matched: ' + result.matchedResult);
   ```

> **说明：**
>
> - privacyProtocol需在三个接口间保持一致。
> - 若调用异常，可通过try/catch捕获BusinessError，错误码详见[关键资产存储服务错误码](../../reference/apis-asset-store-kit/errorcode-asset.md)。
