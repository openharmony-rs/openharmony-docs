# TargetElement

```TypeScript
interface TargetElement
```

Defines the target element for privacy computation, including the raw element data and an optional hash algorithm.

**Since:** 26.0.1

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
```

## elemData

```TypeScript
elemData: Uint8Array
```

The raw data of the target element to be searched for.

**Type:** Uint8Array

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset

## hashAlg

```TypeScript
hashAlg?: HashAlg
```

The hash algorithm used for hashing the target element. If not specified, the element data will be used with SHA256 default.

**Type:** [HashAlg](arkts-dataprotection-privacycomputation-hashalg-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Security.Asset
