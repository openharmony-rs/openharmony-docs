# @ohos.userIAM.userAuth(User Authentication)

The **userAuth** module is the core module for user authentication in OpenHarmony. It provides authentication capabilities in scenarios such as device unlocking, payment verification, and application login.

This module supports multiple biometric authentication methods (face, fingerprint) and password authentication (PIN), and provides various security trust levels. Since API version 26.0.0, the companion device authentication mode is added.

This module applies to the following scenarios:

- Device unlocking authentication.  
- Financial payment verification.  
- Application login protection.  
- Confirmation for sensitive operations.

**Since:** 6

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAuthenticator](arkts-userauthentication-userauth-getauthenticator-f.md) | Obtains an **Authenticator** instance for user authentication. |
| [getAuthInstance](arkts-userauthentication-userauth-getauthinstance-f.md) | Obtains an **AuthInstance** instance for user authentication. |
| [getAuthLockState](arkts-userauthentication-userauth-getauthlockstate-f.md) | Queries the lockout state of the specified authentication type. This API uses a promise to return the result. |
| [getAvailableStatus](arkts-userauthentication-userauth-getavailablestatus-f.md) | Checks whether the specified authentication capability is supported. This API is used to check whether the current device supports the specified authentication type and authentication trust level. It helps an application determine whether the authentication capability is available before initiating authentication, thereby avoiding unnecessary authentication failures. If the query is successful (no error is thrown), the authentication capability is available. If an error is thrown, the application should determine the cause based on the error code and take appropriate measures. |
| [getEnrolledState](arkts-userauthentication-userauth-getenrolledstate-f.md) | Obtains the credential state. This API is used to obtain the credential enrollment information of a specified authentication type, including the credential digest and quantity. The application can compare the current query result with the previously saved result to determine whether the user has added or deleted credentials, and then perform corresponding service processing. |
| [getUserAuthInstance](arkts-userauthentication-userauth-getuserauthinstance-f.md) | Obtains a [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md) instance for user authentication. The user authentication widget is also supported. This API is used to create a user authentication instance. After authentication parameters and UI parameters are configured, you can use the returned instance object to start authentication and subscribe to the authentication result. |
| [getUserRecognitionMgr](arkts-userauthentication-userauth-getuserrecognitionmgr-f.md) | Obtains a [UserRecognitionMgr](arkts-userauthentication-userauth-userrecognitionmgr-i.md) instance, which is used to query and subscribe to the user recognition result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getUserAuthWidgetMgr](arkts-userauthentication-userauth-getuserauthwidgetmgr-f-sys.md) | Obtains the authentication widget manager object. It is used to obtain the **UserAuthWidgetMgr** instance, which can be used to register custom authentication widgets with the system for unified management. |
| [queryReusableAuthResult](arkts-userauthentication-userauth-queryreusableauthresult-f-sys.md) | Queries whether there is any reusable identity authentication result. This API is used to query whether there is an authentication result that meets the reuse conditions before authentication is initiated. If such a result exists, the **AuthToken** that can be reused is returned directly, and the user does not need to perform authentication again. |
| [registerRemoteAuthCallback](arkts-userauthentication-userauth-registerremoteauthcallback-f-sys.md) | Registers a remote authentication callback. This API is used to register a callback in remote authentication scenarios. After the callback is registered, the system can obtain the page parameters required for remote authentication through the callback and receive the authentication result after the authentication is complete. Repeated registration is not allowed. If the callback is not used, call [unregisterRemoteAuthCallback](arkts-userauthentication-userauth-unregisterremoteauthcallback-f-sys.md) to unregister it to avoid callback release failures. |
| [sendNotice](arkts-userauthentication-userauth-sendnotice-f-sys.md) | Sends a notification from the user authentication widget. When the unified authentication widget is used for user authentication, this API is used to receive notifications from the unified authentication widget and send the notifications to the user authentication framework. |
| [unregisterRemoteAuthCallback](arkts-userauthentication-userauth-unregisterremoteauthcallback-f-sys.md) | Unregisters a remote authentication callback. This API is used to unregister a registered remote authentication callback. After the callback is unregistered, the system does not receive requests for page parameters or authentication result notifications for remote authentication. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [UserAuth](arkts-userauthentication-userauth-userauth-c.md) | Provides APIs for managing the **UserAuth** object. |

