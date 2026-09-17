# getSearchResult

## Modules to Import

```TypeScript
```

## getSearchResult

```TypeScript
function getSearchResult(privacySearchResult: PrivacySearchResult, privacyProtocol: PrivacyProtocol):
        Promise<SearchResult>
```

Get the privacy search result and the final search outcome. Decrypts the search result ciphertexts returned by privacySearch to obtain the final match result and optional attached value. This API uses a promise to return the result.

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| privacySearchResult | [PrivacySearchResult](arkts-dataprotection-privacycomputation-privacysearchresult-i.md) | Yes | The result returned by privacySearch. |
| privacyProtocol | [PrivacyProtocol](arkts-dataprotection-privacycomputation-privacyprotocol-i.md) | Yes | The privacy protocol configuration, including data set size and protocol type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SearchResult](arkts-dataprotection-privacycomputation-searchresult-i.md)&gt; | Promise used to return the searchResult. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24000006](../../apis-asset-store-kit/errorcode-asset.md#24000006-insufficient-memory) | Insufficient memory. |
| [24000018](../../apis-asset-store-kit/errorcode-asset.md#24000018-parameter-check-failed) | Parameter verification failed. |
