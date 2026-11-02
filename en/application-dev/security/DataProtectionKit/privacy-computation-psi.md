# Using the PSI Protocol for Private Set Intersection
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @xling_feng_qing-->
<!--Designer: @Pawn_loading-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=1c880bd3d92bd962bc3a718970597adf5708f28d translatedAt=2026-10-31T02:50:43.403Z pushedAt=2026-10-31T05:58:44.292Z nl=1 -->

## When to Use

The PSI protocol (Private Set Intersection) is used to determine whether a target element exists in the other party's dataset without revealing the elements or the content of the dataset. It applies to scenarios where two parties cannot exchange plaintext sets, such as contact matching and friend recommendation.

Performing private set intersection through the PSI protocol involves three steps: generating a privacy target [genPrivacyTarget](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgenprivacytarget), performing a privacy search [privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch), and obtaining the search result [getSearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgetsearchresult). The PSI protocol returns only whether there is a match, without any additional value. To retrieve the additional value of a matched item, use the [PIR protocol](privacy-computation-pir.md).

## How to Develop

1. Import the modules required by the APIs.

   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/psi.ets) -->
   
   ``` TypeScript
   import { privacyComputation } from '@kit.DataProtectionKit';
   ```

2. The initiator generates the privacy target.

   Construct [TargetElement](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#targetelement) (the original data of the target element and the hash algorithm) and [PrivacyProtocol](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacyprotocol) (set the protocol type to PSI_PROTOCOL), and call [genPrivacyTarget](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgenprivacytarget) to generate the privacy target.

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

3. The responder performs the privacy search.

   Construct an array of [Element](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#element) (dataset elements, including keys and hash algorithms), and call [privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch) together with the privacy target and protocol configuration to perform the privacy search.

   <!-- @[privacySearch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/psi.ets) -->
   
   ``` TypeScript
   const elements: privacyComputation.Element[] = [
     { elemKey: new Uint8Array([0x01, 0x02, 0x03]), hashAlg: privacyComputation.HashAlg.SHA256 },
     { elemKey: new Uint8Array([0x07, 0x08, 0x09]), hashAlg: privacyComputation.HashAlg.SHA256 }
   ];
   const searchResult: privacyComputation.PrivacySearchResult =
     await privacyComputation.privacySearch(privacyTarget, elements, privacyProtocol);
   ```

4. The initiator obtains the final result.

   Pass the result returned by [privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch) to [getSearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgetsearchresult), and decrypt it to obtain [SearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#searchresult). matchedResult indicates whether the target element exists in the dataset.

   <!-- @[getSearchResult](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/psi.ets) -->
   
   ``` TypeScript
   const result: privacyComputation.SearchResult =
     await privacyComputation.getSearchResult(searchResult, privacyProtocol);
   console.info('matched: ' + result.matchedResult);
   ```

> **NOTE**
>
> - `privacyProtocol` must remain consistent across the three APIs.
> - If an exception occurs during the call, use `try/catch` to catch `BusinessError`. For details about the error codes, see [Key Asset Store Service Error Codes](../../reference/apis-asset-store-kit/errorcode-asset.md).

<!--no_check-->