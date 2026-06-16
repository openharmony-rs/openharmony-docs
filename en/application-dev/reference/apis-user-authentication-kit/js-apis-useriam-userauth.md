# @ohos.userIAM.userAuth (User Authentication)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

## Overview

The **userAuth** module is the core module for user identity authentication in OpenHarmony. It provides identity authentication capabilities in scenarios such as device unlocking, payment verification, and app login.

This module supports multiple BioAuthn modes (face and fingerprint) and password authentication (PIN), and provides different levels of security trust. Starting from API version 26.0.0, the companion device authentication mode is added.

This module applies to the following scenarios:
- Device unlocking authentication.
- Financial payment verification.
- App login protection.
- Confirmation of sensitive operations.


> **NOTE**<br>
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Key Classes and APIs

### Key Enums

- **[UserAuthType](#userauthtype8)**: Enumerates the authentication modes (PIN, FACE, FINGERPRINT, and COMPANION_DEVICE).
- **[AuthTrustLevel](#authtrustlevel8)**: Enumerates the authentication trust levels (ATL1 to ATL4).
- **[UserAuthResultCode](#userauthresultcode9)**: Enumerates the authentication result codes.
- **[ReuseMode](#reusemode12)**: Enumerates the authentication result reuse modes.
- **[UserAuthTipCode](#userauthtipcode20)**: Enumerates the authentication prompt codes.

### Key APIs

- **[AuthParam](#authparam10)**: Provides the authentication parameters, including the challenge value, authentication mode list, trust level, and reuse information.
- **[WidgetParam](#widgetparam10)**: Provides the parameters for displaying the authentication component, including the title, navigation button text, and window mode.
- **[UserAuthResult](#userauthresult10)**: authentication result API, which contains the result code, authentication token, and authentication mode.
- **[ReuseUnlockResult](#reuseunlockresult12)**: API for reusing authentication result information.
- **[EnrolledState](#enrolledstate12)**: API for the status of registered credentials.
- **[AuthLockState](#authlockstate22)**: API for the authentication lock status.

### Core

- **[UserAuthInstance](#userauthinstance10)**: user authentication instance class, which provides capabilities such as authentication execution, cancellation, and event subscription.

![Class relationship diagram](figures/uml_userauth.png)

## APIs Called in Pairs

The typical process of using the userAuth module for identity authentication is as follows:

```ts
// The following is the pseudocode for describing the calling logic. Only the steps are described, and no detailed executable code is provided.
// 1. Check whether the authentication capability is available.
userAuth.getAvailableStatus(userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL3);

// 2. Obtain the authentication instance.
let authInstance = userAuth.getUserAuthInstance({
  challenge: new Uint8Array([]), // The challenge is used to prevent replay attacks. It must be obtained using the secure random number generator.
  authType: [userAuth.UserAuthType.FACE, userAuth.UserAuthType.PIN],
  authTrustLevel: userAuth.AuthTrustLevel.ATL3
});

// 3. Subscribe to the authentication result event.
authInstance.on('result', (result: userAuth.UserAuthResult) => {
  // Process the authentication result.
});

// 4. (Optional) Subscribe to the authentication prompt event.
authInstance.on('authTip', (tipCode: userAuth.UserAuthTipCode) => {
  // Process the authentication prompt.
});

// 5. Start authentication.
authInstance.start();

// 6. (Optional) Cancel the subscription after the authentication is complete.
authInstance.off('result');
authInstance.off('authTip');
```

**Process of querying the authentication lockout status:**

```javascript
// The following is the pseudocode for describing the calling logic. It provides only the step description and does not provide detailed executable code.
// 1. Query the authentication lockout status.
let lockState = await userAuth.getAuthLockState(userAuth.UserAuthType.FACE);

// 2. Determine whether to perform authentication based on the lockout status.
if (!lockState.isLocked) {
  // Perform the authentication process.
}
```

## Modules to Import

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
```

## Constant

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name       | Type  | Value  | Description      |
| ----------- | ---- | ---- | ---------- |
| MAX_ALLOWABLE_REUSE_DURATION<sup>12+</sup>     | number | 300000   | Maximum validity period of the reuse unlock authentication result. The value is 300000 ms (5 minutes). This constant is used to limit the maximum validity period of the reuse authentication result, preventing security risks caused by using an expired authentication result for a long time. This constant can be used as the maximum value of the reuseDuration parameter in [ReuseUnlockResult](#reuseunlockresult12).<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| PERMANENT_LOCKOUT_DURATION<sup>22+</sup>      | number | 0x7fffffff | Permanent lockout duration, in milliseconds. The value is **0x7fffffff**. When the number of failed authentication attempts reaches the upper limit, the authenticator will be permanently locked out. In this case, the authenticator can be unlocked only after the user enters the correct PIN. This value is used to identify the permanent lockout status of the authenticator, which can be returned by the lockoutDuration field in [AuthLockState](#authlockstate22).<br> **Atomic service API**: This API can be used in atomic services since API version 22.|

## AuthLockState<sup>22+</sup>

Enumerates the lockout status of an identity authentication type. This API is used to query the current frozen status of a specified authentication mode (such as face, fingerprint, or PIN), including whether the authentication mode is frozen, the number of remaining attempts, and the frozen duration. If a user fails to be authenticated for multiple times, the authenticator may be temporarily or permanently frozen. The application can display a message to the user based on the frozen status.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name        | Type   | Read-Only| Optional| Description                |
| ------------ | ---------- | ---- | ---- | -------------------- |
| isLocked       | boolean | No  |  No| Whether the authentication is locked. The value true indicates that the authentication mode is frozen, and the user cannot use this authentication mode for identity authentication. The value false indicates that the authentication mode is not frozen, and the user can use this authentication mode. The frozen status is usually triggered by consecutive authentication failures.|
| remainingAuthAttempts        | number | No  |  No| Number of remaining attempts before the authentication is locked. The maximum value is **5**. The value decreases by 1 each time the authentication fails. When the value decreases to 0, the authenticator will be frozen. This parameter is valid only when isLocked is set to false.|
| lockoutDuration        | number | No  |  No| Remaining lockout duration, in milliseconds. This parameter is valid only when isLocked is set to true.<br>If the authentication mode is permanently frozen, the value is [PERMANENT_LOCKOUT_DURATION](#constant), indicating that the authenticator has been permanently locked. In this case, the user needs to use the PIN to unlock the authenticator before using the authentication mode. If the authentication mode is temporarily frozen, the value is the actual remaining frozen duration. After the frozen duration ends, the user can continue to attempt authentication.|

## UserAuthTipCode<sup>20+</sup>

Enumerates the intermediate states of identity authentication. This enumeration describes various intermediate states during the authentication process, including authentication failure, timeout, frozen state, and loading and releasing of the authentication screen. An application can subscribe to these intermediate states through the [on('authTip')](#onauthtip20) API to provide more refined user feedback and status awareness during the authentication process.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name               | Value  | Description      |
| -----------        | ---- | ---------- |
| COMPARE_FAILURE    | 1    | Authentication failed. Indicates that the current authentication attempt fails, and the user's features do not match the registered credentials. This state is triggered each time the authentication fails. The application can prompt the user to try again based on this state.|
| TIMEOUT            | 2    | The authentication has timed out. The authentication operation times out, usually because the user fails to complete the authentication interaction within the specified period (for example, the user fails to enter the password in time or fails to look at the camera lens).|
| TEMPORARILY_LOCKED | 3    | The authentication is temporarily locked. The authenticator is temporarily frozen. The user can try to authenticate again only after the frozen period ends. Temporary freezing is usually triggered by multiple consecutive authentication failures.|
| PERMANENTLY_LOCKED | 4    | The authentication is permanently locked. The authenticator is permanently frozen. The user cannot wait for the authenticator to be automatically unlocked. Instead, the user must use the PIN to unlock the authenticator and then use the authentication mode. Permanent freezing is usually triggered by authentication failures during the temporary freezing period.|
| WIDGET_LOADED      | 5    | The identity authentication page is loaded. The authentication control has been successfully loaded and displayed. The user can start the authentication interaction. The application can perform UI-related initialization operations after this state is triggered.|
| WIDGET_RELEASED    | 6    | The current identity authentication page is switched to another authentication page or the identity authentication component is closed. The authentication control has been released. The application can perform follow-up operations, such as displaying another screen, after this state is triggered. When the authentication is performed in pop-up mode on a PC or 2-in-1 device, you are advised to subscribe to this state to ensure that other UI operations are performed only after the control is completely released.|
| COMPARE_FAILURE_WITH_FROZEN    | 7    | Authentication fails and authentication freezing is triggered. The current authentication fails, and the number of authentication failures reaches the threshold. As a result, the authenticator is frozen. This state contains both the authentication failure and freezing information. The application can display the corresponding unlock method to the user based on the freezing type (temporary or permanent).|

## EnrolledState<sup>12+</sup>

Represents the state of a credential enrolled. This API is used to describe the current status of the user's registered authentication credentials (such as face, fingerprint, and companion device), including the credential digest and quantity. The application can call the [getEnrolledState](#userauthgetenrolledstate12) API to query the credential status, and detect whether the user's credentials have changed (for example, whether a fingerprint, face, or companion device is added or deleted) to perform corresponding service processing.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name        | Type   | Read-Only| Optional| Description                |
| ------------ | ---------- | ---- | ---- | -------------------- |
| credentialDigest       | number | No  |  No| Credential digest, which is randomly generated when a credential is added. This value is used to identify the version of the currently registered credential. It changes when a credential is added or deleted. The application can save this value and compare it with the value obtained in subsequent queries to determine whether the credential has changed.<br>**Note**: When the authentication result is reused, if the credential used for the previous authentication has been deleted, the returned value of credentialDigest may be 0.|
| credentialCount        | number | No  |  No| Number of enrolled credentials. Number of credentials of the specified type that have been registered by the current user, for example, the number of fingerprints or faces.<br>**Note**: When the authentication result is reused, if the credential used for the previous authentication has been deleted, the returned value of credentialCount may be 0.|

## ReuseMode<sup>12+</sup>

Enumerates the modes for reusing authentication results. This enumeration defines four modes for reusing the authentication result, which are used to control the conditions under which the authentication result can be reused. The application can select a proper reuse mode based on the service scenario to balance security and user experience.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name       | Value  | Description      |
| ----------- | ---- | ---------- |
| AUTH_TYPE_RELEVANT    | 1   | The device unlock authentication result can be reused within the validity period if the authentication type matches any of the authentication types specified for this authentication.<br>For example, if a user performs a service operation that requires facial authentication within the validity period after unlocking the device using face unlock, the authentication result of unlocking the device can be directly reused. However, if the user performs a service operation that requires fingerprint authentication, the authentication result cannot be reused.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| AUTH_TYPE_IRRELEVANT  | 2   | The device unlock authentication result can be reused within the validity period regardless of the authentication type.<br>For example, if a user performs a service operation that requires fingerprint or PIN authentication within the validity period after unlocking the device using face unlock, the authentication result of unlocking the device can be directly reused, without the need to perform authentication again.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT<sup>14+</sup>    | 3   | Any identity authentication result (including device unlock authentication result) can be reused within the validity period if the authentication type matches any of the authentication types specified for this authentication.<br>For example, if a user completes a payment in an application using facial authentication, and then another application initiates a service operation that requires facial authentication within the validity period, the previous authentication result can be reused. However, if the user initiates a service operation that requires fingerprint authentication, the previous authentication result cannot be reused.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT<sup>14+</sup>  | 4   | Any identity authentication result (including device unlock authentication result) can be reused within the validity period regardless of the authentication type.<br>For example, if a user uses facial authentication to complete an operation in an application, the authentication result can be reused when another application initiates any type of authentication operation within the validity period.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|

## ReuseUnlockResult<sup>12+</sup>

Represents information about the authentication result reuse. This API is used to set parameters related to the reuse of authentication results, including the reuse mode and validity period. By properly configuring the reuse of authentication results, you can improve user experience and avoid frequent repeated authentication while ensuring security.

> **NOTE**<br>
>
> If the credential changes within the reuse duration after a successful identity authentication (including device unlock authentication), the authentication result can still be reused and the actual **EnrolledState** is returned in the authentication result. If the identity authentication credential used in the previous authentication has been deleted when the authentication result is reused:
>
> - If the face or fingerprint is deleted, the authentication result can still be reused, but the values of credentialCount and credentialDigest in the returned EnrolledState are both 0.
> - If the screen lock password is deleted, the reuse will fail.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name        | Type  | Read-Only| Optional| Description                |
| ------------ | ---------- | ---- | ---- | -------------------- |
| reuseMode        | [ReuseMode](#reusemode12) | No| No  | Authentication result reuse mode. Select a proper reuse mode based on the security requirements of the service scenario.<br>- AUTH_TYPE_RELEVANT(1): Only the device unlocking result that matches the authentication mode is reused. This mode provides the highest security.<br>- AUTH_TYPE_IRRELEVANT(2): Any type of device unlocking result is reused. This mode is applicable to scenarios with medium security requirements.<br>- CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT(3): Any authentication result that matches the authentication mode is reused. This mode is applicable to cross-application scenarios.<br>- CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT(4): Any authentication result is reused. This mode provides the lowest security but optimal user experience.      |
| reuseDuration    | number | No| No| Reuse duration of the authentication result, in milliseconds. The value must be greater than 0 and cannot exceed the maximum value, which is specified by the constant 300000 (that is, 5 minutes). You are advised to set a proper duration based on the service scenario:<br>- Advanced security conditional access in all scenarios (such as payment): You are advised to set a short duration (for example, 30 seconds to 1 minute).<br>- Medium security scenarios (such as app login): You are advised to set a medium duration (for example, 2 to 3 minutes).<br>- Low security scenarios (such as data query): You can use the maximum duration.|

## userAuth.getAuthLockState<sup>22+</sup>

getAuthLockState(authType: UserAuthType): Promise\<AuthLockState\>

Queries the lockout state of the specified authentication type. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name        | Type                              | Mandatory| Description                      |
| -------------- | ---------------------------------- | ---- | -------------------------- |
| authType       | [UserAuthType](#userauthtype8)     | Yes  | Authentication type.|

**Return value**

| Type                 | Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Promise&lt;[AuthLockState](#authlockstate22)&gt; | Promise used to return the result. An error is reported when the operation fails.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message|
| -------- | ------- |
| 201 | Permission denied. |
| 12500002 | General operation error. |
| 12500005 | The authentication type is not supported. |
| 12500008 | The parameter is out of range. |
| 12500010 | The type of credential has not been enrolled. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let queryType = userAuth.UserAuthType.PIN;
let authLockState : userAuth.AuthLockState = {
  isLocked : false,
  remainingAuthAttempts : 0,
  lockoutDuration : 0
}

userAuth.getAuthLockState(queryType)
  .then((result: userAuth.AuthLockState) => {
    authLockState = result;
    console.info('get auth lock state successfully.');
  })
  .catch((err: BusinessError) => {
    console.info(`get auth lock state failed, err code is : ${err?.code}, err message is : ${err?.message}`);
  })
```

## userAuth.getEnrolledState<sup>12+</sup>

getEnrolledState(authType: UserAuthType): EnrolledState

Obtains the credential state. This API is used to obtain the credential registration information of a specified authentication mode, including the credential digest and quantity. The application can compare the current query result with the previously saved result to determine whether the user has added or deleted credentials, and then perform corresponding service processing.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name        | Type                              | Mandatory| Description                      |
| -------------- | ---------------------------------- | ---- | -------------------------- |
| authType       | [UserAuthType](#userauthtype8)     | Yes  | Authentication type. Type of the credential to be queried. The value can be FACE (face), FINGERPRINT (fingerprint), PIN (PIN), or COMPANION_DEVICE (companion device). When the PIN is queried, the overall status of the PIN is returned, instead of the number of individual PINs.|

**Return value**

| Type                 | Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| [EnrolledState](#enrolledstate12) | Credential state obtained if the operation is successful. The value contains credentialDigest (credential digest) and credentialCount (credential count). The application can save the credentialDigest value and compare it with the subsequent query result to detect credential changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message|
| -------- | ------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. |
| 12500002 | General operation error. |
| 12500005 | The authentication type is not supported. |
| 12500010 | The type of credential has not been enrolled. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enrolledState = userAuth.getEnrolledState(userAuth.UserAuthType.FACE);
  console.info('get current enrolled state successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`get current enrolled state failed, Code is ${err?.code}, message is ${err?.message}`);
}
```

## AuthParam<sup>10+</sup>

Defines the user authentication parameters. This API is used to configure user authentication parameters, including the challenge value, authentication mode list, authentication trust level, and authentication result reuse configuration. These parameters can be properly configured to meet authentication requirements in different service scenarios.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name          | Type                              | Read-Only| Optional| Description                                                        |
| -------------- | ---------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| challenge      | Uint8Array                         |  No |  No | Random challenge value, which can be used to prevent replay attacks. It cannot exceed 32 bytes and can be passed in **Uint8Array([])** format. You are advised to use the random number generated by the [crypto framework](../apis-crypto-architecture-kit/js-apis-cryptoFramework.md) as the challenge value to enhance security. After the authentication is successful, the challenge value is included in the authentication token. The service can verify the challenge value in the token to confirm the validity of the authentication result.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| authType       | [UserAuthType](#userauthtype8)[]   |  No |  No | Authentication type list, which specifies the types of authentication provided on the user authentication page. Multiple authentication modes can be specified at the same time, for example, [UserAuthType.PIN, UserAuthType.FACE, UserAuthType.FINGERPRINT]. The user can select any of them to complete the authentication. The selection of the authentication mode affects the matching conditions for authentication result reuse. Currently, device authentication and other authentication modes cannot be initiated at the same time.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| authTrustLevel | [AuthTrustLevel](#authtrustlevel8) |  No |  No | Authentication trust level. The authentication trust level determines the security strength of the authentication. Select a proper level based on the security requirements of the service scenario.<br>- ATL1: applicable to low-security scenarios, such as service risk control and general personal data query.<br>- ATL2: applicable to medium-security scenarios, such as app login and maintaining the screen-unlocked state of the device.<br>- ATL3: applicable to advanced security scenarios, such as device unlocking.<br>- ATL4: It is applicable to all scenarios of advanced security conditional access, such as small-amount payment.<br>For details, see [Principles for Classifying Biometric Authentication Trust Levels](../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels).<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| reuseUnlockResult<sup>12+</sup> | [ReuseUnlockResult](#reuseunlockresult12) |  No |  Yes | Information about the authentication result reuse. After this parameter is set, if the reuse conditions are met, the system directly returns the previous authentication result, and the user does not need to perform authentication interaction again. By default, the result cannot be reused. Enabling authentication result reuse can improve user experience. However, you should properly configure the reuse mode and validity period based on the security requirements of the service scenario.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| skipLockedBiometricAuth<sup>20+</sup> | boolean |  No |  Yes | Whether to skip the authentication mode that has been locked and automatically switch to another authentication mode. If no authentication mode can be switched to, the component is disabled and an authentication freezing error code is returned.<br>- true: When the biometric authentication is frozen, skip the countdown screen and directly switch to another authentication mode (for example, from the frozen fingerprint authentication to the face or PIN authentication). This mode is applicable to scenarios where authentication needs to be completed quickly.<br>- false (default): The user cannot skip the countdown screen. The user can continue to use the authentication mode or manually switch to another authentication mode only after the countdown ends.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## WidgetParam<sup>10+</sup>

Represents the information presented on the user authentication page. This API is used to configure the display style and interaction mode of the authentication screen, including the title, navigation button text, and window mode. By properly setting these parameters, you can provide clear authentication guidance and good interaction experience for users.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name                | Type                               | Read-Only| Optional| Description                                                        |
| -------------------- | ----------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| title                | string                              |  No |  No | Title of the user authentication page, which cannot be empty or exceed 500 characters. You are advised to set it to the authentication purpose, such as payment or application login. The title is displayed on the authentication screen to help users understand the purpose of the current authentication, improving user trust and cooperation.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| navigationButtonText | string                              |  No |  Yes | Text on the navigation button. It cannot exceed 60 characters. The button can be clicked to trigger a custom operation, such as redirecting to a custom authentication screen or canceling the authentication. This parameter is supported in the single-fingerprint and single-face scenarios. Since API version 18, this parameter is also supported in the face+fingerprint combined authentication scenario. By default, the custom navigation button is not displayed.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| uiContext<sup>18+</sup>            | Context               |  No |  Yes | The identity authentication dialog box is displayed in a pop-up window of the widget application. This parameter is supported only on 2-in-1 devices. After a valid uiContext is passed, the authentication dialog box is displayed in a pop-up window of the widget application. After the authentication result is returned, the application needs to obtain the widget release message (subscribe to the [on('authTip')](#onauthtip20) event and wait for the WIDGET_RELEASED state) before displaying other windows. If this parameter is not specified or the device is of other types, the identity authentication dialog box is displayed in a pop-up window of the system. In this case, the application can directly perform the follow-up procedure after the widget is released.<br>**Default value**: The identity authentication dialog box is displayed in a pop-up window of the system.<br> **Atomic service API**: This API can be used in atomic services since API version 18.|

## UserAuthResult<sup>10+</sup>

Represents the user authentication result. If the authentication is successful, the authentication mode and token information are returned. If the authentication fails, the corresponding error code is returned. This API is used to describe the result information after the authentication is complete. The application can obtain the result through the onResult callback of [IAuthCallback](#iauthcallback10).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name    | Type                          | Read-Only| Optional| Description                                                        |
| -------- | ------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| result   | number                         |  No |  No | User authentication result. If the operation is successful, SUCCESS(12500000) is returned. If the operation fails, the corresponding error code is returned. The error codes are as follows:<br>- FAIL(12500001): The authentication fails.<br>- CANCELED(12500003): The authentication is canceled.<br>- TIMEOUT(12500004): The authentication times out.<br>- LOCKED(12500009): The authenticator is locked.<br>- NOT_ENROLLED(12500010): The credential is not registered.<br>- PIN_EXPIRED(12500013): The screen lock password has expired.<br>For details about the error codes, please refer to [UserAuthResultCode](#userauthresultcode9).|
| token    | Uint8Array                     |  No |  Yes | When the authentication is successful, the token information is returned. The token contains the user identity authentication credential and can be used for subsequent security operation verification (such as payment confirmation and sensitive data access). The maximum length of the token is 1024 bytes. The token contains the challenge value used during authentication. The service can verify the challenge value to prevent replay attacks.|
| authType | [UserAuthType](#userauthtype8) |  No |  Yes | When the authentication is successful, the authentication mode of the primary use is returned. If multiple authentication modes are specified in the authType field of [AuthParam](#authparam10), this field identifies the authentication mode that the user selects and completes.                          |
| enrolledState<sup>12+</sup> | [EnrolledState](#enrolledstate12) |  No |  Yes | When the authentication is successful, the status of the registered credential is returned. It contains the credential digest and quantity of the current authentication mode. The application can compare this value with the previously saved value to determine whether the user credential has changed. If the authentication result reuse function is enabled and the credential (face or fingerprint) used for previous authentication has been deleted, the values of credentialCount and credentialDigest in the returned enrolledState are both 0.|

## IAuthCallback<sup>10+</sup>

Provides callbacks to return the authentication result. This port describes the callback method of the authentication result, which is used to obtain the authentication result after the authentication is complete. By implementing the onResult method, the application can obtain the authentication token when the authentication is successful, or obtain the error code and related information when the authentication fails.

### onResult<sup>10+</sup>

onResult(result: UserAuthResult): void

Called to return the authentication result. When the authentication is successful, the token information is returned in the UserAuthResult object, which can be used for subsequent security operation verification. When the authentication fails, the error code is returned in the result field. You can take corresponding measures based on the error code, for example, asking the user to perform authentication again or instructing the user to register a credential.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name| Type                               | Mandatory| Description      |
| ------ | ----------------------------------- | ---- | ---------- |
| result | [UserAuthResult](#userauthresult10) | Yes  | Authentication result. It contains information such as the authentication result code, authentication token (when the authentication is successful), authentication mode, and credential status. The application needs to check the result.result field to determine whether the authentication is successful.<br>- If the value of result.result is SUCCESS(12500000), the authentication is successful, and the result.token can be used to perform the follow-up procedure.<br>- If the value of result.result is another value, the authentication fails. In this case, the application needs to handle the error based on the specific error code.|

**Example 1**

Initiate a lock screen password authentication request at ATL3 or higher.
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };

  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The authentication result is returned by onResult only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.on('result', {
    onResult (result) {
      console.info(`userAuthInstance callback result = ${result.result}`);
    }
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

**Example 2**

Initiate a lock screen password authentication request at ATL3 or higher, and enable the authentication result to be reused for the same type of authentication within the maximum reuse duration of device unlocking.
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

let reuseUnlockResult: userAuth.ReuseUnlockResult = {
  reuseMode: userAuth.ReuseMode.AUTH_TYPE_RELEVANT,
  reuseDuration: userAuth.MAX_ALLOWABLE_REUSE_DURATION,
}
try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
    reuseUnlockResult: reuseUnlockResult,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The authentication result is returned by onResult only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.on('result', {
    onResult (result) {
      console.info(`userAuthInstance callback result = ${result.result}`);
    }
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

**Example 3**

Initiate a lock screen password authentication request at ATL3 or higher, and enable the authentication result to be reused for any type of authentication within the maximum reuse duration of any application.
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

let reuseUnlockResult: userAuth.ReuseUnlockResult = {
  reuseMode: userAuth.ReuseMode.CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT,
  reuseDuration: userAuth.MAX_ALLOWABLE_REUSE_DURATION,
}
try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
    reuseUnlockResult: reuseUnlockResult,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The authentication result is returned by onResult only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.on('result', {
    onResult (result) {
      console.info(`userAuthInstance callback result = ${result.result}`);
    }
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## AuthTipInfo<sup>20+</sup>

Represents the intermediate authentication status. This API is used to describe various intermediate status information generated during the authentication, including the authentication mode and specific status code. The application can obtain these intermediate status information through [AuthTipCallback](#authtipcallback20) to provide more refined user feedback and status awareness during the authentication.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name    | Type                                 | Read-Only| Optional| Description                             |
| -------- | ------------------------------------ | ---- | ---- | ------------------------------------ |
| tipType | [UserAuthType](#userauthtype8)        |  No |  No | Authentication type of the intermediate status. Indicates the authentication mode that generates the current intermediate state, such as facial authentication (FACE), fingerprint authentication (FINGERPRINT), or PIN authentication (PIN). The application can provide specific tips to the user based on the authentication mode.|
| tipCode | [UserAuthTipCode](#userauthtipcode20) |  No |  No | Intermediate status. Indicates the specific intermediate state type, such as authentication failure, timeout, freezing, and UI loading or releasing. The application should provide corresponding feedback or execute corresponding processing logic based on the tip code.|

## AuthTipCallback<sup>20+</sup>

type AuthTipCallback = (authTipInfo: AuthTipInfo) => void

Defines the callback to return the intermediate authentication status. This callback is used to obtain various intermediate state information during the authentication process, including each authentication failure, frozen state, UI loading, and UI releasing. By subscribing to these intermediate states, the application can provide more refined user interaction and status management during the authentication process.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name| Type                               | Mandatory| Description      |
| ------ | -----------------------------------| ---- | ---------- |
| authTipInfo | [AuthTipInfo](#authtipinfo20)   | Yes  | Intermediate authentication status. It contains the authentication mode (tipType) and status code (tipCode). The application should perform the following operations based on the tip code:<br>- COMPARE_FAILURE(1): Prompt the user to try again.<br>- TIMEOUT(2): Prompt the user that the operation times out.<br>- TEMPORARILY_LOCKED(3): Prompt the user to wait until the frozen state is released.<br>- PERMANENTLY_LOCKED(4): Prompt the user to unlock the device using the PIN.<br>- WIDGET_LOADED(5): The authentication UI has been loaded and can be initialized.<br>- WIDGET_RELEASED(6): The authentication UI has been released and the follow-up procedure can be performed.<br>- COMPARE_FAILURE_WITH_FROZEN(7): Prompt the user that the authentication fails and the device is frozen.|

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };

  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The intermediate authentication status is returned by onAuthTip only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.on('authTip', (authTipInfo: userAuth.AuthTipInfo) => {
    console.info('userAuthInstance callback');
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## UserAuthInstance<sup>10+</sup>

Provides APIs for user authentication. The user authentication widget is supported. This API provides complete user authentication capabilities, including subscribing to authentication results and intermediate states, starting authentication, and canceling authentication. The unified authentication control provides users with a criterion-based authentication UI and consistent authentication experience.

Before using the APIs of **UserAuthInstance**, you must obtain a **UserAuthInstance** instance by using [getUserAuthInstance](#userauthgetuserauthinstance10).

> **NOTE**<br>
>
> Each UserAuthInstance instance can be used for only one authentication process. If you need to perform authentication again, you must obtain the UserAuthInstance instance again.

### on('result')<sup>10+</sup>

on(type: 'result', callback: IAuthCallback): void

Subscribes to the user authentication result. This API is used to obtain the final identity authentication result after the user completes identity authentication interaction with the authentication component. Before the authentication control disappears, the intermediate authentication failures will not be returned through this API. Only the final authentication result (success or failure) is returned through this API. If you need to detect each authentication failure and intermediate state during the entire authentication process, subscribe to the events by calling the [on('authTip')](#onauthtip20) API.

> **NOTE**<br>
>
> On PCs/2-in-1 devices, if an application initiates authentication in an application modal dialog (that is, a valid **uiContext** is passed when the user API parameter [widgetParam](#widgetparam10) is configured) and receives the authentication result, and if other windows need to be displayed, the application needs to obtain the flag message released by the component pop-up window and subscribe to the component release message (**authTipInfo.tipCode = UserAuthTipCode.WIDGET_RELEASED**) through the [on('authTip')](#onauthtip20) API.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name  | Type                             | Mandatory| Description                                      |
| -------- | --------------------------------- | ---- | ------------------------------------------ |
| type     | 'result'                          | Yes  | Event type. The value is **result**, which indicates the authentication result.|
| callback | [IAuthCallback](#iauthcallback10) | Yes  | Callback used to return the user authentication result.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                |
| -------- | ------------------------ |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed. |
| 12500002 | General operation error. |

**Example 1**

Perform user identity authentication in a system modal dialog.
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The authentication result is returned by onResult only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.on('result', {
    onResult (result) {
      console.info(`userAuthInstance callback result = ${result.result}`);
    }
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

**Example 2**

Perform user identity authentication in an application modal dialog.

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

@Entry
@Component
struct Index {
  modelApplicationAuth(): void {
    try {
      const rand = cryptoFramework.createRandom();
      const len: number = 16;
      let randData: Uint8Array | null = null;
      let retryCount = 0;
      while(retryCount < 3){
        randData = rand?.generateRandomSync(len)?.data;
        if(randData){
          break;
        }
        retryCount++;
      }
      if(!randData){
        return;
      }
      const authParam: userAuth.AuthParam = {
        challenge: randData,
        authType: [userAuth.UserAuthType.PIN],
        authTrustLevel: userAuth.AuthTrustLevel.ATL3,
      };
      const uiContext: UIContext = this.getUIContext();
      const context: Context | undefined = uiContext.getHostContext();
      const widgetParam: userAuth.WidgetParam = {
        title: 'Enter password',
        uiContext: context,
      };
      const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
      console.info('get userAuth instance successfully.');
      // The authentication result is returned by onResult only after the authentication is started by start() of UserAuthInstance.
      userAuthInstance.on('result', {
        onResult (result) {
          console.info(`userAuthInstance callback result =${result.result}`);
        }
      });
      console.info('auth on successfully.');
      userAuthInstance.start();
      console.info('auth start successfully.');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
    }
  }

  build() {
    Column() {
      Button('start auth')
        .onClick(() => {
          this.modelApplicationAuth();
        })
    }
  }
}
```

### off('result')<sup>10+</sup>

off(type: 'result', callback?: IAuthCallback): void

Unsubscribes from the user authentication result.

> **NOTE**<br>
> 
> The [UserAuthInstance](#userauthinstance10) instance used to invoke this API must be the one used to subscribe to the event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name  | Type                             | Mandatory| Description                                      |
| -------- | --------------------------------- | ---- | ------------------------------------------ |
| type     | 'result'                          | Yes  | Event type. The value is **result**, which indicates the authentication result.|
| callback | [IAuthCallback](#iauthcallback10) | No  | Callback used to return the user authentication result. If this parameter is not passed, the value passed when the [on('result')](#onresult10-1) API is called is used by default.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                |
| -------- | ------------------------ |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed. |
| 12500002 | General operation error. |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  userAuthInstance.off('result', {
    onResult (result) {
      console.info(`auth off result = ${result.result}`);
    }
  });
  console.info('auth off successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

### start<sup>10+</sup>

start(): void

Starts authentication.

> **NOTE**<br>
>
> Each **UserAuthInstance** can be used for authentication only once.

**Required permissions**:

- API version 20 or later: ohos.permission.ACCESS_BIOMETRIC or ohos.permission.USER_AUTH_FROM_BACKGROUND (This permission is available only to system apps and can be used to initiate authentication in the background.)

- API versions 10 to 19: ohos.permission.ACCESS_BIOMETRIC

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                                        |
| -------- | ------------------------------------------------ |
| 201      | Permission denied. Possible causes: <br>1.No permission to access biometric. <br>2.No permission to start authentication from background.|
| 401      | Parameter error. Possible causes: <br>1.Incorrect parameter types. |
| 12500001 | Authentication failed. <br> Applicable versions: 10 to 19                         |
| 12500002 | General operation error.                         |
| 12500003 | Authentication canceled.                         |
| 12500004 | Authentication timeout. <br> Applicable versions: 10 to 19                        |
| 12500005 | The authentication type is not supported.        |
| 12500006 | The authentication trust level is not supported. |
| 12500007 | Authentication service is busy. <br> Applicable version: 10–19                |
| 12500009 | Authentication is locked out.                    |
| 12500010 | The type of credential has not been enrolled.    |
| 12500011 | Switched to the customized authentication process.   |
| 12500013 | Operation failed because of PIN expired. <br> Applicable versions: 12+|

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

### cancel<sup>10+</sup>

cancel(): void

Cancels this authentication.

> **NOTE**<br>
>
> **UserAuthInstance** must be the instance being authenticated.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Error codes**

| ID| Error Message                       |
| -------- | ------------------------------- |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: <br>1.Incorrect parameter types. |
| 12500002 | General operation error.        |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam : userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The cancel() API can be called only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.start();
  console.info('auth start successfully.');
  userAuthInstance.cancel();
  console.info('auth cancel successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

### on('authTip')<sup>20+</sup>

on(type: 'authTip', callback: AuthTipCallback): void

Subscribes to authentication tip information. This API is used to obtain the startup and exit prompts of the central vehicle controller during the authentication process, and the user's failed authentication attempts. This API uses an asynchronous callback to return the result.

> **NOTE**<br>
>
> On PCs/2-in-1 devices, if an application initiates authentication in an application modal dialog (that is, a valid **uiContext** is passed when the user API parameter [widgetParam](#widgetparam10) is configured) and receives the authentication result, and if other windows need to be displayed, the application needs to obtain the flag message released by the component pop-up window and subscribe to the component release message (**authTipInfo.tipCode = UserAuthTipCode.WIDGET_RELEASED**) through the [on('authTip')](#onauthtip20) API.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name  | Type          | Mandatory| Description                                      |
| -------- | ------------- | ---- | ------------------------------------------ |
| type     | string        | Yes  | Event type. The supported event is **'authTip'**. This event is triggered when [start()](#start10) is called and authentication is initiated.|
| callback | [AuthTipCallback](#authtipcallback20) | Yes  | Callback used to return the intermediate authentication status.    |

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                |
| -------- | ------------------------ |
| 12500002 | General operation error. |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The intermediate authentication status is returned by onAuthTip only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.on('authTip', (authTipInfo: userAuth.AuthTipInfo) => {
    console.info('userAuthInstance callback.');
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

### off('authtip')<sup>20+</sup>

off(type: 'authTip', callback?: AuthTipCallback): void

Unsubscribes from the event for intermediate authentication status.

> **NOTE**<br>
> 
> The [UserAuthInstance](#userauthinstance10) instance used to invoke this API must be the one used to subscribe to the event.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name  | Type          | Mandatory| Description                                      |
| -------- | ------------- | ---- | ------------------------------------------ |
| type     | string        | Yes  | Event type. The supported event is **'authTip'**. This API unsubscribes from the event triggered by [on('authTip')](#onauthtip20) after the [start()](#start10) call and the initiation of authentication.|
| callback | [AuthTipCallback](#authtipcallback20) | No  | Callback used to return the intermediate authentication status. If this parameter is not passed, the value passed when the [on('authTip')](#onauthtip20) API is called is used by default.|

**Error codes**

For details about the error codes, see [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                |
| -------- | ------------------------ |
| 12500002 | General operation error. |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  userAuthInstance.off('authTip', (authTipInfo: userAuth.AuthTipInfo) => {
    console.info('userAuthInstance callback');
  });
  console.info('auth off successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## userAuth.getUserAuthInstance<sup>10+</sup>

getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance

Obtains a [UserAuthInstance](#userauthinstance10) instance for user authentication. The user authentication widget is also supported. This API is used to create a user authentication instance. After the authentication parameters and UI parameters are configured, you can start authentication and subscribe to authentication results using the returned instance object.

> **NOTE**<br>
>
> Each **UserAuthInstance** can be used for authentication only once. After the authentication is complete (regardless of whether it succeeds or fails), the instance cannot be used again.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name     | Type                         | Mandatory| Description                      |
| ----------- | ----------------------------- | ---- | -------------------------- |
| authParam   | [AuthParam](#authparam10)      | Yes  | User authentication parameters. The parameters include the challenge value, authentication mode list, authentication trust level, and authentication result reuse configuration. It is recommended that the challenge value be a random number generated by the encryption framework. Multiple authentication modes can be specified for users to choose from. The authentication trust level should be selected based on the security requirements of the service scenario.        |
| widgetParam | [WidgetParam](#widgetparam10) | Yes  | Parameters on the user authentication page. The parameters include the page title, navigation button text, window mode (system API), and pop-up window context of the application. You are advised to set the title to the authentication purpose. The navigation button text can be used to customize the authentication redirection.|

**Return value**

| Type                                   | Description                      |
| --------------------------------------- | -------------------------- |
| [UserAuthInstance](#userauthinstance10) | **UserAuthInstance** instance that supports UI. After obtaining the instance, call [on('result')](#onresult10-1) to subscribe to the authentication result, and then call [start](#start10) to start the authentication. After the authentication is complete, you can obtain the authentication result through the callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                                        |
| -------- | ------------------------------------------------ |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed.   |
| 12500002 | General operation error.                         |
| 12500005 | The authentication type is not supported.        |
| 12500006 | The authentication trust level is not supported. |

**Example**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  let userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## AuthResultInfo<sup>(deprecated)</sup>

Represents the authentication result.

> **NOTE**<br>
>
> This parameter is supported since API version 9 and deprecated since API version 11. Use [UserAuthResult](#userauthresult10) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name        | Type  | Read-Only| Optional| Description                |
| ----------- | ------ | ---- | ---- | -------------------- |
| result        | number | No| No| Authentication result.      |
| token        | Uint8Array | No| Yes| Token that has passed the user identity authentication.|
| remainAttempts  | number     | No| Yes| Number of remaining authentication attempts.|
| lockoutDuration | number     | No| Yes| Lock duration of the authentication operation, in ms.|

## TipInfo<sup>(deprecated)</sup>

Represents the tip information displayed during the authentication, which is used to provide feedback during the authentication process.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 11. Use [AuthTipInfo](#authtipinfo20) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name        | Type  | Read-Only| Optional| Description                |
| ------------ | ----- | ---- | ---- | -------------------- |
| module        | number | No| No| ID of the module that sends the tip information.      |
| tip        | number | No| No| Tip to be given during the authentication process.      |

## EventInfo<sup>(deprecated)</sup>

type EventInfo = AuthResultInfo | TipInfo

Enumerates the authentication event information types.

It consists of the fields in **Type** in the following table.

> **NOTE**<br>
>
> This parameter is supported since API version 9 and deprecated since API version 11. Use [UserAuthResult](#userauthresult10) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Type   | Description                      |
| --------- | ----------------------- |
| [AuthResultInfo](#authresultinfodeprecated)    | Authentication result. |
| [TipInfo](#tipinfodeprecated)    | Authentication tip information.     |

## AuthEventKey<sup>(deprecated)</sup>

type AuthEventKey = 'result' | 'tip'

Defines the keyword of the authentication event type. It is used as a parameter of [on](#ondeprecated).

It consists of the fields in **Type** in the following table.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 11.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Type      | Description                   |
| ---------- | ----------------------- |
| 'result' | If the first parameter of [on](#ondeprecated) is **result**, the [callback](#callbackdeprecated) returns the authentication result.|
| 'tip'    | If the first parameter of [on](#ondeprecated) is **tip**, the [callback](#callbackdeprecated) returns the authentication tip information.|

## AuthEvent<sup>(deprecated)</sup>

Provides an asynchronous callback to return the authentication event information.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 11. Use [IAuthCallback](#iauthcallback10) instead.

### callback<sup>(deprecated)</sup>

callback(result : EventInfo) : void

Called to return the authentication result or authentication tip information.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 11. Use [onResult](#onresult10) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name   | Type                      | Mandatory| Description                          |
| --------- | -------------------------- | ---- | ------------------------------ |
| result    | [EventInfo](#eventinfodeprecated)     | Yes  | Authentication result or tip information. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
// Obtain the authentication result via a callback.
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  } as userAuth.AuthEvent);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed, error = ${error}`);
  // do error.
}
// Obtain the authentication tip information via a callback.
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.on('tip', {
    callback : (result : userAuth.TipInfo) => {
      switch (result.tip) {
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_BRIGHT:
          // Do something.
          break;
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_DARK:
          // Do something.
          break;
        default:
          // do others.
      }
    }
  } as userAuth.AuthEvent);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed, error = ${error}`);
  // do error.
}
```

## AuthInstance<sup>(deprecated)</sup>

Implements user authentication.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 10. Use [UserAuthInstance](#userauthinstance10) instead.

### on<sup>(deprecated)</sup>

on : (name : AuthEventKey, callback : AuthEvent) => void

Subscribes to the user authentication events of the specified type.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 10. Use [on('result')](#onresult10-1) instead.
>
> Use the [AuthInstance](#authinstancedeprecated) instance obtained to call this API.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name   | Type                       | Mandatory| Description                      |
| --------- | -------------------------- | ---- | ------------------------- |
| name  | [AuthEventKey](#autheventkeydeprecated) | Yes  | Authentication event type. If the value is **result**, the callback returns the authentication result. If the value is **tip**, the callback returns the authentication tip information.|
| callback  | [AuthEvent](#autheventdeprecated)   | Yes  | Callback used to return the authentication result or tip information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message|
| -------- | ------- |
| 401 | Parameter error. |
| 12500002 | General operation error. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  // Subscribe to the authentication result.
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  });
  // Subscribe to authentication tip information.
  auth.on('tip', {
    callback : (result : userAuth.TipInfo) => {
      switch (result.tip) {
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_BRIGHT:
          // Do something.
          break;
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_DARK:
          // Do something.
          break;
        default:
          // do others.
      }
    }
  } as userAuth.AuthEvent);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed, error = ${error}`);
  // do error.
}
```

### off<sup>(deprecated)</sup>

off : (name : AuthEventKey) => void

Unsubscribes from the user authentication events of the specified type.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 10. Use [off('result')](#offresult10) instead.
>
> The [AuthInstance](#authinstancedeprecated) instance used to invoke this API must be the one used to subscribe to the event.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name   | Type                       | Mandatory| Description                      |
| --------- | -------------------------- | ---- | ------------------------- |
| name    | [AuthEventKey](#autheventkeydeprecated)      | Yes  | Authentication event type. If the value is **result**, the authentication result is unsubscribed from. If the value is **tip**, the authentication tip information is unsubscribed from.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message|
| -------- | ------- |
| 401 | Parameter error. |
| 12500002 | General operation error. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  // Subscribe to the authentication result.
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  });
  // Unsubscribe from the authentication result.
  auth.off('result');
  console.info('cancel subscribe authentication event successfully.');
} catch (error) {
  console.error(`cancel subscribe authentication event failed, error = ${error}`);
  // do error.
}
```

### start<sup>(deprecated)</sup>

start : () => void

Starts authentication.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 10. Use [start](#start10) instead.
>
> Use the [AuthInstance](#authinstancedeprecated) instance obtained to call this API.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message|
| -------- | ------- |
| 201 | Permission denied. |
| 401 | Parameter error. |
| 12500001 | Authentication failed. |
| 12500002 | General operation error. |
| 12500003 | The operation is canceled. |
| 12500004 | The operation is time-out.  |
| 12500005 | The authentication type is not supported. |
| 12500006 | The authentication trust level is not supported. |
| 12500007 | The authentication task is busy. |
| 12500009 | The authenticator is locked. |
| 12500010 | The type of credential has not been enrolled. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;

try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`auth failed, error = ${error}`);
}
```

### cancel<sup>(deprecated)</sup>

cancel : () => void

Cancels this authentication.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 10. Use [cancel](#cancel10) instead.
>
> Use the [AuthInstance](#authinstancedeprecated) instance obtained to call this API. The [AuthInstance](#authinstancedeprecated) instance must be the instance being authenticated.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message|
| -------- | ------- |
| 201 | Permission denied. |
| 401 | Parameter error. |
| 12500002 | General operation error. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;

try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.cancel();
  console.info('cancel auth successfully.');
} catch (error) {
  console.error(`cancel auth failed, error = ${error}`);
}
```

## userAuth.getAuthInstance<sup>(deprecated)</sup>

getAuthInstance(challenge : Uint8Array, authType : UserAuthType, authTrustLevel : AuthTrustLevel): AuthInstance

Obtains an **AuthInstance** instance for user authentication.

> **NOTE**<br>
>
> This API is supported since API version 9 and deprecated since API version 10. Use [getUserAuthInstance](#userauthgetuserauthinstance10) instead.
>
> An **AuthInstance** instance can be used for authentication only once.


**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name        | Type                                    | Mandatory| Description                    |
| -------------- | ---------------------------------------- | ---- | ------------------------ |
| challenge      | Uint8Array                               | Yes  | Challenge value. It cannot exceed 32 bytes and can be passed in Uint8Array([]) format.|
| authType       | [UserAuthType](#userauthtype8)           | Yes  | Authentication type. Currently, **FACE** and **FINGERPRINT** are supported.|
| authTrustLevel | [AuthTrustLevel](#authtrustlevel8)       | Yes  | Authentication trust level.              |

**Return value**

| Type                                   | Description        |
| --------------------------------------- | ------------ |
| [AuthInstance](#authinstancedeprecated) | **AuthInstance** instance obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message|
| -------- | ------- |
| 401 | Parameter error. |
| 12500002 | General operation error. |
| 12500005 | The authentication type is not supported. |
| 12500006 | The authentication trust level is not supported. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;

try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  console.info('get auth instance successfully.');
} catch (error) {
  console.error(`get auth instance failed, error = ${error}`);
}
```

## userAuth.getAvailableStatus<sup>9+</sup>

getAvailableStatus(authType : UserAuthType, authTrustLevel : AuthTrustLevel): void

Checks whether the specified authentication capability is supported. This API is used to check whether the current device supports the specified authentication mode and trust level, helping the app determine whether the authentication capability is available before initiating authentication. This avoids unnecessary authentication failures. If the query is successful (no error is reported), the authentication capability is available. If an error is reported, the application needs to determine the cause based on the error code and take corresponding measures.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name        | Type                              | Mandatory| Description                      |
| -------------- | ---------------------------------- | ---- | -------------------------- |
| authType       | [UserAuthType](#userauthtype8)     | Yes  | Authentication type. It specifies the authentication mode to be queried. The value can be FACE, FINGERPRINT, PIN, or COMPANION_DEVICE.<br>**Note:**<br>PIN is supported since API version 11.<br>COMPANION_DEVICE query is supported since API version 26.0.0.|
| authTrustLevel | [AuthTrustLevel](#authtrustlevel8) | Yes  | Authentication trust level. It specifies the trust level of the authentication to be queried. The valid values are ATL1(10000), ATL2(20000), ATL3(30000), and ATL4(40000). A higher level indicates a higher requirement on the liveness detection capability of the authentication scheme.      |

> The mechanism for returning the error code is as follows:
>
> Error code 12500005 is returned if the authentication executor is not registered and the specified authentication capability is not supported.
>
> Error code 12500006 is returned if the authentication executor has been registered, the authentication functionality is not disabled, but the authentication trust level is lower than that specified by the service.
>
> Error code 12500010 is returned if the authentication executor has been registered, the authentication functionality is not disabled, but the user has not enrolled credential.
>
> Error code 12500013 is returned if the authentication executor has been registered, the authentication functionality is not disabled, but the password has expired.

> **NOTE**
>
> If **getAvailableStatus** is called to check whether lock screen password authentication at ATL4 is supported for a user who has enrolled a 4-digit PIN as the lock screen password (the authentication trust level is ATL3), error code 12500010 will be returned.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message|
| -------- | ------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. |
| 12500002 | General operation error. |
| 12500005 | The authentication type is not supported. |
| 12500006 | The authentication trust level is not supported. |
| 12500010 | The type of credential has not been enrolled. |
| 12500013 | Operation failed because of PIN expired.<br>Applicable versions: 12+|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  userAuth.getAvailableStatus(userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL3);
  console.info('current auth trust level is supported');
} catch (error) {
  console.error(`current auth trust level is not supported, error = ${error}`);
}
```

## UserAuthResultCode<sup>9+</sup>

Enumerates the authentication result codes. This enumeration defines all result codes that may be returned for user authentication, including success codes and error codes. The application can determine the authentication result based on the return code and take corresponding measures.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name                   |   Value  | Description                |
| ----------------------- | ------ | -------------------- |
| SUCCESS                          | 12500000      | The operation is successful. The user identity is successfully authenticated, and the authentication token is valid. The application can use the returned token to perform subsequent security operations.<br> **Atomic service API**: This API can be used in atomic services since API version 12.    |
| FAIL                             | 12500001      | Authentication failed. The user's identity does not match the registered credential, which may be caused by incorrect user input or the use of an unregistered credential. It is recommended that the user be prompted to try again.<br> **Atomic service API**: This API can be used in atomic services since API version 12.    |
| GENERAL_ERROR                    | 12500002      | A general operation error occurred. An unknown error occurred during authentication. You are advised to try again later or contact the system administrator.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| CANCELED                         | 12500003      | The authentication is canceled. The user proactively cancels the authentication or the authentication is canceled by the system. The application can determine whether to initiate the authentication again based on the service logic.<br> **Atomic service API**: This API can be used in atomic services since API version 12.    |
| TIMEOUT                          | 12500004      | The authentication has timed out. The user fails to complete the authentication interaction within the specified time (for example, the user does not enter the password in time or does not look at the camera lens). You are advised to prompt the user to try again and pay attention to the operation time limit.<br> **Atomic service API**: This API can be used in atomic services since API version 12.    |
| TYPE_NOT_SUPPORT                 | 12500005      | The authentication type is not supported. The current device does not support the specified authentication mode. For example, the device does not support fingerprint authentication if it does not have a fingerprint sensor. You are advised to check the device capability or change the authentication mode.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| TRUST_LEVEL_NOT_SUPPORT          | 12500006      | The authentication trust level is not supported. The specified authentication level is higher than the highest level that can be achieved by the current authentication mode. You are advised to reduce the authentication level or use a more secure authentication mode.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| BUSY                             | 12500007      | The system does not respond. The authentication service is busy processing other requests. You are advised to try again later.<br> **Atomic service API**: This API can be used in atomic services since API version 12.    |
| INVALID_PARAMETERS<sup>20+</sup> | 12500008      | Parameter verification failed. The input parameter does not meet the requirements, for example, the parameter type is incorrect or the parameter value is out of range. You are advised to check the parameter and call the API again.<br> **Atomic service API**: This API can be used in atomic services since API version 20. |
| LOCKED                           | 12500009      | The authentication executor is locked. The authenticator is frozen because the authentication fails for multiple consecutive times. The user can continue the authentication only after the authenticator is unfrozen or the user enters the PIN to unlock the authenticator. You can call the [getAuthLockState](#userauthgetauthlockstate22) API to query the specific frozen state.<br> **Atomic service API**: This API can be used in atomic services since API version 12. |
| NOT_ENROLLED                     | 12500010      | The user has not enrolled the specified system identity authentication credential. It indicates that the user has not registered the requested authentication mode (for example, the user has not enrolled a fingerprint when fingerprint authentication is requested). You are advised to guide the user to register the corresponding credential first.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| CANCELED_FROM_WIDGET<sup>10+</sup> | 12500011 | The user cancels the system authentication and selects a custom authentication of the application. It indicates that the user taps the navigation button on the authentication screen and chooses to use the custom authentication mode provided by the application. The application needs to start the custom authentication screen.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| PIN_EXPIRED<sup>12+</sup> | 12500013 | The lock screen password has expired. It indicates that the system lock screen password has expired (for example, the enterprise policy requires that the password be changed periodically). The user needs to update the lock screen password before using the authentication function.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|

## UserAuth<sup>(deprecated)</sup>

Provides APIs for managing the **UserAuth** object.

### constructor<sup>(deprecated)</sup>

constructor()

A constructor used to create a **UserAuth** instance.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [getAuthInstance](#userauthgetauthinstancedeprecated) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
```

### getVersion<sup>(deprecated)</sup>

getVersion() : number

Obtains the version of this authenticator.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Return value**

| Type  | Description                  |
| ------ | ---------------------- |
| number | Authenticator version obtained.|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let version = auth.getVersion();
console.info(`auth version = ${version}`);
```

### getAvailableStatus<sup>(deprecated)</sup>

getAvailableStatus(authType : UserAuthType, authTrustLevel : AuthTrustLevel) : number

Checks whether the specified authentication capability is supported.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [getAvailableStatus](#userauthgetavailablestatus9) instead.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name        | Type                              | Mandatory| Description                      |
| -------------- | ---------------------------------- | ---- | -------------------------- |
| authType       | [UserAuthType](#userauthtype8)     | Yes  | Authentication type. Currently, **FACE** and **FINGERPRINT** are supported.|
| authTrustLevel | [AuthTrustLevel](#authtrustlevel8) | Yes  | Authentication trust level.      |

**Return value**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | Query result. If the authentication capability is supported, **SUCCESS** is returned. Otherwise, a [ResultCode](#resultcodedeprecated) is returned.|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let checkCode = auth.getAvailableStatus(userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1);
if (checkCode == userAuth.ResultCode.SUCCESS) {
  console.info('check auth support successfully.');
} else {
  console.error(`check auth support failed, code = ${checkCode}`);
}
```

### auth<sup>(deprecated)</sup>

auth(challenge: Uint8Array, authType: UserAuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array

Starts user authentication. This API uses a callback to return the result.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [start](#startdeprecated) instead.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name        | Type                                    | Mandatory| Description                    |
| -------------- | ---------------------------------------- | ---- | ------------------------ |
| challenge      | Uint8Array                               | Yes  | Challenge value, which can be passed in Uint8Array([]) format.|
| authType       | [UserAuthType](#userauthtype8)           | Yes  | Authentication type. Currently, **FACE** and **FINGERPRINT** are supported.|
| authTrustLevel | [AuthTrustLevel](#authtrustlevel8)       | Yes  | Authentication trust level.            |
| callback       | [IUserAuthCallback](#iuserauthcallbackdeprecated) | Yes  | Callback used to return the result.       |

**Return value**

| Type      | Description                                                        |
| ---------- | ------------------------------------------------------------ |
| Uint8Array | Context ID, which is used as the input parameter of [cancelAuth](#cancelauthdeprecated).|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let challenge = new Uint8Array([]);
auth.auth(challenge, userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1, {
  onResult: (result, extraInfo) => {
    try {
      console.info(`auth onResult result = ${result}`);
      if (result == userAuth.ResultCode.SUCCESS) {
        // Add the logic to be executed when the authentication is successful.
      } else {
        // Add the logic to be executed when the authentication fails.
      }
    } catch (error) {
      console.error(`auth onResult failed, error = ${error}`);
    }
  }
});
```

### cancelAuth<sup>(deprecated)</sup>

cancelAuth(contextID : Uint8Array) : number

Cancels the authentication based on the context ID.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [cancel](#canceldeprecated) instead.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name   | Type      | Mandatory| Description                                      |
| --------- | ---------- | ---- | ------------------------------------------ |
| contextID | Uint8Array | Yes  | Context ID, which is obtained by [auth](#authdeprecated).|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| number | Returns **SUCCESS** if the cancellation is successful. Returns a [ResultCode](#resultcodedeprecated) otherwise.|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

// contextId can be obtained via auth(). In this example, it is defined here.
let contextId = new Uint8Array([0, 1, 2, 3, 4, 5, 6, 7]);
let auth = new userAuth.UserAuth();
let cancelCode = auth.cancelAuth(contextId);
if (cancelCode == userAuth.ResultCode.SUCCESS) {
  console.info('cancel auth successfully.');
} else {
  console.error('cancel auth failed.');
}
```

## IUserAuthCallback<sup>(deprecated)</sup>

Provides callbacks to return the authentication result.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [AuthEvent](#autheventdeprecated) instead.

### onResult<sup>(deprecated)</sup>

onResult: (result : number, extraInfo : AuthResult) => void

Called to return the authentication result.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [callback](#callbackdeprecated) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name   | Type                      | Mandatory| Description       |
| --------- | -------------------------- | ---- | ------------------------------------------------ |
| result    | number           | Yes  | Authentication result. For details, see [ResultCode](#resultcodedeprecated).|
| extraInfo | [AuthResult](#authresultdeprecated) | Yes  | Extended information, which varies depending on the authentication result.<br>If the authentication is successful, the user authentication token will be returned in **extraInfo**.<br>If the authentication fails, the remaining number of authentication times will be returned in **extraInfo**.<br>If the authentication executor is locked, the freeze time will be returned in **extraInfo**.|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let challenge = new Uint8Array([]);
auth.auth(challenge, userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1, {
  onResult: (result, extraInfo) => {
    try {
      console.info(`auth onResult result = ${result}`);
      if (result == userAuth.ResultCode.SUCCESS) {
        // Add the logic to be executed when the authentication is successful.
      }  else {
        // Add the logic to be executed when the authentication fails.
      }
    } catch (error) {
      console.error(`auth onResult failed, error = ${error}`);
    }
  }
});
```

### onAcquireInfo<sup>(deprecated)</sup>

onAcquireInfo ?: (module : number, acquire : number, extraInfo : any) => void

Called to acquire authentication tip information. This API is optional.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [callback](#callbackdeprecated) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name   | Type  | Mandatory| Description                          |
| --------- | ------ | ---- | ------------------------------ |
| module    | number | Yes  | ID of the module that sends the tip information.            |
| acquire   | number | Yes  | Authentication tip information.|
| extraInfo | any    | Yes  | Reserved field.                    |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let challenge = new Uint8Array([]);
auth.auth(challenge, userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1, {
  onResult: (result, extraInfo) => {
    try {
      console.info(`auth onResult result = ${result}`);
      if (result == userAuth.ResultCode.SUCCESS) {
        // Add the logic to be executed when the authentication is successful.
      }  else {
        // Add the logic to be executed when the authentication fails.
      }
    } catch (error) {
      console.error(`auth onResult failed, error = ${error}`);
    }
  },
  onAcquireInfo: (module, acquire, extraInfo : userAuth.AuthResult) => {
    try {
      console.info('auth onAcquireInfo successfully.');
    } catch (error) {
      console.error(`auth onAcquireInfo failed, error = ${error}`);
    }
  }
});
```

## AuthResult<sup>(deprecated)</sup>

Represents the authentication result object.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [AuthResultInfo](#authresultinfodeprecated) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name        | Type  | Read-Only| Optional| Description                |
| ------------ | ---------- | ---- | ---- | -------------------|
| token        | Uint8Array | No| Yes| Authentication token information.|
| remainTimes  | number     | No| Yes| Number of remaining authentication operations.|
| freezingTime | number     | No| Yes| Time for which the authentication operation is frozen. The unit is milliseconds.|

## ResultCode<sup>(deprecated)</sup>

Enumerates the authentication result codes.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 9. Use [UserAuthResultCode](#userauthresultcode9) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name                   | Value| Description                |
| ----------------------- | ------ | -------------------- |
| SUCCESS                 | 0      | The operation is successful.          |
| FAIL                    | 1      | The authentication failed.          |
| GENERAL_ERROR           | 2      | A general operation error occurred.      |
| CANCELED                | 3      | The authentication is canceled.          |
| TIMEOUT                 | 4      | The authentication timed out.          |
| TYPE_NOT_SUPPORT        | 5      | The authentication type is not supported.  |
| TRUST_LEVEL_NOT_SUPPORT | 6      | The authentication trust level is not supported.  |
| BUSY                    | 7      | Indicates the busy state.          |
| INVALID_PARAMETERS      | 8      | Invalid parameters are detected.          |
| LOCKED                  | 9      | The authentication executor is locked.      |
| NOT_ENROLLED            | 10     | The user has not enrolled the authentication information.|

## FaceTips<sup>(deprecated)</sup>

Enumerates the tip codes used during the facial authentication process.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 11.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name                         |   Value  |    Description                            |
| ----------------------------- | ------ | ------------------------------------ |
| FACE_AUTH_TIP_TOO_BRIGHT      | 1      | The obtained facial image is too bright due to high illumination.          |
| FACE_AUTH_TIP_TOO_DARK        | 2      | The obtained facial image is too dark due to low illumination.          |
| FACE_AUTH_TIP_TOO_CLOSE       | 3      | The face is too close to the device.                  |
| FACE_AUTH_TIP_TOO_FAR         | 4      | The face is too far away from the device.                  |
| FACE_AUTH_TIP_TOO_HIGH        | 5      | Only the upper part of the face is captured because the device is angled too high.        |
| FACE_AUTH_TIP_TOO_LOW         | 6      | Only the lower part of the face is captured because the device is angled too low.        |
| FACE_AUTH_TIP_TOO_RIGHT       | 7      | Only the right part of the face is captured because the device is deviated to the right.      |
| FACE_AUTH_TIP_TOO_LEFT        | 8      | Only the left part of the face is captured because the device is deviated to the left.      |
| FACE_AUTH_TIP_TOO_MUCH_MOTION | 9      | The face moves too fast during facial information collection.|
| FACE_AUTH_TIP_POOR_GAZE       | 10     | The face is not facing the camera.                    |
| FACE_AUTH_TIP_NOT_DETECTED    | 11     | No face is detected.                |


## FingerprintTips<sup>(deprecated)</sup>

Enumerates the tip codes used during the fingerprint authentication process.

> **NOTE**<br>
>
> This API is supported since API version 8 and deprecated since API version 11.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name                             |   Value  | Description                                              |
| --------------------------------- | ------ | -------------------------------------------------- |
| FINGERPRINT_AUTH_TIP_GOOD         | 0      | The obtained fingerprint image is in good condition.                              |
| FINGERPRINT_AUTH_TIP_DIRTY        | 1      | Large fingerprint image noise is detected due to suspicious or detected dirt on the sensor.|
| FINGERPRINT_AUTH_TIP_INSUFFICIENT | 2      | The noise of the fingerprint image is too large to be processed.    |
| FINGERPRINT_AUTH_TIP_PARTIAL      | 3      | Incomplete fingerprint image is detected.                            |
| FINGERPRINT_AUTH_TIP_TOO_FAST     | 4      | The fingerprint image is incomplete due to fast movement.                        |
| FINGERPRINT_AUTH_TIP_TOO_SLOW     | 5      | Failed to obtain the fingerprint image because the finger seldom moves.                      |


## UserAuthType<sup>8+</sup>

Enumerates the identity authentication types. This enumeration defines the authentication modes supported by the system, including the screen lock PIN and BioAuthn (facial recognition and fingerprint). When initiating authentication, an application needs to specify the authentication mode list, and the user can select any of the authentication modes to complete the authentication. Different authentication modes have different security strength and user experience characteristics. An application should select an appropriate authentication mode based on the service scenario.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name       | Value  | Description      |
| ----------- | ---- | ---------- |
| PIN<sup>10+</sup>         | 1    | PIN authentication. The user enters the screen lock password to complete authentication. Screen lock password authentication provides advanced security conditional access, with the authentication trust level reaching ATL4. It is applicable to all scenarios that require advanced security conditional access, such as payment and confirmation of important operations. The user needs to manually enter the password, which is less convenient than biometric authentication.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| FACE        | 2    | Facial authentication. The user completes authentication through facial recognition. The system verifies the matching degree between the user's facial features and the registered face. Facial authentication supports different levels of liveness detection. For details about the classification principles, please refer to [Trustworthiness Classification Principles of Biometric Authentication](../../security/UserAuthenticationKit/user-authentication-overview.md). The advantage is that the experience is convenient. The disadvantage is that the device and lighting conditions have certain requirements.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| FINGERPRINT | 4    | Fingerprint authentication. The user completes authentication through the fingerprint sensor. The system verifies the matching degree between the user's fingerprint features and the registered fingerprint. Fingerprint authentication supports multiple levels of trustworthiness. For details about the classification principles, please refer to [Trustworthiness Classification Principles of Biometric Authentication](../../security/UserAuthenticationKit/user-authentication-overview.md). It is applicable to scenarios with medium security requirements. The advantage is that the operation is simple and quick. The disadvantage is that the device must be equipped with a fingerprint sensor, and the identification effect may be affected by wet hands or abrasion.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| COMPANION_DEVICE  | 64    | Accompanying device authentication. The user completes authentication by wearing an accompanying device. Accompanying device authentication supports multiple levels of trustworthiness. For details about the classification principles, please refer to [Trustworthiness Classification Principles of Biometric Authentication](../../security/UserAuthenticationKit/user-authentication-overview.md).<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|
## AuthTrustLevel<sup>8+</sup>

Enumerates the trust levels of the authentication result. This enumeration defines four levels of trustworthiness, which are used to describe the security strength of authentication results. A higher level of trustworthiness indicates a stronger liveness detection capability and more accurate user identity identification of the authentication scheme, and is applicable to service scenarios with advanced security conditional access requirements. An application should select a proper level of trustworthiness based on the security requirements of the service scenario.

For details about typical scenarios and examples, see [Trust Levels of Biometric Authentication](../../security/UserAuthenticationKit/user-authentication-overview.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name| Value   | Description                                                        |
| ---- | ----- | ------------------------------------------------------------ |
| ATL1 | 10000 | Trust level 1 of the authentication result, indicating that the authentication solution can identify individuals and has the basic liveness detection capability (such as simple action detection). The security strength is low, and the authentication result may be risky. It is applicable to low-security scenarios, such as service risk control, general personal data query, and access to non-sensitive information. It is recommended that this level be used together with other security measures.|
| ATL2 | 20000 | Trust level 2 of the authentication result, indicating that the authentication solution can accurately identify individuals and has the criterion-based liveness detection capability (such as detecting blinking and nodding). The security strength is medium, and the solution can effectively defend against simple forgery attacks. It is applicable to medium-security scenarios, such as maintaining the screen-unlocked state, app login, and confirmation of general sensitive operations.|
| ATL3 | 30000 | Trust level 3 of the authentication result, indicating that the authentication solution can accurately identify individuals and has a strong liveness detection capability (such as 3D face recognition and multi-frame analysis). The security strength is high, and the solution can effectively defend against common forgery attacks such as photos and videos. It is applicable to advanced security scenarios, such as device unlocking, confirmation of important and sensitive operations, and enterprise-level app login. 3D face recognition devices support this level.|
| ATL4 | 40000 | Trust level 4 of the authentication result, indicating that the authentication solution can accurately identify individuals with high precision and has a strong liveness detection capability (such as in-depth analysis and multi-dimensional verification). The security strength is the highest, and the solution can effectively defend against various advanced forgery attacks. It is applicable to advanced security scenarios, such as small-amount payment, financial transaction, and access to highly sensitive data. Only a few advanced security conditional access authentication solutions support this level.|

## SecureLevel<sup>(deprecated)</sup>

type SecureLevel = string

Enumerates the authentication security levels.

> **NOTE**<br>
>
> This API is supported since API version 6 and deprecated since API version 8. Use [AuthTrustLevel](#authtrustlevel8) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| string | String type. The authentication security level can be **'S1'** \| **'S2'**\|**'S3'**\|**'S4'**.<br>\- **S1**: authentication trust level 1. The authentication of this level can identify individual users and provides limited liveness detection capabilities. It is usually used in service risk control and query of general personal data.<br>\- **S2**: authentication trust level 2. The authentication of this level can accurately identify individual users and provides regular liveness detection capabilities. It is usually used in scenarios such as application logins and keeping the unlocking state of a device.<br>\- **S3**: authentication trust level 3. The authentication of this level can accurately identify individual users and provides strong liveness detection capabilities. It is usually used in scenarios such as unlocking a device.<br>\- **S4**: authentication trust level 4. The authentication of this level can accurately identify individual users and provides powerful liveness detection capabilities. It is usually used in scenarios such as small-amount payment.|

## AuthType<sup>(deprecated)</sup>

type AuthType = string

Enumerates the authentication types.

> **NOTE**<br>
>
> This API is supported since API version 6 and deprecated since API version 8. Use [UserAuthType](#userauthtype8) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| string  | Authentication mode, which can be any of the following: **'ALL'**\|**'FACE_ONLY'**.<br>\- **ALL**: reserved and not supported by the current version.<br>\- **FACE_ONLY**: facial authentication.|

## userAuth.getAuthenticator<sup>(deprecated)</sup>

getAuthenticator(): Authenticator

Obtains an **Authenticator** instance for user authentication.

> **NOTE**<br>
>
> This API is supported since API version 6 and deprecated since API version 8. Use [getAuthInstance](#userauthgetauthinstancedeprecated) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Return value**

| Type                                     | Description        |
| ----------------------------------------- | ------------ |
| [Authenticator](#authenticatordeprecated) | **Authenticator** instance obtained.|

**Example**
  ```ts
  import { userAuth } from '@kit.UserAuthenticationKit';
  
  let authenticator = userAuth.getAuthenticator();
  ```

## Authenticator<sup>(deprecated)</sup>

Provides APIs for managing the **Authenticator** object.

> **NOTE**<br>
>
> This API is supported since API version 6 and deprecated since API version 8. Use [AuthInstance](#authinstancedeprecated) instead.

### execute<sup>(deprecated)</sup>

execute(type: AuthType, level: SecureLevel, callback: AsyncCallback&lt;number&gt;): void

Starts user authentication. This API uses an asynchronous callback to return the result.

> **NOTE**<br>
>
> This API is supported since API version 6 and deprecated since API version 8. Use [start](#startdeprecated) instead.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name  | Type                       | Mandatory| Description                                                                                                                   |
| -------- | --------------------------- | ---- |-----------------------------------------------------------------------------------------------------------------------|
| type     | AuthType                      | Yes  | Authentication type. Currently, only **FACE_ONLY** is supported.<br>**ALL** is reserved and not supported by the current version.                                                                |
| level    | SecureLevel  | Yes  | Security level of the authentication. It can be **S1** (lowest), **S2**, **S3**, or **S4** (highest).<br>Devices capable of 3D facial recognition support S3 and lower-level authentication.<br>Devices capable of 2D facial recognition support S2 and lower-level authentication.|
| callback | AsyncCallback&lt;number&gt; | Yes| Callback used to return the result. **number** indicates the [AuthenticationResult](#authenticationresultdeprecated).|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

let authenticator = userAuth.getAuthenticator();
authenticator.execute('FACE_ONLY', 'S2', (error, code)=>{
  if (code === userAuth.ResultCode.SUCCESS) {
    console.info('auth successfully.');
    return;
  }
  console.error(`auth failed, code = ${code}`);
});
```


### execute<sup>(deprecated)</sup>

execute(type : AuthType, level : SecureLevel): Promise&lt;number&gt;

Starts user authentication. This API uses a promise to return the result.

> **NOTE**<br>
>
> This API is supported since API version 6 and deprecated since API version 8. Use [start](#startdeprecated) instead.

**Required permissions**: ohos.permission.ACCESS_BIOMETRIC

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name| Type  | Mandatory| Description                                                                                                                   |
| ------ | ------ | ---- |-----------------------------------------------------------------------------------------------------------------------|
| type   | AuthType | Yes  | Authentication type. Currently, only **FACE_ONLY** is supported.<br>**ALL** is reserved and not supported by the current version.                                                                |
| level  | SecureLevel | Yes  | Security level of the authentication. It can be **S1** (lowest), **S2**, **S3**, or **S4** (highest).<br>Devices capable of 3D facial recognition support S3 and lower-level authentication.<br>Devices capable of 2D facial recognition support S2 and lower-level authentication.|

**Return value**

| Type                 | Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the authentication result, which is a number. For details, see [AuthenticationResult](#authenticationresultdeprecated).|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  let authenticator = userAuth.getAuthenticator();
  authenticator.execute('FACE_ONLY', 'S2').then((code)=>{
    console.info('auth successfully.');
  })
} catch (error) {
  console.error(`auth failed, code = ${error}`);
}
```

## AuthenticationResult<sup>(deprecated)</sup>

Enumerates the authentication results.

> **NOTE**<br>
>
> This API is supported since API version 6 and deprecated since API version 8. Use [UserAuthResultCode](#userauthresultcode9) instead.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name              |   Value  | Description                      |
| ------------------ | ------ | -------------------------- |
| NO_SUPPORT         | -1     | The device does not support the current authentication mode.|
| SUCCESS            | 0      | The authentication is successful.                |
| COMPARE_FAILURE    | 1      | The feature comparison failed.                |
| CANCELED           | 2      | The authentication was canceled by the user.            |
| TIMEOUT            | 3      | The authentication has timed out.                |
| CAMERA_FAIL        | 4      | The camera failed to start.            |
| BUSY               | 5      | The authentication service is not available. Try again later.  |
| INVALID_PARAMETERS | 6      | The authentication parameters are invalid.            |
| LOCKED             | 7      | The user account is locked because the number of authentication failures has reached the threshold.|
| NOT_ENROLLED       | 8      | No authentication credential is registered.          |
| GENERAL_ERROR      | 100    | Other errors.                |
