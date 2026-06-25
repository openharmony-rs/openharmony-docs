# @ohos.userIAM.userAuth (User Authentication) (System API)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

## Overview

The **userAuth** module is the core module for user authentication in OpenHarmony. It provides authentication capabilities in scenarios such as device unlocking, payment verification, and application login.

This topic describes only the advanced capabilities provided by this module for system application and authentication widget developers. These APIs provide system-level features such as authentication widget management, custom notification sending, authentication result reuse query, and privacy password authentication.

You can use them in the following scenarios:

- The system application needs to manage the lifecycle of custom authentication widgets.
- The authentication widget needs to perform bidirectional communication with the authentication framework.
- System notifications related to the authentication widget need to be sent.
- Reusable authentication results need to be queried to implement seamless authentication.
- The privacy password needs to be used for authentication.
- A specific user or credential needs to be specified for authentication.

> **NOTE**<br>
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.userIAM.userAuth (User Authentication)](js-apis-useriam-userauth.md).

## Modules to Import

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
```

## AuthParam<sup>10+</sup>

Represents the user authentication parameters. This API is used to configure user authentication parameters, including the challenge value, authentication type list, and authentication trust level.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name          | Type                              | Read-Only| Optional| Description                                                        |
| -------------- | ---------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| userId<sup>18+</sup> | number | No  | Yes  | Target user ID to be authenticated. The value is a non-negative integer, which specifies the user to be authenticated. The default value is the ID of the current user.<br>**System API**: This is a system API.|
| credentialIdList<sup>23+</sup> | Uint8Array[] | No| Yes| List of credential IDs. If the credential ID list is not empty, the specified credential IDs are authenticated, instead of all credentials of the user. This is applicable to scenarios where precise control over authentication credentials is required.<br>**System API**: This is a system API.<br>**Model restriction:** This API can be used only in the stage model.|

## WindowModeType<sup>10+</sup>

Enumerates the display types of the user authentication screen. This enum defines the display modes that can be used on the authentication screen and is used to control the window style of the system authentication widget.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

| Name      | Value  | Description      |
| ---------- | ---- | ---------- |
| DIALOG_BOX | 1    | Dialog box type. The authentication screen is displayed in dialog box mode, which is applicable to most authentication scenarios and provides good user experience.|
| FULLSCREEN | 2    | Full screen. The authentication screen is displayed in full screen mode, which is applicable to scenarios that require immersive authentication experience or scenarios where a large amount of authentication information needs to be displayed.|

## WidgetParam<sup>10+</sup>

Represents the information presented on the user authentication page. This API is used to configure the display style and interaction mode of the authentication screen, including the title, navigation button text, and window mode.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name                | Type                               | Read-Only| Optional| Description                                                        |
| -------------------- | ----------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| windowMode           | [WindowModeType](#windowmodetype10) | No  | Yes  | Enumerates the window types of the authentication widget. This parameter is used to control the window style of the system authentication widget. You can select the dialog box mode (**DIALOG_BOX**) or full-screen mode (**FULLSCREEN**). The default value is **WindowModeType.DIALOG_BOX**.<br>**System API**: This is a system API.|

## NoticeType<sup>10+</sup>

Enumerates the notification types of user authentication. This enum defines the notification types supported by the system, which are used to identify the source of a notification.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

| Name         | Value  | Description                |
| ------------- | ---- | -------------------- |
| WIDGET_NOTICE | 1    | The notification is sent by the system authentication widget to notify the user of events related to the authentication framework.|

## userAuth.sendNotice<sup>10+</sup>

sendNotice(noticeType: NoticeType, eventData: string): void

Sends a notification from the user authentication widget. When the unified authentication widget is used for user authentication, this API is used to receive notifications from the unified authentication widget and send the notifications to the user authentication framework.

**Required permissions**: ohos.permission.SUPPORT_USER_AUTH

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name    | Type                       | Mandatory| Description      |
| ---------- | --------------------------- | ---- | ---------- |
| noticeType | [NoticeType](#noticetype10) | Yes  | Notification type. It identifies the source of a notification. Currently, **WIDGET_NOTICE (1)** is supported, indicating that the notification is from the authentication widget.|
| eventData  | string                | Yes  | Event data. It is a string in JSON format, containing the notification details, such as the authentication type and ready event. The data length ranges from 0 to 65536 bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission denied. Called by non-system application. |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed.    |
| 12500002 | General operation error.                |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface  EventData {
  widgetContextId: number;
  event: string;
  version: string;
  payload: PayLoad;
}
interface PayLoad {
  type: string[];
}
try {
  const eventData : EventData = {
    widgetContextId: 123456,
    event: 'EVENT_AUTH_TYPE_READY',
    version: '1',
    payload: {
      type: ['pin']
    } as PayLoad,
  };
  const jsonEventData = JSON.stringify(eventData);
  let noticeType = userAuth.NoticeType.WIDGET_NOTICE;
  userAuth.sendNotice(noticeType, jsonEventData);
  console.info('sendNotice successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`sendNotice failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## UserAuthWidgetMgr<sup>10+</sup>

