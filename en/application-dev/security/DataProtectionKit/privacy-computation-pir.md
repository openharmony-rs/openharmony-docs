# Using the PIR Protocol for Private Information Retrieval
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @xling_feng_qing-->
<!--Designer: @Pawn_loading-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=2827c23030fa3028ff9885a7e0a9042afc4f3ccf translatedAt=2026-10-31T07:15:27.448Z pushedAt=2026-11-02T07:18:51.056Z nl=1 -->

## When to Use

The PIR protocol (Private Information Retrieval) applies to scenarios where you obtain the attached values of matching items from the other party's dataset without exposing the query conditions, for example, querying configuration information by identifier or querying entitlement information by credential.

Private information retrieval through the PIR protocol involves three steps: generating a privacy target [genPrivacyTarget](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgenprivacytarget), performing a privacy search [privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch), and obtaining the search result [getSearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgetsearchresult). The PIR protocol returns the attached value of the matching element upon a hit.

## Development Procedure

1. Import the modules required by the APIs.

   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/pir.ets) -->
   
   ``` TypeScript
   import { privacyComputation } from '@kit.DataProtectionKit';
   ```

2. The initiator generates the privacy target.

   Construct [TargetElement](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#targetelement) (the original data of the target element and the hash algorithm) and [PrivacyProtocol](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacyprotocol) (set the protocol type to PIR_PROTOCOL), and call [genPrivacyTarget](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgenprivacytarget) to generate the privacy target.

   <!-- @[genPrivacyTarget](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/pir.ets) -->
   
   ``` TypeScript
   const targetElement: privacyComputation.TargetElement = {
     elemData: new Uint8Array([0x01, 0x02, 0x03]),
     hashAlg: privacyComputation.HashAlg.SHA256
   };
   const privacyProtocol: privacyComputation.PrivacyProtocol = {
     dataSetSize: privacyComputation.DataSetSize.SIZE_256,
     protocolType: privacyComputation.ProtocolType.PIR_PROTOCOL
   };
   const privacyTarget: Uint8Array = await privacyComputation.genPrivacyTarget(targetElement, privacyProtocol);
   ```

3. The responder performs the privacy search.

   Construct an array of [Element](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#element) (dataset elements, including the key, hash algorithm, and attached value elemValue), and call [privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch) together with the privacy target and protocol configuration to perform the privacy search. elemValue is the attached value returned upon a hit and is used only in the PIR protocol.

   <!-- @[privacySearch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/pir.ets) -->
   
   ``` TypeScript
   const elements: privacyComputation.Element[] = [
     {
       elemKey: new Uint8Array([0x01, 0x02, 0x03]),
       hashAlg: privacyComputation.HashAlg.SHA256,
       elemValue: new Uint8Array([0xA1, 0xA2])
     },
     {
       elemKey: new Uint8Array([0x07, 0x08, 0x09]),
       hashAlg: privacyComputation.HashAlg.SHA256,
       elemValue: new Uint8Array([0xB1, 0xB2])
     }
   ];
   const searchResult: privacyComputation.PrivacySearchResult =
     await privacyComputation.privacySearch(privacyTarget, elements, privacyProtocol);
   ```

4. The initiator obtains the final result.

   Pass the result returned by [privacySearch](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationprivacysearch) to [getSearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#privacycomputationgetsearchresult) and decrypt it to obtain [SearchResult](../../reference/apis-data-protection-kit/js-apis-privacyComputation.md#searchresult). matchedResult indicates whether there is a hit; upon a hit, attachedValues returns the attached value of the matching element.

   <!-- @[getSearchResult](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/PrivacyComputation/entry/src/main/ets/operations/pir.ets) -->
   
   ``` TypeScript
   const result: privacyComputation.SearchResult =
     await privacyComputation.getSearchResult(searchResult, privacyProtocol);
   console.info('matched: ' + result.matchedResult);
   if (result.matchedResult && result.attachedValues) {
     console.info('attachedValues count: ' + result.attachedValues.length);
   }
   ```

> **NOTE**
>
> - `privacyProtocol` must remain consistent across the three APIs.
> - If an exception occurs during the call, use `try/catch` to catch `BusinessError`. For details about the error codes, see [Key Asset Store Service Error Codes](../../reference/apis-asset-store-kit/errorcode-asset.md).

<!--no_check-->