### Interfaces

| Name | Description |
| --- | --- |
| [Authenticator](arkts-userauthentication-userauth-authenticator-i.md) | Provides APIs for managing the **Authenticator** object. |
| [AuthEvent](arkts-userauthentication-userauth-authevent-i.md) | Provides an asynchronous callback to return the authentication event information. |
| [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md) | Implements user authentication. |
| [AuthLockState](arkts-userauthentication-userauth-authlockstate-i.md) | Enumerates the lockout status of an identity authentication type. This API is used to query the lockout status of a specified authentication type (such as face, fingerprint, or PIN), including whether the authentication type is locked out, the number of remaining attempts, and the lockout duration. If a user fails to be authenticated multiple times, the authenticator may enter a temporary or permanent lockout state. The application can notify the user based on the lockout information. |
| [AuthParam](arkts-userauthentication-userauth-authparam-i.md) | Defines the user authentication parameters. This API is used to configure user authentication parameters, including the challenge value, authentication type list, authentication trust level, and authentication result reuse configuration. By properly configuring these parameters, you can meet authentication requirements in different service scenarios. |
| [AuthResult](arkts-userauthentication-userauth-authresult-i.md) | Represents the authentication result object. |
| [AuthResultInfo](arkts-userauthentication-userauth-authresultinfo-i.md) | Represents the authentication result. |
| [AuthTipInfo](arkts-userauthentication-userauth-authtipinfo-i.md) | Represents the intermediate authentication status. This API is used to describe various intermediate states generated during authentication, including the authentication type and specific status code corresponding to each state. The application can obtain these intermediate states through [AuthTipCallback](arkts-userauthentication-userauth-authtipcallback-t.md) to provide more refined user feedback and status awareness during authentication. |
| [EnrolledState](arkts-userauthentication-userauth-enrolledstate-i.md) | Represents the state of a credential enrolled. This API is used to describe the current state of enrolled authentication credentials (such as face, fingerprint, and companion device), including the credential digest and quantity. The application can call the [getEnrolledState](arkts-userauthentication-userauth-getenrolledstate-f.md) API to query the credential status, and check whether the user's credentials have changed (for example, whether a fingerprint, face, or companion device is added or deleted) to perform corresponding service processing. |
| [IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md) | Provides callbacks to return the authentication result. This API defines the authentication result callback method, which is used to obtain the authentication result after the authentication is complete. By implementing the **onResult** method, the application can obtain the authentication token when the authentication is successful, or obtain the error code and related information when the authentication fails. |
| [IUserAuthCallback](arkts-userauthentication-userauth-iuserauthcallback-i.md) | Provides callbacks to return the authentication result. |
| [ReuseUnlockResult](arkts-userauthentication-userauth-reuseunlockresult-i.md) | Represents information about the authentication result reuse. This API is used to configure parameters related to authentication result reuse, including the reuse mode and validity period. By properly configuring authentication result reuse, you can ensure security while avoiding repeated authentication, improving user experience. |
| [TipInfo](arkts-userauthentication-userauth-tipinfo-i.md) | Represents the tip information displayed during the authentication, which is used to provide feedback during the authentication process. |
| [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md) | Provides APIs for user authentication. The user authentication widget is supported. This API provides complete user authentication capabilities, including subscribing to authentication results and intermediate states, and starting and canceling authentication. The unified authentication widget provides users with a standardized authentication UI and consistent authentication experience. |
| [UserAuthResult](arkts-userauthentication-userauth-userauthresult-i.md) | Represents the user authentication result. If the authentication is successful, the authentication type and token information are returned. If the authentication fails, the corresponding error code is returned. This API is used to describe the result information after the authentication is complete. The application can obtain the result through the **onResult** callback of [IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md). |
| [UserRecognitionMgr](arkts-userauthentication-userauth-userrecognitionmgr-i.md) | Provides APIs for querying and subscribing to user recognition results. Use [getUserRecognitionMgr](arkts-userauthentication-userauth-getuserrecognitionmgr-f.md) to obtain a **UserRecognitionMgr** instance. |
| [UserRecognitionResult](arkts-userauthentication-userauth-userrecognitionresult-i.md) | Defines the user recognition result. |
| [WidgetParam](arkts-userauthentication-userauth-widgetparam-i.md) | Represents the information presented on the user authentication page. This API is used to configure the display style and interaction mode of the authentication screen, including the title, navigation button text, and window mode. By properly setting these parameters, you can provide clear authentication guidance and good interaction experience for users. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AuthParam](arkts-userauthentication-userauth-authparam-i-sys.md) | Defines the user authentication parameters. This API is used to configure user authentication parameters, including the challenge value, authentication type list, authentication trust level, and authentication result reuse configuration. By properly configuring these parameters, you can meet authentication requirements in different service scenarios. |
| [IAuthWidgetCallback](arkts-userauthentication-userauth-iauthwidgetcallback-i-sys.md) | Defines the callback of the authentication widget. The authentication widget uses this callback to obtain commands sent by the user authentication framework and perform corresponding authentication operations based on the command content. |
| [IRemoteAuthCallback](arkts-userauthentication-userauth-iremoteauthcallback-i-sys.md) | Defines the callback of remote authentication. This API is used in remote authentication scenarios to obtain parameters of the remote authentication page and return the authentication result. |
| [UserAuthWidgetMgr](arkts-userauthentication-userauth-userauthwidgetmgr-i-sys.md) | Defines the authentication widget manager. It is used to register the custom authentication widget with the **UserAuthWidgetMgr** for unified management and scheduling. The custom authentication widget can receive commands from the user authentication framework and perform corresponding operations. |
| [WidgetParam](arkts-userauthentication-userauth-widgetparam-i-sys.md) | Represents the information presented on the user authentication page. This API is used to configure the display style and interaction mode of the authentication screen, including the title, navigation button text, and window mode. By properly setting these parameters, you can provide clear authentication guidance and good interaction experience for users. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AuthenticationResult](arkts-userauthentication-userauth-authenticationresult-e.md) | Enumerates the authentication results. |
| [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md) | Enumerates the trust levels of the authentication result. This enum defines four trust levels of the authentication result, which are used to describe the security strength of the authentication result. A higher trust level indicates a stronger liveness detection capability and more accurate user identity recognition of the authentication solution, and is applicable to service scenarios that require higher security. The application should select a proper authentication trust level based on the security requirements of service scenarios. |
| [FaceTips](arkts-userauthentication-userauth-facetips-e.md) | Enumerates the tip codes used during the facial authentication process. |
| [FingerprintTips](arkts-userauthentication-userauth-fingerprinttips-e.md) | Enumerates the tip codes used during the fingerprint authentication process. |
| [ResultCode](arkts-userauthentication-userauth-resultcode-e.md) | Enumerates the authentication result codes. |
| [ReuseMode](arkts-userauthentication-userauth-reusemode-e.md) | Enumerates the modes for reusing authentication results. This enum defines four modes for reusing authentication results and is used to control which authentication results can be reused under what conditions. The application can select a proper reuse mode based on the service scenario to balance security and user experience. |
| [UserAuthResultCode](arkts-userauthentication-userauth-userauthresultcode-e.md) | Enumerates the authentication result codes. They include all success codes and error codes for user authentication operations. The application can determine the authentication result based on the return code and take corresponding measures. |
| [UserAuthTipCode](arkts-userauthentication-userauth-userauthtipcode-e.md) | Enumerates the intermediate states of identity authentication. This enum is used to describe various intermediate states during authentication, including authentication failure, timeout, lockout, and loading and release of the authentication screen. Applications can subscribe to these intermediate states through the [on('authTip')](arkts-userauthentication-userauth-userauthinstance-i.md#onauthtip) API to provide more refined user feedback and status awareness during authentication. |
| [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | Enumerates the identity authentication types. This enum defines the authentication types supported by the system, including PIN authentication and biometric authentication (face and fingerprint). When initiating authentication, an application needs to specify the authentication type list, and the user can select any of the authentication types to complete the authentication. The security strength and user experience vary depending on authentication types. The application needs to select a proper authentication type based on service scenarios. |
| [UserRecognitionStatus](arkts-userauthentication-userauth-userrecognitionstatus-e.md) | Enumerates the user recognition status. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [NoticeType](arkts-userauthentication-userauth-noticetype-e-sys.md) | Enumerates the notification types of user authentication. This enum defines the notification types supported by the system, which are used to identify the source of a notification. |
| [UserAuthResultCode](arkts-userauthentication-userauth-userauthresultcode-e-sys.md) | Enumerates the authentication result codes. They include all success codes and error codes for user authentication operations. The application can determine the authentication result based on the return code and take corresponding measures. |
| [UserAuthType](arkts-userauthentication-userauth-userauthtype-e-sys.md) | Enumerates the identity authentication types. This enum defines the authentication types supported by the system, including PIN authentication and biometric authentication (face and fingerprint). When initiating authentication, an application needs to specify the authentication type list, and the user can select any of the authentication types to complete the authentication. The security strength and user experience vary depending on authentication types. The application needs to select a proper authentication type based on service scenarios. |
| [WindowModeType](arkts-userauthentication-userauth-windowmodetype-e-sys.md) | Enumerates the display types of the user authentication screen. This enum defines the display modes that can be used on the authentication screen and is used to control the window style of the system authentication widget. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md) | Defines the keyword of the authentication event type. It is used as a parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on). |
| [AuthTipCallback](arkts-userauthentication-userauth-authtipcallback-t.md) | Defines the callback to return the intermediate authentication status. This callback is used to obtain various intermediate status information during authentication, including authentication failure, lockout, and loading and release of the authentication screen. By subscribing to these intermediate statuses, the application can provide more refined user interaction and status management during the authentication process. |
| [AuthType](arkts-userauthentication-userauth-authtype-t.md) | Enumerates the authentication types. |
| [EventInfo](arkts-userauthentication-userauth-eventinfo-t.md) | Enumerates the authentication event information types. |
| [SecureLevel](arkts-userauthentication-userauth-securelevel-t.md) | Enumerates the authentication security levels. |
| [UserRecognitionResultCallback](arkts-userauthentication-userauth-userrecognitionresultcallback-t.md) | Defines the callback used to receive the user recognition result. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ResultCallback](arkts-userauthentication-userauth-resultcallback-t-sys.md) | Triggered to return the remote authentication result. This callback type is used in remote authentication scenarios. After remote authentication is complete, the system calls this callback function to return the authentication result. |
| [WidgetParamCallback](arkts-userauthentication-userauth-widgetparamcallback-t-sys.md) | Triggered to obtain remote authentication page parameters. This callback type is used in remote authentication scenarios. When the system needs to obtain the configuration parameters of the remote authentication page, it calls this callback function. |
<!--DelEnd-->

### Constants

| Name | Description |
| --- | --- |
| [MAX_ALLOWABLE_REUSE_DURATION](arkts-userauthentication-userauth-con.md#max_allowable_reuse_duration) | Maximum reuse duration of the authentication result, in milliseconds. The value is **300000** (5 minutes). This constant is used to limit the maximum duration for reusing an authentication result, preventing security risks caused by reusing expired authentication results for a long time. It can be used as the maximum value of the **reuseDuration** parameter in [ReuseUnlockResult](arkts-userauthentication-userauth-reuseunlockresult-i.md). |
| [PERMANENT_LOCKOUT_DURATION](arkts-userauthentication-userauth-con.md#permanent_lockout_duration) | Permanent lockout duration, in milliseconds. The value is **0x7fffffff**. When the number of failed authentication attempts reaches the upper limit, the authenticator enters the permanent lockout status. In this case, PIN authentication is required for unlocking. This value is used to identify the permanent lockout status of the authenticator, which can be returned by the **lockoutDuration** field in [AuthLockState](arkts-userauthentication-userauth-authlockstate-i.md). |
