# @ohos.security.privacyComputation(Declares the APIs for privacy-preserving computation, including privacy target generation,)

The namespace of privacyComputation, providing privacy-preserving computation capabilities such as privacy target generation, privacy search, and search result retrieval.

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [genPrivacyTarget](arkts-dataprotection-privacycomputation-genprivacytarget-f.md) | Generates a privacy target for the given element. The privacy target is an encrypted representation of the search element that can be used in a privacy-preserving search without revealing the original data. This API uses a promise to return the result. |
| [getSearchResult](arkts-dataprotection-privacycomputation-getsearchresult-f.md) | Get the privacy search result and the final search outcome. Decrypts the search result ciphertexts returned by privacySearch to obtain the final match result and optional attached value. This API uses a promise to return the result. |
| [privacySearch](arkts-dataprotection-privacycomputation-privacysearch-f.md) | Performs a privacy-preserving search. Searches the given dataset elements against the encrypted privacy target without revealing the target or the dataset contents to the other party. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [Element](arkts-dataprotection-privacycomputation-element-i.md) | Defines a dataset element used in privacy search. Each element contains a key for matching, an optional hash algorithm, and an optional value for PIR protocol retrieval. |
| [PrivacyProtocol](arkts-dataprotection-privacycomputation-privacyprotocol-i.md) | Defines the privacy protocol configuration, including the data set size and protocol type used for privacy-preserving computation. |
| [PrivacySearchResult](arkts-dataprotection-privacycomputation-privacysearchresult-i.md) | Defines the result of a privacy search operation, containing the result ciphertexts and optional value ciphertexts. |
| [SearchResult](arkts-dataprotection-privacycomputation-searchresult-i.md) | Defines the final search result after decryption, indicating whether a match was found and the optional attached value associated with the matched element. |
| [TargetElement](arkts-dataprotection-privacycomputation-targetelement-i.md) | Defines the target element for privacy computation, including the raw element data and an optional hash algorithm. |

### Enums

| Name | Description |
| --- | --- |
| [DataSetSize](arkts-dataprotection-privacycomputation-datasetsize-e.md) | Enumerates the data set sizes supported by the privacy protocol. The data set size defines the number of comparisons that a single result ciphertext can contain. The total number of result ciphertexts generated is determined by elements.size / dataSetSize. Choose an appropriate data set size based on the number of elements in privacySearch and the acceptable size of each result ciphertext. |
| [HashAlg](arkts-dataprotection-privacycomputation-hashalg-e.md) | Defines the hash algorithms used for privacy-preserving computation. |
| [ProtocolType](arkts-dataprotection-privacycomputation-protocoltype-e.md) | Enumerates the privacy protocol types. The protocol type determines the privacy-preserving computation method used for the search operation. |