Defines the authentication widget manager. It is used to register the custom authentication widget with the **UserAuthWidgetMgr** for unified management and scheduling. Through this API, the custom authentication widget can receive commands from the user authentication framework and perform corresponding operations.

### on<sup>10+</sup>

on(type: 'command', callback: IAuthWidgetCallback): void

Subscribes to command events from the user authentication framework. The authentication widget uses this API to subscribe to commands from the user authentication framework so that it can perform corresponding authentication operations based on the commands.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                        |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'command'                                     | Yes  | Event type to subscribe to. The value **'command'** indicates that the event is used by the user authentication framework to send commands to the user authentication widget.|
| callback | [IAuthWidgetCallback](#iauthwidgetcallback10) | Yes  | Callback function. It is used to receive commands from the user authentication framework. The authentication widget needs to parse the commands and perform corresponding operations in the callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                |
| -------- | ------------------------ |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed. |
| 12500002 | General operation error. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.on('command', {
    sendCommand(cmdData) {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

### off<sup>10+</sup>

off(type: 'command', callback?: IAuthWidgetCallback): void

Unsubscribes from command events from the user authentication framework. The authentication widget uses this API to unsubscribe from commands from the user authentication framework.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                        |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'command'                                     | Yes  | Event type to subscribe to. The value **'command'** indicates that the event that the user authentication framework sends commands to the identity authentication widget is unsubscribed.|
| callback | [IAuthWidgetCallback](#iauthwidgetcallback10) | No  | Callback function. It specifies the callback function to be unregistered. If this parameter is not passed, all registered callback functions are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                |
| -------- | ------------------------ |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed. |
| 12500002 | General operation error. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.off('command', {
    sendCommand(cmdData) {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('cancel subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## userAuth.getUserAuthWidgetMgr<sup>10+</sup>

getUserAuthWidgetMgr(version: number): UserAuthWidgetMgr

Obtains the authentication widget manager object. It is used to obtain the **UserAuthWidgetMgr** instance, which can be used to register custom authentication widgets with the system for unified management.

> **NOTE**<br>
>
> Each **UserAuthWidgetMgr** instance can manage one authentication widget. To manage multiple widgets, you need to obtain multiple instances.

**Required permissions**: ohos.permission.SUPPORT_USER_AUTH

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name | Type  | Mandatory| Description                |
| ------- | ------ | ---- | -------------------- |
| version | number | Yes  | Version number of the authentication widget. Currently, version 1 is supported. The widget version determines the communication protocol and supported features between the widget and the framework.|

**Return value**

| Type                                     | Description        |
| ----------------------------------------- | ------------ |
| [UserAuthWidgetMgr](#userauthwidgetmgr10) | Authentication widget manager object. It can be used to subscribe to and unsubscribe from commands from the user authentication framework.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission denied. Called by non-system application. |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. |
| 12500002 | General operation error.                |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## IAuthWidgetCallback<sup>10+</sup>

Defines the callback of the authentication widget. The authentication widget uses this callback to obtain commands sent by the user authentication framework and perform corresponding authentication operations based on the command content.

### sendCommand<sup>10+</sup>

sendCommand(cmdData: string): void

Triggered to receive commands from the user authentication framework. The user authentication framework uses this callback to send commands to the identity authentication widget. The widget needs to parse the command content and perform corresponding operations.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name | Type  | Mandatory| Description                              |
| ------- | ------ | ---- | ---------------------------------- |
| cmdData | string | Yes  | Command data. It is a JSON string, containing the command content sent by the user authentication framework to the authentication widget, such as commands for switching the authentication type and returning the authentication result. The widget needs to parse the data and perform the corresponding operations.|

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.on('command', {
    sendCommand(cmdData) {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## UserAuthType<sup>8+</sup>

Enumerates the types of credentials for identity authentication. This enum defines the authentication types supported by the system, including biometric authentication (face and fingerprint) and password authentication (PIN).

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name       | Value  | Description      |
| ----------- | ---- | ---------- |
| PRIVATE_PIN<sup>14+</sup>  | 16   | Privacy PIN. It is a special PIN authentication type, which is generally used for secondary access control after the screen is unlocked. For example, a user can use the privacy password protection application lock to prevent family members who know the lock screen password from accessing some of their applications.<br>**System API**: This is a system API.|

**Example**

Initiate privacy PIN authentication with the authentication trust level greater than or equal to ATL3.

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  const randData: Uint8Array = rand?.generateRandomSync(len)?.data;
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PRIVATE_PIN],
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

## userAuth.queryReusableAuthResult<sup>20+</sup>

queryReusableAuthResult(authParam: AuthParam): Uint8Array

Queries whether there is any reusable identity authentication result. This API is used to query whether there is an authentication result that meets the reuse conditions before authentication is initiated. If such a result exists, the **AuthToken** that can be reused is returned directly, and the user does not need to perform authentication again.

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name | Type  | Mandatory| Description                |
| ------- | ------ | ---- | -------------------- |
| authParam | [AuthParam](js-apis-useriam-userauth.md#authparam10) | Yes| Represents the user authentication parameters. The parameters include the challenge value, authentication type list (**authType**), authentication trust level (**authTrustLevel**), and authentication result reuse configuration (**reuseUnlockResult**). Based on these parameters, the system determines whether there are reusable authentication results that meet the requirements.|

**Return value**

| Type       | Description                                |
| ---------- | ------------------------------------ |
| Uint8Array | Reusable authentication token (**AuthToken**). If there are reusable authentication results that meet the requirements, the **AuthToken** data is returned. The maximum length is 1024 bytes. If there are no such results, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission denied. Called by non-system application. |
| 12500002 | General operation error.                |
| 12500008 | The parameter is out of range.          |
| 12500017 | Failed to reuse authentication result.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  const randData: Uint8Array = rand?.generateRandomSync(len)?.data;
  const reuseUnlockResult: userAuth.ReuseUnlockResult = {
    reuseMode: userAuth.ReuseMode.AUTH_TYPE_RELEVANT,
    reuseDuration: userAuth.MAX_ALLOWABLE_REUSE_DURATION,
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
    reuseUnlockResult: reuseUnlockResult,
  };
  let authToken = userAuth.queryReusableAuthResult(authParam);
  console.info('query reuse auth result successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`query reuse auth result failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## UserAuthResultCode<sup>9+</sup>

Enumerates the authentication result codes. They include all success codes and error codes for user authentication operations.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

| Name                   |   Value  | Description                |
| ----------------------- | ------ | -------------------- |
| AUTH_TOKEN_CHECK_FAILED<sup>18+</sup> | 12500015      | Failed to verify the **AuthToken**. It is an error code of the system API **verifyAuthToken**, indicating that the integrity verification of the verified **AuthToken** fails and the token may be tampered or damaged.|
| AUTH_TOKEN_EXPIRED<sup>18+</sup>      | 12500016      | The **AuthToken** has expired. It is an error code of the system API **verifyAuthToken**, indicating that the interval between the **AuthToken** issuance time and the **AuthToken** verification time exceeds the maximum validity period (**allowableDuration**).|
| REUSE_AUTH_RESULT_FAILED<sup>20+</sup>| 12500017      | Failed to reuse the authentication result. It is an error code of the system API **queryReusableAuthResult**, indicating that the reusable authentication result fails to be queried. The possible causes are as follows: No authentication result that meets the reuse conditions exists, the authentication result has expired, or the credential has been changed.|
