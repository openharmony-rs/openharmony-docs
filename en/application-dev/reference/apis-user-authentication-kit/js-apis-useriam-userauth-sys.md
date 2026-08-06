# @ohos.userIAM.userAuth (User Authentication) (System API)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=be48531bb599ab262690e4bcab7fffa1f7126656 translatedAt=2026-07-27T00:48:26.780Z pushedAt=2026-07-27T08:45:08.376Z -->

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

Represents the user authentication parameters. This API is used to configure user authentication parameters. This topic defines only the parameters specific to system APIs. For the complete parameter definitions, see [AuthParam](js-apis-useriam-userauth.md#authparam10).

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name          | Type                              | Read-Only| Optional| Description                                                        |
| -------------- | ---------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| userId<sup>18+</sup> | number | No   | Yes   | ID of the target user to be authenticated. This parameter is passed when a specific user, rather than the currently logged-in user, needs to be authenticated. If not passed, the ID of the currently logged-in user is used by default. The value is a non-negative integer.<br>**System API:** This is a system API.|
| credentialIdList<sup>23+</sup> | Uint8Array[] | No | Yes | List of IDs for credentials to be authenticated. This parameter is passed when only specific credentials, rather than all credentials of the user, need to be authenticated. If not passed or an empty array is passed, all credentials of the user are authenticated by default.<br>**System API:** This is a system API.<br>**Model restriction:** This API can be used only in the stage model.|

## WindowModeType<sup>10+</sup>

Enumerates the display types of the user authentication screen. This enum defines the display modes that can be used on the authentication screen and is used to control the window style of the system authentication widget.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

| Name      | Value  | Description      |
| ---------- | ---- | ---------- |
| DIALOG_BOX | 1    | Dialog box type. The authentication screen is displayed in dialog box mode, which is applicable to most authentication scenarios and provides good user experience.|
| FULLSCREEN | 2    | Full screen. The authentication screen is displayed in full screen mode, which is applicable to scenarios that require immersive authentication experience or scenarios where a large amount of authentication information needs to be displayed.|

## WidgetParam<sup>10+</sup>

Represents the parameters for configuring the user authentication screen. This API is used to configure the display style and interaction mode of the authentication screen. This topic defines only the parameters specific to system APIs. For the complete parameter definitions, see [WidgetParam](js-apis-useriam-userauth.md#widgetparam10).

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name                | Type                               | Read-Only| Optional| Description                                                        |
| -------------------- | ----------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| windowMode           | [WindowModeType](#windowmodetype10) | No   | Yes   | Window type of the user authentication screen. **DIALOG_BOX** is suitable for most authentication scenarios (with better user experience), and **FULLSCREEN** is suitable for scenarios that require an immersive authentication experience or involve more authentication information. If not specified, the default value is **WindowModeType.DIALOG_BOX**.<br>**System API:** This is a system API. |
| appWindow          | [window.Window](../apis-arkui/arkts-apis-window-Window.md) | No   | Yes   | Application window object. It is used to display the identity authentication dialog box as an application modal dialog. It is suitable for scenarios where the authentication dialog box needs to be controlled through a window object. If this parameter is provided, **uiContext** will be ignored.<br>**Since:** 26.0.0<br>**System API:** This is a system API.<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API:** This API can be used in atomic services since API version 26.0.0. |

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
| eventData  | string                | Yes   | Event data, which is a JSON string that contains the specific content of the notification, such as the authentication type ready event. The data length ranges from 0 to 65536 bytes. The JSON object should contain fields such as **widgetContextId** (number type, widget context ID), **event** (string type, event type), **version** (string type, version number), and **payload** (object type, event payload object). |

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
  payload: Payload;
}
interface Payload {
  type: string[];
}
try {
  const eventData : EventData = {
    widgetContextId: 123456,
    event: 'EVENT_AUTH_TYPE_READY',
    version: '1',
    payload: {
      type: ['pin']
    } as Payload,
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

Defines the identity authentication widget manager. It is used to register custom identity authentication widgets with the **UserAuthWidgetMgr** for unified management and scheduling. Custom authentication widgets can receive commands from the user authentication framework and execute corresponding operations.

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
    sendCommand: (cmdData) => {
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
| callback | [IAuthWidgetCallback](#iauthwidgetcallback10) | No | Callback to unregister, which must be the same as the callback passed in the **on** method. If this parameter is not passed, all registered callbacks are unregistered. Before using the **off** API, ensure that the corresponding callback has been registered through the [on](#on10) method. |

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
    sendCommand: (cmdData) => {
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
| version | number | Yes | Version number of the authentication widget. Currently, only version 1 is supported. The widget version determines the communication protocol and supported features between the widget and the framework. |

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
| cmdData | string | Yes | Command data, which is a JSON string containing the command content sent by the user authentication framework to the authentication widget. The JSON structure includes corresponding fields based on different command types. Common fields include: **commandType** (string, command type), **authType** (array, list of authentication types), **result** (number, authentication result code), etc. The widget must parse this data and perform corresponding operations based on the command type. |

**Example**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.on('command', {
    sendCommand: (cmdData) => {
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

Enumerates the credential types for identity authentication. This topic defines only the authentication types specific to system APIs. For the complete type definitions, see [UserAuthType](js-apis-useriam-userauth.md#userauthtype8).

**System capability**: SystemCapability.UserIAM.UserAuth.Core

| Name       | Value  | Description      |
| ----------- | ---- | ---------- |
| PRIVATE_PIN<sup>14+</sup>  | 16   | Privacy PIN. It is a special PIN authentication type, which is generally used for secondary access control after the screen is unlocked (that is, the user must be authenticated again before accessing a specific application or content after the device is unlocked). For example, a user can use a privacy password to protect the application lock (a feature that performs secondary authentication on application startup to prevent others from opening the user's applications) to prevent family members who know the lock screen password from accessing some of their applications.<br>**System API:** This is a system API. |

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
    onResult: (result) => {
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

Enumerates the result codes. This topic defines only the error codes specific to system APIs. For the complete error code definitions, see [UserAuthResultCode](js-apis-useriam-userauth.md#userauthresultcode9).

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

| Name                   |   Value  | Description                |
| ----------------------- | ------ | -------------------- |
| AUTH_TOKEN_CHECK_FAILED<sup>18+</sup> | 12500015      | Failed to verify the **AuthToken**. It is an error code of the system API **verifyAuthToken**, indicating that the integrity verification of the verified **AuthToken** fails and the token may be tampered or damaged.|
| AUTH_TOKEN_EXPIRED<sup>18+</sup>      | 12500016      | The **AuthToken** has expired. It is an error code of the system API **verifyAuthToken**, indicating that the interval between the **AuthToken** issuance time and the **AuthToken** verification time exceeds the maximum validity period (**allowableDuration**).|
| REUSE_AUTH_RESULT_FAILED<sup>20+</sup>| 12500017      | Failed to reuse the authentication result. It is an error code of the system API **queryReusableAuthResult**, indicating that the reusable authentication result fails to be queried. The possible causes are as follows: No authentication result that meets the reuse conditions exists, the authentication result has expired, or the credential has been changed.|

## WidgetParamCallback

type WidgetParamCallback = (challenge: Uint8Array) => WidgetParam

Defines the callback for obtaining remote authentication widget parameters. This type is used in remote authentication scenarios. When the configuration parameters of the remote authentication widget need to be obtained, the system invokes this callback.

**Since:** 26.0.0

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| challenge | Uint8Array | Yes | Random challenge value, which can be used to prevent replay attacks. The maximum length is 32 bytes. Uint8Array([]) can be passed. It is recommended that a random number generated by the [crypto framework](../apis-crypto-architecture-kit/js-apis-cryptoFramework.md) be used as the challenge value to enhance security. |

**Return value**

| Type | Description |
| -------- | -------- |
| [WidgetParam](js-apis-useriam-userauth.md#widgetparam10) | Configuration parameters of the user authentication widget, including the title and navigation button text. |

## ResultCallback

type ResultCallback = (challenge: Uint8Array, result: UserAuthResult) => void

Defines the callback for returning remote authentication results. This type is used in remote authentication scenarios. After the remote authentication is complete, the system invokes this callback to return the authentication result.

**Since:** 26.0.0

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| challenge | Uint8Array | Yes | Challenge value. It is a one-time random number used to prevent replay attacks, which is consistent with the challenge value passed during authentication initiation. |
| result | [UserAuthResult](js-apis-useriam-userauth.md#userauthresult10) | Yes | User authentication result, including the authentication result code and authentication token. |

## IRemoteAuthCallback

Defines the remote authentication callback API. This API is used in remote authentication scenarios and provides the callback capabilities for obtaining remote authentication widget parameters and returning authentication results.

**Since:** 26.0.0

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| onGetRemoteAuthWidgetParam | [WidgetParamCallback](#widgetparamcallback) | No | No | Callback for obtaining remote authentication widget parameters. When a remote device initiates an authentication request, the system invokes this callback to obtain the authentication widget configuration parameters. |
| onRemoteAuthResult | [ResultCallback](#resultcallback) | No | No | Callback for returning remote authentication results. After the remote authentication is complete, the system invokes this callback to return the authentication result to the initiator. |

## userAuth.registerRemoteAuthCallback

registerRemoteAuthCallback(callback: IRemoteAuthCallback): void

Registers a remote authentication callback. This API is used in remote authentication scenarios. After registration, the system can obtain the page parameters required for remote authentication through the callback and receive the authentication result after the authentication is complete. Duplicate registration is not allowed. When the callback is no longer needed, call [unregisterRemoteAuthCallback](#userauthunregisterremoteauthcallback) to unregister it to prevent the callback from being unable to be released.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [IRemoteAuthCallback](#iremoteauthcallback) | Yes | Remote authentication callback API, which includes the callbacks for obtaining authentication widget parameters and returning authentication results. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Permission denied. Called by non-system application. |
| 12500002 | General operation error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userAuth } from '@kit.UserAuthenticationKit';

let remoteAuthCallback: userAuth.IRemoteAuthCallback = {
  onGetRemoteAuthWidgetParam(challenge: Uint8Array): userAuth.WidgetParam {
    console.info('Received challenge for remote auth, length: ' + challenge.length);
    return {
      title: 'Remote Authentication',
      navigationButtonText: 'Cancel'
    } as userAuth.WidgetParam;
  },
  onRemoteAuthResult(challenge: Uint8Array, result: userAuth.UserAuthResult): void {
    console.info('remote auth result, result: ' + result.result + ', authType: ' + result.authType);
  }
};

try {
  userAuth.unregisterRemoteAuthCallback();
  userAuth.registerRemoteAuthCallback(remoteAuthCallback);
  console.info('Remote auth callback registered successfully');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`failed to register remote auth callback. Code is ${err?.code}, message is ${err?.message}`);
}
```

## userAuth.unregisterRemoteAuthCallback

unregisterRemoteAuthCallback(): void

Unregisters the remote authentication callback. This API is used to unregister a previously registered remote authentication callback. After unregistration, the system no longer receives remote authentication page parameter requests or authentication result notification.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Permission denied. Called by non-system application. |
| 12500002 | General operation error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  userAuth.unregisterRemoteAuthCallback();
  console.info('Remote auth callback unregistered successfully');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`failed to unregister remote auth callback. Code is ${err?.code}, message is ${err?.message}`);
}
```