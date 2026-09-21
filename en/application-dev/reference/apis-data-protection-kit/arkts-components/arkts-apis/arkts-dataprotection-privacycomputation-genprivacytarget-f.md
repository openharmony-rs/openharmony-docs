# genPrivacyTarget

## Modules to Import

```TypeScript
```

## genPrivacyTarget

```TypeScript
function genPrivacyTarget(targetElement: TargetElement, privacyProtocol: PrivacyProtocol): Promise<Uint8Array>
```

Generates a privacy target for the given element. The privacy target is an encrypted representation of the search element that can be used in a privacy-preserving search without revealing the original data. This API uses a promise to return the result.

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetElement | [TargetElement](arkts-dataprotection-privacycomputation-targetelement-i.md) | Yes | The element to search for, including its raw data and optional hash algorithm. |
| privacyProtocol | [PrivacyProtocol](arkts-dataprotection-privacycomputation-privacyprotocol-i.md) | Yes | The privacy protocol configuration, including data set size and protocol type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the encryption result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24000006](../../apis-asset-store-kit/errorcode-asset.md#24000006-insufficient-memory) | Insufficient memory. |
| [24000018](../../apis-asset-store-kit/errorcode-asset.md#24000018-parameter-check-failed) | Parameter verification failed. |
