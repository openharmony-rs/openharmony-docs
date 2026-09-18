# Element

Defines a dataset element used in privacy search. Each element contains a key for matching, an optional hash algorithm, and an optional value for PIR protocol retrieval.

**Since:** 26.1.0

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
```

## elemKey

```TypeScript
elemKey: Uint8Array
```

The key of the dataset element, used for matching against the privacy target.

**Type:** Uint8Array

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset

## elemValue

```TypeScript
elemValue?: Uint8Array
```

The value associated with the element key. This field is used in PIR protocol to retrieve the attached value when a match is found. If not specified, the element only supports key matching without value retrieval.

**Type:** Uint8Array

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset

## hashAlg

```TypeScript
hashAlg?: HashAlg
```

The hash algorithm used for hashing the element key. If not specified, the element key will be used with SHA256 default.

**Type:** [HashAlg](arkts-dataprotection-privacycomputation-hashalg-e.md)

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Security.Asset
