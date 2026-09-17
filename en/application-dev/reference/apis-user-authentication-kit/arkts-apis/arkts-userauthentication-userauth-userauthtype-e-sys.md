# UserAuthType

Enumerates the identity authentication types. This enum defines the authentication types supported by the system, including PIN authentication and biometric authentication (face and fingerprint). When initiating authentication, an application needs to specify the authentication type list, and the user can select any of the authentication types to complete the authentication. The security strength and user experience vary depending on authentication types. The application needs to select a proper authentication type based on service scenarios.

**Since:** 8

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## PRIVATE_PIN

```TypeScript
PRIVATE_PIN = 16
```

Privacy PIN. It is a special PIN authentication type, which is generally used for secondary access control after the screen is unlocked. (That is, after the device is unlocked, the user needs to be authenticated again before accessing specific apps or content.) For example, a user can use the privacy PIN to protect the application lock (the application lock is a secondary verification function for application startup, which can prevent others from opening the user's application), so as to prevent family members who know the lock screen password from accessing some applications of the user.

**Since:** 14

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.
