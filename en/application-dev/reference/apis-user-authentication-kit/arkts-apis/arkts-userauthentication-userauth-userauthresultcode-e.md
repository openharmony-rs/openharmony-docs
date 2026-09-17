# UserAuthResultCode

Enumerates the authentication result codes. They include all success codes and error codes for user authentication operations. The application can determine the authentication result based on the return code and take corresponding measures.

**Since:** 9

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## SUCCESS

```TypeScript
SUCCESS = 12500000
```

The operation is successful. It indicates that the user authentication is successful and the authentication token is valid. The application can use the returned token to perform subsequent security operations.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## FAIL

```TypeScript
FAIL = 12500001
```

The authentication fails. It indicates that the user characteristics do not match the enrolled credentials. The possible cause is that the user input is incorrect or an unenrolled credential is used. It is recommended that the user be prompted to try again.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## GENERAL_ERROR

```TypeScript
GENERAL_ERROR = 12500002
```

A general operation error occurred. It indicates that an unknown error occurs during authentication. It is recommended that the user be prompted to try again later or contact the system administrator.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## CANCELED

```TypeScript
CANCELED = 12500003
```

The authentication is canceled. It indicates that the user or the system cancels the authentication. The application can determine whether to initiate the authentication again based on the service logic.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## TIMEOUT

```TypeScript
TIMEOUT = 12500004
```

The authentication has timed out. It indicates that the user does not complete the authentication interaction within the specified time (for example, the user does not enter the password in time or does not look at the camera). You are advised to prompt the user to try again and pay attention to the operation time limit.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## TYPE_NOT_SUPPORT

```TypeScript
TYPE_NOT_SUPPORT = 12500005
```

The authentication type is not supported. It indicates that the current device does not support the specified authentication type. For example, the device does not have a fingerprint sensor but the fingerprint authentication is requested. You are advised to check the device capability or change the authentication type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## TRUST_LEVEL_NOT_SUPPORT

```TypeScript
TRUST_LEVEL_NOT_SUPPORT = 12500006
```

The authentication trust level is not supported. It indicates that the specified authentication trust level is higher than the highest level supported by the current authentication type. You are advised to lower the authentication trust level or use a more secure authentication type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## BUSY

```TypeScript
BUSY = 12500007
```

The system is busy. It indicates that the authentication service is busy processing other requests. You are advised to try again later.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 12500008
```

Parameter verification failed. It indicates that the input parameter does not meet the requirements, for example, the parameter type is incorrect or the parameter value is out of range. You are advised to check the parameter and call the API again.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## LOCKED

```TypeScript
LOCKED = 12500009
```

The authentication executor is locked. It indicates that the authenticator is locked due to consecutive authentication failures. The user can continue the authentication only after waiting for unlocking or using the PIN. You can call [getAuthLockState](arkts-userauthentication-userauth-getauthlockstate-f.md) to query the lock status.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## NOT_ENROLLED

```TypeScript
NOT_ENROLLED = 12500010
```

The user has not enrolled the specified system identity authentication credential. It indicates that the user has not enrolled the requested authentication type. For example, the fingerprint authentication is requested but the user has not enrolled the fingerprint. You are advised to guide the user to register the corresponding credential first.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## CANCELED_FROM_WIDGET

```TypeScript
CANCELED_FROM_WIDGET = 12500011
```

The user cancels the system authentication and selects a custom authentication of the application. It indicates that the user taps the navigation button on the authentication screen and chooses to use the custom authentication type provided by the application. The application needs to launch the custom authentication page.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## PIN_EXPIRED

```TypeScript
PIN_EXPIRED = 12500013
```

The PIN has expired. It indicates that the system PIN has expired. For example, the enterprise policy requires that the PIN be changed periodically. In this case, the user needs to change the PIN before using the authentication function.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
