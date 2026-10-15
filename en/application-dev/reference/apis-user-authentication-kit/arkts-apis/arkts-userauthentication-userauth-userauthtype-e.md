# UserAuthType

```TypeScript
enum UserAuthType
```

Enumerates the identity authentication types. This enum defines the authentication types supported by the system, including PIN authentication and biometric authentication (face and fingerprint). When initiating authentication, an application needs to specify the authentication type list, and the user can select any of the authentication types to complete the authentication. The security strength and user experience vary depending on authentication types. The application needs to select a proper authentication type based on service scenarios.

**Since:** 8

<!--Device-userAuth-enum UserAuthType--><!--Device-userAuth-enum UserAuthType-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## COMPANION_DEVICE

```TypeScript
COMPANION_DEVICE = 64
```

Companion device authentication. It indicates that the user completes authentication through a worn companion device. Companion device authentication supports multiple authentication trust levels. For details about the classification principle, see [Principles for Classifying Biometric Authentication Trust Levels](../../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels).

**Note:** Concurrent authentication with other authentication types (**PIN**\/**FACE**\/**FINGERPRINT**) is not supported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-UserAuthType-COMPANION_DEVICE = 64--><!--Device-UserAuthType-COMPANION_DEVICE = 64-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## FACE

```TypeScript
FACE = 2
```

Face authentication. It indicates that the user completes authentication through face recognition, and the system verifies the match between the user's facial features and the enrolled face. Face authentication supports different levels of liveness detection. For details about the classification principle, see [Principles for Classifying Biometric Authentication Trust Levels](../../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels). The advantage is convenient user experience, but the disadvantage is that there are certain requirements on the device and lighting conditions.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthType-FACE = 2--><!--Device-UserAuthType-FACE = 2-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## FINGERPRINT

```TypeScript
FINGERPRINT = 4
```

Fingerprint authentication. It indicates that the user completes authentication through the fingerprint sensor, and the system verifies the match between the user's fingerprint features and the enrolled fingerprint. Fingerprint authentication supports multiple authentication trust levels. For details about the classification principle, see [Principles for Classifying Biometric Authentication Trust Levels](../../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels). It is applicable to medium-security scenarios. The advantage is that the operation is simple and quick. The disadvantage is that the device must be equipped with a fingerprint sensor, and wet hands or fingerprint abrasion may affect the recognition effect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthType-FINGERPRINT = 4--><!--Device-UserAuthType-FINGERPRINT = 4-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## PIN

```TypeScript
PIN = 1
```

PIN authentication. It indicates that the user enters the PIN to complete authentication. PIN authentication offers high security, with an authentication trust level up to ATL4, and is suitable for high-security scenarios such as payment and important operation confirmation. The user needs to enter the password manually, which is less convenient than biometric authentication.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthType-PIN = 1--><!--Device-UserAuthType-PIN = 1-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
