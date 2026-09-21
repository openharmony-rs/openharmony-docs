# HuksSecureSignType

```TypeScript
export enum HuksSecureSignType
```

Enumerates the signature types of the key generated or imported.

**Since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_SECURE_SIGN_WITH_AUTHINFO

```TypeScript
HUKS_SECURE_SIGN_WITH_AUTHINFO = 1
```

The signature carries authentication information. This field is specified when a key is generated or imported. When the key is used for signing, the data will be added with the authentication information and then be signed.

**NOTE:** 

The carried authentication information includes identity information. You need to describe the purpose, retention policy, and destruction method of the identity information in the privacy statement.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension
