# @ohos.security.privacyComputation (Privacy Computation)

<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @xling_feng_qing-->
<!--Designer: @Pawn_loading-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=d13ac1422b0baeecdbad4d81d9d51c15709bde20 translatedAt=2026-11-02T00:57:29.538Z pushedAt=2026-11-02T05:43:23.346Z nl=1 -->

This module provides privacy computation capabilities, including privacy target generation, privacy search, and search result retrieval. It can be used to perform data comparison and retrieval without disclosing the original data and dataset content to the other party.

A complete privacy computation consists of three steps: the initiator calls [genPrivacyTarget](#privacycomputationgenprivacytarget) to generate a privacy target, the responder calls [privacySearch](#privacycomputationprivacysearch) to perform the privacy search and return the result ciphertext, and the initiator calls [getSearchResult](#privacycomputationgetsearchresult) to decrypt the result ciphertext and obtain the matched result and the original additional value from the responder.

**Since:** 26.0.1

## Modules to Import

```ts
import { privacyComputation } from '@kit.DataProtectionKit';
```

## HashAlg

Enumerates the hash algorithms used for privacy computation. It is used to calculate hash values for target elements or dataset elements.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

| Name | Value | Description |
| -------- | -------- | -------- |
| NONE | 0 | No hash algorithm. When no hash algorithm is explicitly specified, **NONE** is used by default. |
| SHA256 | 1 | SHA-256. |
| SHA384 | 2 | SHA-384. |
| SHA512 | 3 | SHA-512. |

## DataSetSize

Enumerates the dataset sizes supported by the privacy protocol. The dataset size defines the number of comparisons that a single ciphertext result can contain. The total number of ciphertexts generated is determined by **elements.size**/**dataSetSize**.

Select an appropriate value based on the number of elements in the privacy search and the acceptable size of each ciphertext.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

| Name | Value | Description |
| -------- | -------- | -------- |
| SIZE_128 | 0 | A single ciphertext can contain 128 comparisons. |
| SIZE_256 | 1 | A single ciphertext can contain 256 comparisons. |
| SIZE_512 | 2 | A single ciphertext can contain 512 comparisons. |

## ProtocolType

Enumerates the privacy protocol types, which determine the algorithm used for privacy search.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

| Name | Value | Description |
| -------- | -------- | -------- |
| PSI_PROTOCOL | 0 | Private Set Intersection (PSI) protocol. This parameter determines whether a target element exists in a dataset without revealing the element or the dataset content. |
| PIR_PROTOCOL | 1 | Private Information Retrieval (PIR) protocol. This parameter is used to retrieve the additional value matching a target key from a dataset without revealing the key or the retrieved value. |

## PrivacyProtocol

Defines the privacy protocol configuration, including the dataset size and protocol type.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| dataSetSize | [DataSetSize](#datasetsize) | No | No | Dataset size of the privacy protocol. |
| protocolType | [ProtocolType](#protocoltype) | No | No | Protocol type of privacy computation. |


## TargetElement

Defines the target element of privacy computation, including the raw element data and an optional hash algorithm.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| elemData | Uint8Array | No | No | Raw data of the target element to search for. The length must not exceed 1 KB. |
| hashAlg | [HashAlg](#hashalg) | No | Yes | Hash algorithm used to compute the target element. If no hash algorithm is explicitly specified, the default value is NONE. |
## Element

Defines the dataset element used in privacy search. Each element contains a key for matching, an optional hash algorithm, and an optional additional value for PIR protocol retrieval.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| elemKey | Uint8Array | No | No | Key of the dataset element, which is used to match against the privacy target. The length must not exceed 1 KB. |
| hashAlg | [HashAlg](#hashalg) | No | Yes | Hash algorithm used to compute the element key. If no hash algorithm is explicitly specified, **NONE** is used by default. |
| elemValue | Uint8Array | No | Yes | Additional value associated with the element key.<br>**Note:**<br>This parameter is used only in the PIR protocol to retrieve the additional value when a match is found.<br>If not specified, the element supports only key matching, not value retrieval. |

## PrivacySearchResult

Defines the result of a privacy search, including the result ciphertext and the optional additional value ciphertext.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| resultCipherText | Uint8Array[] | No | No | Array of result ciphertexts generated by the privacy search. It can be decrypted using [getSearchResult](#privacycomputationgetsearchresult). |
| valueCipherText | Uint8Array[] | No | Yes | Array of value ciphertexts generated when the PIR protocol is used for the privacy search. These ciphertexts contain the encrypted values related to the matched elements.<br>**Note:** This field exists only under the PIR protocol and is not read under the PSI protocol. |

## SearchResult

Defines the final search result after decryption, indicating whether a match is found and the optional additional value associated with the matched element.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| matchedResult | boolean | No | No | Whether the privacy target is found in the dataset. The value **true** indicates that a match is found; the value **false** indicates no match. |
| attachedValues | Uint8Array[] | No | Yes | Additional values associated with the matched element. A value is returned only when the PIR protocol is used and a match is found. Otherwise, **undefined** is returned. |

## privacyComputation.genPrivacyTarget

genPrivacyTarget(targetElement: TargetElement, privacyProtocol: PrivacyProtocol): Promise&lt;Uint8Array&gt;

Generates a privacy target for a given element. A privacy target is an encrypted representation of the searched element, which can be used for privacy search without disclosing the original data. This API uses a promise to return the result.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| targetElement | [TargetElement](#targetelement) | Yes | Target element to search, including the original data and an optional hash algorithm. |
| privacyProtocol | [PrivacyProtocol](#privacyprotocol) | Yes | Privacy protocol configuration, including the dataset size and protocol type. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;Uint8Array&gt; | Promise used to return the encrypted privacy target. |

**Error codes**

For details about the error codes, see [Critical Asset Storage Service Error Codes](../apis-asset-store-kit/errorcode-asset.md).

| ID | Error Message |
| -------- | -------- |
| 24000001 | The service is unavailable. |
| 24000006 | Insufficient memory. |
| 24000009 | The cryptography operation failed. |
| 24000017 | The capability is not supported. |
| 24000018 | Parameter verification failed. |

**Example**

```ts
import { privacyComputation } from '@kit.DataProtectionKit';

async function genTarget() {
  const targetElement: privacyComputation.TargetElement = {
    elemData: new Uint8Array([0x01, 0x02, 0x03]),
    hashAlg: privacyComputation.HashAlg.SHA256
  };
  const privacyProtocol: privacyComputation.PrivacyProtocol = {
    dataSetSize: privacyComputation.DataSetSize.SIZE_512,
    protocolType: privacyComputation.ProtocolType.PSI_PROTOCOL
  };

  const privacyTarget: Uint8Array = await privacyComputation.genPrivacyTarget(targetElement, privacyProtocol);
  console.info('privacyTarget length: ' + privacyTarget.length);
}
```

## privacyComputation.privacySearch

privacySearch(privacyTarget: Uint8Array, elements: Element[], privacyProtocol: PrivacyProtocol): Promise&lt;PrivacySearchResult&gt;

Performs a privacy search. This API searches the given dataset elements based on the encrypted privacy target without disclosing the target or the dataset content to the other party. This API uses a promise to return the result.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| privacyTarget | Uint8Array | Yes | Encrypted privacy target generated by [genPrivacyTarget](#privacycomputationgenprivacytarget). |
| elements | [Element](#element)[] | Yes | Dataset elements to search. |
| privacyProtocol | [PrivacyProtocol](#privacyprotocol) | Yes | Privacy protocol configuration, which must be consistent with that used when generating the privacy target. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[PrivacySearchResult](#privacysearchresult)&gt; | Promise object used to return the privacy search result, which contains the result ciphertext and the optional additional value ciphertext. |

**Error codes**

For details about the error codes, see [Asset Store Service Error Code](../apis-asset-store-kit/errorcode-asset.md).

| ID | Error Message |
| -------- | -------- |
| 24000001 | The service is unavailable. |
| 24000006 | Insufficient memory. |
| 24000009 | The cryptography operation failed. |
| 24000017 | The capability is not supported. |
| 24000018 | Parameter verification failed. |

**Example**

```ts
import { privacyComputation } from '@kit.DataProtectionKit';

async function search(privacyTarget: Uint8Array) {
  const elements: Array<privacyComputation.Element> = [
    {
      elemKey: new Uint8Array([0x01, 0x02, 0x03]),
      hashAlg: privacyComputation.HashAlg.SHA256,
      elemValue: new Uint8Array([0xA1, 0xA2])
    },
    {
      elemKey: new Uint8Array([0x07, 0x08, 0x09]),
      hashAlg: privacyComputation.HashAlg.SHA256
    }
  ];
  const privacyProtocol: privacyComputation.PrivacyProtocol = {
    dataSetSize: privacyComputation.DataSetSize.SIZE_256,
    protocolType: privacyComputation.ProtocolType.PIR_PROTOCOL
  };

  const result: privacyComputation.PrivacySearchResult =
    await privacyComputation.privacySearch(privacyTarget, elements, privacyProtocol);
  console.info('resultCipherText count: ' + result.resultCipherText.length + ', valueCipherText count: ' + (result.valueCipherText?.length ?? 0));
}
```

## privacyComputation.getSearchResult

getSearchResult(privacySearchResult: PrivacySearchResult, privacyProtocol: PrivacyProtocol): Promise&lt;SearchResult&gt;

Obtains the privacy search result and the final search result. This method decrypts the result ciphertext returned by [privacySearch](#privacycomputationprivacysearch) to obtain the final matching result and the optional additional values. This API uses a promise to return the result.

**Since:** 26.0.1

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| privacySearchResult | [PrivacySearchResult](#privacysearchresult) | Yes | Result returned by [privacySearch](#privacycomputationprivacysearch). |
| privacyProtocol | [PrivacyProtocol](#privacyprotocol) | Yes | Privacy protocol configuration, which must be consistent with that used when generating the privacy target. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[SearchResult](#searchresult)&gt; | Promise used to return the final search result. **matchedResult** indicates whether the target is matched; **attachedValues** is the additional value of the matched item (returned only for the PIR protocol when a match is found). |

**Error codes**

For details about the following error codes, see [Asset Store Service Error Code](../apis-asset-store-kit/errorcode-asset.md).

| ID | Error Message |
| -------- | -------- |
| 24000001 | The service is unavailable. |
| 24000006 | Insufficient memory. |
| 24000009 | The cryptography operation failed. |
| 24000017 | The capability is not supported. |
| 24000018 | Parameter verification failed. |

**Example**

```ts
import { privacyComputation } from '@kit.DataProtectionKit';

async function getResult(searchResult: privacyComputation.PrivacySearchResult) {
  const privacyProtocol: privacyComputation.PrivacyProtocol = {
    dataSetSize: privacyComputation.DataSetSize.SIZE_256,
    protocolType: privacyComputation.ProtocolType.PIR_PROTOCOL
  };

  const result: privacyComputation.SearchResult =
    await privacyComputation.getSearchResult(searchResult, privacyProtocol);
  if (result.matchedResult) {
    console.info('matched, attachedValues count: ' + (result.attachedValues?.length ?? 0));
  } else {
    console.info('not matched');
  }
}
```
