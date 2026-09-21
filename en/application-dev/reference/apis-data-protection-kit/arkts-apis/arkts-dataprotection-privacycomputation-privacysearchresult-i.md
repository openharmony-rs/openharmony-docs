# PrivacySearchResult

```TypeScript
interface PrivacySearchResult
```

Defines the result of a privacy search operation, containing the result ciphertexts and optional value ciphertexts.

**Since:** 26.0.1

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
```

## resultCipherText

```TypeScript
resultCipherText: Array<Uint8Array>
```

The array of result ciphertexts generated during the privacy search. These ciphertexts encode the search result and need to be decrypted by getSearchResult.

**Type:** Array&lt;Uint8Array&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

## valueCipherText

```TypeScript
valueCipherText?: Uint8Array[]
```

The array of value ciphertexts generated during the privacy search when using PIR protocol. These ciphertexts contain the encrypted values associated with the matched elements.

**Type:** Uint8Array[]

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset
