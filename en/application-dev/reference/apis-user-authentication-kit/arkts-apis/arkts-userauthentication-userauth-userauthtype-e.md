# UserAuthType

Enumerates the identity authentication types. This enum defines the authentication types supported by the system, including PIN authentication and biometric authentication (face and fingerprint). When initiating authentication, an application needs to specify the authentication type list, and the user can select any of the authentication types to complete the authentication. The security strength and user experience vary depending on authentication types. The application needs to select a proper authentication type based on service scenarios.

**Since:** 8

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## PIN

```TypeScript
PIN = 1
```

PIN authentication. It indicates that the user enters the PIN to complete authentication. PIN authentication has a high security level of ATL4. It is applicable to scenarios requiring high security, such as payment and confirmation of important operations. However, users need to manually enter information, which is not as convenient as biometric authentication.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## FACE

```TypeScript
FACE = 2
```

Face authentication. It indicates that the system checks whether the facial features of a user match the enrolled face. Face authentication supports different levels of liveness detection. For details about the classification principles, see [Principles for Classifying Biometric Authentication Trust Levels](../../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels). The advantage is convenient user experience, but the disadvantage is that there are certain requirements on the device and lighting conditions.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## FINGERPRINT

```TypeScript
FINGERPRINT = 4
```

Fingerprint authentication. It indicates that the user is authenticated through the fingerprint sensor. The system checks whether the user fingerprint matches the enrolled fingerprint. Fingerprint authentication supports multiple trust levels. For details about the classification principles, see [Principles for Classifying Biometric Authentication Trust Levels](../../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels). It is applicable to medium-security scenarios. The advantage is that the operation is simple and quick. The disadvantage is that the device must be equipped with a fingerprint sensor, and wet hands or fingerprint abrasion may affect the recognition effect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## COMPANION_DEVICE

```TypeScript
COMPANION_DEVICE = 64
```

Companion device authentication. It indicates that the user completes the authentication through the companion device. Companion device authentication supports multiple trust levels. For details about the classification principles, see [Principles for Classifying Biometric Authentication Trust Levels](../../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
