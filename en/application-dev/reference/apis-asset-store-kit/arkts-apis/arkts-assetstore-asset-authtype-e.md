# AuthType

```TypeScript
enum AuthType
```

Enumerates the types of user authentication supported by an asset.

**Since:** 11

<!--Device-asset-enum AuthType--><!--Device-asset-enum AuthType-End-->

**System capability:** SystemCapability.Security.Asset

## NONE

```TypeScript
NONE = 0x00
```

No user authentication is required before the asset is accessed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-AuthType-NONE = 0x00--><!--Device-AuthType-NONE = 0x00-End-->

**System capability:** SystemCapability.Security.Asset

## ANY

```TypeScript
ANY = 0xFF
```

The asset can be accessed if any user authentication (such as PIN, facial, or fingerprint authentication) is successful.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-AuthType-ANY = 0xFF--><!--Device-AuthType-ANY = 0xFF-End-->

**System capability:** SystemCapability.Security.Asset
