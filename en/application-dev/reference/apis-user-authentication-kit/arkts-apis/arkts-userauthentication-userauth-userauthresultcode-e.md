# UserAuthResultCode

```TypeScript
enum UserAuthResultCode
```

Enumerates the authentication result codes. They include all success codes and error codes for user authentication operations. The application can determine the authentication result based on the return code and take corresponding measures.

**Since:** 9

<!--Device-userAuth-enum UserAuthResultCode--><!--Device-userAuth-enum UserAuthResultCode-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## BUSY

```TypeScript
BUSY = 12500007
```

The system is busy. It indicates that the authentication service is busy processing other requests. You are advised to try again later.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-BUSY = 12500007--><!--Device-UserAuthResultCode-BUSY = 12500007-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## CANCELED

```TypeScript
CANCELED = 12500003
```

The authentication is canceled. It indicates that the user or the system cancels the authentication. The application can determine whether to initiate the authentication again based on the service logic.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-CANCELED = 12500003--><!--Device-UserAuthResultCode-CANCELED = 12500003-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## CANCELED_FROM_WIDGET

```TypeScript
CANCELED_FROM_WIDGET = 12500011
```

The user cancels the system authentication mode and selects the application-defined authentication. It indicates that the user taps the navigation button on the authentication API and selects the custom authentication mode provided by the application. The application needs to bring up the custom authentication API.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-CANCELED_FROM_WIDGET = 12500011--><!--Device-UserAuthResultCode-CANCELED_FROM_WIDGET = 12500011-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## FAIL

```TypeScript
FAIL = 12500001
```

The authentication fails. It indicates that the user characteristics do not match the enrolled credentials. The possible cause is that the user input is incorrect or an unenrolled credential is used. It is recommended that the user be prompted to try again.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-FAIL = 12500001--><!--Device-UserAuthResultCode-FAIL = 12500001-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## GENERAL_ERROR

```TypeScript
GENERAL_ERROR = 12500002
```

A general operation error occurs. It indicates that an unknown error occurs during authentication. You are advised to try again later or contact the system administrator.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-GENERAL_ERROR = 12500002--><!--Device-UserAuthResultCode-GENERAL_ERROR = 12500002-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 12500008
```

The parameter verification fails. It indicates that the passed parameters do not meet the requirements, for example, the parameter type is incorrect or the parameter value is out of range. You are advised to check the parameters and call the API again.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-UserAuthResultCode-INVALID_PARAMETERS = 12500008--><!--Device-UserAuthResultCode-INVALID_PARAMETERS = 12500008-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## LOCKED

```TypeScript
LOCKED = 12500009
```

The authenticator is locked. It indicates that the authenticator enters the freeze state because authentication fails for multiple consecutive times. The user needs to wait until the freeze is removed or use the PIN to unlock before continuing authentication. You can call [getAuthLockState](arkts-userauthentication-userauth-getauthlockstate-f.md) to query the specific freeze state.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-LOCKED = 12500009--><!--Device-UserAuthResultCode-LOCKED = 12500009-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## NOT_ENROLLED

```TypeScript
NOT_ENROLLED = 12500010
```

The user has not enrolled the specified system identity authentication credential. It indicates that the user has not enrolled the requested authentication type (for example, fingerprint authentication is requested but the user has not enrolled a fingerprint). You are advised to guide the user to enroll the corresponding credential first.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-NOT_ENROLLED = 12500010--><!--Device-UserAuthResultCode-NOT_ENROLLED = 12500010-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## PIN_EXPIRED

```TypeScript
PIN_EXPIRED = 12500013
```

The lock screen password has expired. It indicates that the system lock screen password has expired (for example, an enterprise policy requires the password to be changed periodically). The user needs to update the lock screen password before continuing to use the authentication function.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-PIN_EXPIRED = 12500013--><!--Device-UserAuthResultCode-PIN_EXPIRED = 12500013-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## SUCCESS

```TypeScript
SUCCESS = 12500000
```

The operation is successful. It indicates that the user authentication is successful and the authentication token is valid. The application can use the returned token to perform subsequent security operations.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-SUCCESS = 12500000--><!--Device-UserAuthResultCode-SUCCESS = 12500000-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## TIMEOUT

```TypeScript
TIMEOUT = 12500004
```

The authentication has timed out. It indicates that the user does not complete the authentication interaction within the specified time (for example, the user does not enter the password in time or does not look at the camera). You are advised to prompt the user to try again and pay attention to the operation time limit.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-TIMEOUT = 12500004--><!--Device-UserAuthResultCode-TIMEOUT = 12500004-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## TRUST_LEVEL_NOT_SUPPORT

```TypeScript
TRUST_LEVEL_NOT_SUPPORT = 12500006
```

The authentication trust level is not supported. It indicates that the specified authentication trust level is higher than the highest level that the current authentication type can achieve. You are advised to lower the authentication trust level or use a more secure authentication type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-TRUST_LEVEL_NOT_SUPPORT = 12500006--><!--Device-UserAuthResultCode-TRUST_LEVEL_NOT_SUPPORT = 12500006-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## TYPE_NOT_SUPPORT

```TypeScript
TYPE_NOT_SUPPORT = 12500005
```

The authentication type is not supported. It indicates that the current device does not support the specified authentication type. For example, the device does not have a fingerprint sensor but the fingerprint authentication is requested. You are advised to check the device capability or change the authentication type.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UserAuthResultCode-TYPE_NOT_SUPPORT = 12500005--><!--Device-UserAuthResultCode-TYPE_NOT_SUPPORT = 12500005-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
