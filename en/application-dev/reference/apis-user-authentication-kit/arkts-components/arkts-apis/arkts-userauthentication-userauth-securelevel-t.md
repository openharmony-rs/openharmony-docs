# SecureLevel

```TypeScript
type SecureLevel = 'S1' | 'S2' | 'S3' | 'S4'
```

Enumerates the authentication security levels.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md)

**System capability:** SystemCapability.UserIAM.UserAuth.Core

| Type | Description |
| --- | --- |
| 'S1' | Authentication trust level 1. The authentication of this level can identify individual users and provides certain liveness detection capabilities. It is usually used in service risk control and query of general personal data. |
| 'S2' | Authentication trust level 2. The authentication of this level can accurately identify individual users and provides certain liveness detection capabilities. It is usually used in scenarios such as application logins and keeping the unlocking state of a device. |
| 'S3' | Authentication trust level 3. The authentication of this level can accurately identify individual users and provides strong liveness detection capabilities. It is usually used in scenarios such as unlocking a device. |
| 'S4' | Authentication trust level 4. The authentication of this level can identify individual users with high precision and provides powerful liveness detection capabilities. It is usually used in scenarios such as small-amount payment. |
