# ReturnType

```TypeScript
enum ReturnType
```

Enumerates the type of information returned by an asset query operation.

**Since:** 11

**System capability:** SystemCapability.Security.Asset

## ALL

```TypeScript
ALL = 0
```

The query result contains the asset in plaintext and its attributes.

**Note:**  Use this option when you need to query the plaintext of a single asset.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## ATTRIBUTES

```TypeScript
ATTRIBUTES = 1
```

The query result contains only the asset attributes.

**Note:**  Use this option when you need to query attributes of multiple assets.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset
