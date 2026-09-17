# SearchResult

Defines the final search result after decryption, indicating whether a match was found and the optional attached value associated with the matched element.

**Since:** 26.1.0

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
```

## attachedValues

```TypeScript
attachedValues?: Uint8Array[]
```

The attached value associated with the matched element. This field is available only when using PIR protocol and a match is found; it is undefined otherwise.

**Type:** Uint8Array[]

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset

## matchedResult

```TypeScript
matchedResult: boolean
```

Indicates whether the privacy target was found in the dataset. True means a match was found; false means no match.

**Type:** boolean

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset
