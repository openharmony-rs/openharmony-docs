# UserAuthTipCode

Enumerates the intermediate states of identity authentication. This enum is used to describe various intermediate states during authentication, including authentication failure, timeout, lockout, and loading and release of the authentication screen. Applications can subscribe to these intermediate states through the [on('authTip')](arkts-userauthentication-userauth-userauthinstance-i.md#onauthtip) API to provide more refined user feedback and status awareness during authentication.

**Since:** 20

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## COMPARE_FAILURE

```TypeScript
COMPARE_FAILURE = 1
```

The authentication fails. This state occurs because the user's biometric features do not match the registered credential. It is triggered each time the authentication fails. Your application can prompt the user to try again based on this state.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## TIMEOUT

```TypeScript
TIMEOUT = 2
```

The authentication has timed out. This state usually occurs because the user has not completed the authentication interaction within the specified time (for example, the user has not entered the password in time or has not looked straight at the camera lens).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## TEMPORARILY_LOCKED

```TypeScript
TEMPORARILY_LOCKED = 3
```

The authentication is temporarily locked. When this state occurs, users can attempt to perform authentication only after the lockout duration expires. The temporary lockout status is usually triggered by multiple consecutive authentication failures.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## PERMANENTLY_LOCKED

```TypeScript
PERMANENTLY_LOCKED = 4
```

The authentication is permanently locked. When this state occurs, automatic unlocking is unavailable. Users must use PIN authentication to unlock the authenticator before using the authentication type. The permanent lockout status is usually triggered by failed authentication attempts during the temporary lockout period.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## WIDGET_LOADED

```TypeScript
WIDGET_LOADED = 5
```

The identity authentication page is loaded. This state indicates that the authentication widget is successfully loaded and displayed, and the user can start authentication interaction. The application can perform UI-related initialization operations after this state is triggered.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## WIDGET_RELEASED

```TypeScript
WIDGET_RELEASED = 6
```

The current identity authentication page is switched to another authentication page or the identity authentication component is closed. This state indicates that the authentication widget has been released. The application can perform follow-up operations, such as displaying another window, after this state is triggered. When using the application modal dialog for authentication on a PC/2-in-1 device, you are advised to subscribe to this status to ensure that the widget is completely released before performing other operations.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## COMPARE_FAILURE_WITH_FROZEN

```TypeScript
COMPARE_FAILURE_WITH_FROZEN = 7
```

The authentication fails and authentication freezing is triggered. This state indicates that the number of authentication failures reaches the threshold and the authenticator is locked. This state contains both authentication failure and freezing information. Your application can prompt the user with the corresponding unlock method based on the lockout type (temporary or permanent).

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
