# AuthTrustLevel

Enumerates the trust levels of the authentication result. This enum defines four trust levels of the authentication result, which are used to describe the security strength of the authentication result. A higher trust level indicates a stronger liveness detection capability and more accurate user identity recognition of the authentication solution, and is applicable to service scenarios that require higher security. The application should select a proper authentication trust level based on the security requirements of service scenarios.

For typical use cases, see [Principles for Classifying Biometric Authentication Trust Levels](../../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels).

**Since:** 8

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## ATL1

```TypeScript
ATL1 = 10000
```

Authentication trust level 1. It can identify individual users and provides basic liveness detection capabilities (such as simple action detection). The security strength is low, and the authentication result may be risky. It is applicable to low-security scenarios such as service risk control, common personal data query, and access to non-sensitive information. It is recommended that this level be used together with other security measures.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## ATL2

```TypeScript
ATL2 = 20000
```

Authentication trust level 2. It can accurately identify individual users and provides standard liveness detection capabilities (such as blinking and nodding detection). It features medium security strength and can effectively defend against simple forgery attacks. It is applicable to medium-security scenarios such as maintaining the screen-unlocked state of a device, application login, and confirmation of general sensitive operations.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## ATL3

```TypeScript
ATL3 = 30000
```

Authentication trust level 3. It can accurately identify individual users and provides strong liveness detection capabilities (such as 3D face recognition and multi-frame analysis). It features high security strength and can effectively defend against common forgery attacks such as photos and videos. It is applicable to high-security scenarios such as device unlocking, confirmation of important sensitive operations, and enterprise-level application login. 3D face recognition devices support this level.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## ATL4

```TypeScript
ATL4 = 40000
```

Authentication trust level 4. It can accurately identify individual users and provides strong liveness detection capabilities (such as in-depth analysis and multi-dimensional verification). It features the highest security strength and can effectively defend against various advanced forgery attacks. It is applicable to high-security scenarios, such as small-amount payment, financial transactions, and access to highly sensitive data. Only a few high-security authentication solutions support this level.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
