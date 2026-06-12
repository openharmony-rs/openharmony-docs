# @ohos.userIAM.userAccessCtrl (User Access Control) (System API)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

## Overview

The **userAccessCtrl** module is a core component of the OpenHarmony user identity and access management (UserIAM) system. It is dedicated to the verification and management of authentication tokens. This module provides APIs for verifying authentication tokens (**AuthToken**). It can parse and verify user authentication results and return detailed authentication information.

This module applies to the following scenarios:
- System-level applications need to verify the validity of user authentication tokens.
- Detailed information about the authentication token needs to be obtained, such as the authentication type, trust level, and user ID.
- Access control decisions need to be made based on the authentication result.


> **NOTE**
>
> - The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.

## Key Classes and APIs

### Key Enums

- [AuthTokenType](#authtokentype): Enumerates the authentication token types, including local authentication, reuse authentication, and collaborative authentication.

### Key Functions

- [verifyAuthToken](#useraccessctrlverifyauthtoken): Verifies the authentication token and returns the parsed authentication information. This is the core verification function of the **UserAccessCtrl** module.

### Key APIs

- [AuthToken](#authtoken): Defines the data structure of the authentication token returned after successful verification, including key information such as the authentication challenge, trust level, authentication type, and user ID.

![Class relationship diagram](figures/uml_useraccessctrl.png)

## APIs Called in Pairs

The typical process of using the **userAccessCtrl** module is as follows:

```ts
// The following is the pseudocode for describing the calling logic. It provides only the step description and does not provide detailed executable code.
// 1. Obtain the authentication token to be verified (usually obtained from other authentication processes).
let authToken = getAuthTokenFromPreviousAuthFlow();

// 2. Set the validity period (in milliseconds) of the token.
let allowableDuration = 3600000; // 1 hour.

// 3. Call verifyAuthToken to verify the token.
let parsedToken = await userAccessCtrl.verifyAuthToken(authToken, allowableDuration);

// 4. Perform subsequent processing based on the returned AuthToken information.
// - Check authTrustLevel to determine the trust level.
// - Check authType to determine the authentication mode.
// - Check tokenType to determine the token type.
// - Use userId to perform user-related operations.
```

## Modules to Import

```ts
import { userAccessCtrl } from '@kit.UserAuthenticationKit';
```

## AuthTokenType

Enumerates the authentication token types. They are used to identify the source of the token.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

| Name                     | Value  | Description      |
| ------------------------ | ---- | ---------- |
| TOKEN_TYPE_LOCAL_AUTH    | 0    | Local authentication token. It is an authentication token issued based on the local authentication result, indicating that the user has been authenticated on the local device.|
| TOKEN_TYPE_LOCAL_RESIGN  | 1    | Local resigning token. It is an authentication token signed based on the reused authentication result, indicating that the current authentication result is reused from a previous authentication result.|
| TOKEN_TYPE_COAUTH        | 2    | Collaborative authentication token. It is an authentication token issued based on multiple device collaboration authentication results, indicating that the user has completed authentication through multi-device collaboration.|

## AuthToken

Authentication token data. It indicates the parsed **AuthToken** data returned after the verification is successful, including detailed authentication information such as the challenge value, authentication trust level, authentication type, and user ID.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

| Name          | Type                              | Read Only| Optional| Description                                      |
| -------------- | ---------------------------------- | ----- | ----- |------------------------------------------------------------ |
| challenge | Uint8Array | No| No| Random challenge value for the authentication. It is used to prevent replay attacks. The challenge value passed during authentication is included in the **AuthToken**. The service can verify this field to confirm the validity of the authentication result.|
| authTrustLevel | [userAuth.AuthTrustLevel](js-apis-useriam-userauth.md#authtrustlevel8) | No| No| Authentication trust level. It indicates the security strength level of the current authentication. The value can be **ATL1(10000)**, **ATL2(20000)**, **ATL3(30000)**, or **ATL4(40000)**. A higher level indicates a stronger liveness detection capability and more accurate identity recognition.|
| authType | [userAuth.UserAuthType](js-apis-useriam-userauth.md#userauthtype8) | No| No | Credential type for the identity authentication. It indicates the authentication mode used for the current authentication, such as **PIN(1)**, **FACE(2)**, and **FINGERPRINT(4)**.|
| tokenType | [AuthTokenType](#authtokentype) | No| No| Enumerates the authentication token types. It identifies the source of the token, such as local authentication, reuse authentication, or collaborative authentication.|
| userId | number | No| No | User ID. It indicates the ID of the user who has completed authentication. The value is a positive integer greater than or equal to 0.|
| timeInterval | bigint | No | No | Time elapsed since the **AuthToken** was issued, in milliseconds.|
| secureUid | bigint    | No | Yes | Secure user ID. It indicates the security ID of a user, which is used internally by the system and returned only in specific authentication scenarios.|
| enrolledId | bigint   | No | Yes | Credential enrollment ID. It indicates the original value of **credentialDigest** in **enrolledState**, which reflects the credential change.|
| credentialId | bigint | No | Yes | Credential ID. It indicates the ID of the credential that is successfully matched in the current authentication. It is used to associate with the specific authentication credential.|


## userAccessCtrl.verifyAuthToken

verifyAuthToken(authToken: Uint8Array, allowableDuration: number): Promise\<AuthToken>

Verifies an authentication token. This API is used to verify the validity of an **AuthToken**, including the integrity and validity check. After the verification is successful, the detailed information about the parsed **AuthToken** is returned. This API uses a promise to return the result.

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                       | Mandatory| Description      |
| ---------- | --------------------------- | ---- | ---------- |
| authToken | Uint8Array | Yes  | Authentication token to be verified. The value contains a maximum of 1024 bytes and is returned after the user is authenticated. The token contains the credentials information for user authentication, which is used for subsequent security operation verification.|
| allowableDuration  | number  | Yes  | Authentication validity period. It indicates the maximum time interval for using the token from the time when the token is issued. The unit is millisecond. The value must be greater than 0 and less than or equal to 86400000 (24 hours). It is used to verify the validity of a token to prevent expired tokens from being used.|

**Return value**

| Type                                     | Description        |
| ----------------------------------------- | ------------ |
| Promise\<[AuthToken](#authtoken)> | Promise object used to return the result. If the verification is successful, the parsed **AuthToken** data is returned, including the challenge value, authentication trust level, authentication type, and user ID. If the verification fails, the corresponding error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 201      | Permission denied.        |
| 202      | Permission denied. Called by non-system application. |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed.    |
| 12500002 | General operation error.                |
| 12500015 | AuthToken integrity check failed.     |
| 12500016 | AuthToken has expired.                |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAccessCtrl } from '@kit.UserAuthenticationKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const allowableDuration: number = 5000;
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
  // The authentication result is returned by onResult() only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.on('result', {
    onResult (result) {
        if (!result.token) {
            console.error('userAuthInstance callback result.token is null');
            return;
        }
        try {
          // Initiate a request for verifying the AuthToken.
          userAccessCtrl.verifyAuthToken(result.token, allowableDuration)
              .then((retAuthToken: userAccessCtrl.AuthToken) => {
                  Object.keys(retAuthToken).forEach((key) => {
                      // Process the service logic.
                      console.info(`retAuthToken key:${key}`);
                  })
              }).catch ((error: BusinessError) => {
                  console.error(`verify authToken failed. Code is ${error?.code}, message is ${error?.message}`);
              })
        } catch (error) {
          const err: BusinessError = error as BusinessError;
          console.error(`verify authToken failed. Code is ${err?.code}, message is ${err?.message}`);
        }
    }
  });
  console.info('auth on successfully.');
  // Start authentication.
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```
