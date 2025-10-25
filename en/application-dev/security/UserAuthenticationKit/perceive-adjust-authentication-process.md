# Perceiving and Adjusting the Authentication Process

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

From API version 20, you can adjust and perceive the authentication process using related APIs.

Adjusting the authentication process: When initiating authentication, the application can control whether to skip the disabled biometric authentication by using the **skipLockedBiometricAuth** property of the [AuthParam](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authparam10) parameter.

Perceiving the authentication process: The application registers a callback through the [on](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#on20) API to obtain the prompts for starting and exiting the components during authentication, and each authentication failure during authentication. The correct sequence is as follows: Register a callback through **on**, and then initiate authentication through [start](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#start10). The callback can receive information only after the authentication is successfully initiated.

## Available APIs

For details about the parameters, return value, and error codes, see [getAvailableStatus](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md).

| API| Feature Description| 
| ------- | ------- |
| AuthParam | User authentication parameters, including the challenge value, authentication type list, and authentication level.<br>You can use the **skipLockedBiometricAuth** parameter to determine whether to skip the disabled biometric authentication.<br>**true**: When biometric authentication is frozen, the system automatically skips the countdown page and directly switches to another authentication mode.<br>**false** (default): The countdown page is not skipped.|
| on(type: 'authTip', callback: AuthTipCallback): void | Subscribes to authentication tip information.| 
| off(type: 'authTip', callback?: AuthTipCallback): void | Unsubscribe from authentication tip information.| 

## How to Develop

1. Check that the application has the ohos.permission.ACCESS_BIOMETRIC permission. For details about how to request permissions, see [Requesting Permissions](prerequisites.md#requesting-permissions).

2. Set [AuthParam](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authparam10) (including the challenge, [UserAuthType](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8), and [AuthTrustLevel](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authtrustlevel8)), configure [WidgetParam](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#widgetparam10), and use [getUserAuthInstance](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetuserauthinstance10) to obtain a **UserAuthInstance** instance.

3. Call [UserAuthInstance.on](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#on20) to subscribe to the authentication tip information.

4. Call [UserAuthInstance.start](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#start10) to initiate authentication. The [AuthTipCallback](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authtipcallback20) callback returns the intermediate authentication status [AuthTipInfo](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authtipinfo20).

5. After the authentication is successful, call [UserAuthInstance.off](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#off20) to unsubscribe from the authentication tip information.

The following code snippet shows how to skip the disabled biometric authentication and subscribe to the authentication information:

<!-- @[perceive-adjust-authentication-process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  perceiveAndAdjustAuthentication() {
    try {
      const randData = getRandData();
      if (!randData) {
        return;
      }
      // Set authentication parameters.
      const authParam: userAuth.AuthParam = {
        challenge: randData,
        authType: [userAuth.UserAuthType.PIN, userAuth.UserAuthType.FACE, userAuth.UserAuthType.FINGERPRINT],
        authTrustLevel: userAuth.AuthTrustLevel.ATL3,
        skipLockedBiometricAuth: true
      };
      // Set the authentication page.
      const widgetParam: userAuth.WidgetParam = {
        title: resourceToString($r('app.string.title')),
      };
      // Obtain an authentication object.
      const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
      Logger.info('get userAuth instance success');
      // Subscribe to authentication tip information.
      userAuthInstance.on('authTip', (authTipInfo: userAuth.AuthTipInfo) => {
        try {
          Logger.info(`userAuthInstance callback authTipInfo = ${JSON.stringify(authTipInfo)}`);
          this.result[ResultIndex.PERCEIVE_ADJUST] = (`${authTipInfo.tipType}`);
          // Unsubscribe from the information after authentication is complete.
          userAuthInstance.off('result');
        } catch (error) {
          const err: BusinessError = error as BusinessError;
          Logger.error(`onResult catch error. Code: ${err?.code}, Message: ${err?.message}`);
        }
      });
      // Start user authentication.
      userAuthInstance.start();
	// ···
        // Unsubscribe from authentication tip information.
        userAuthInstance.off('authTip');
        Logger.info('off authTip success');
        // Cancel the authentication.
        userAuthInstance.cancel();
        Logger.info('auth cancel success');
		// ···
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      Logger.error(`auth catch error, code is ${err?.code as number}, message is ${err?.message}`);
    }
  }

```


## Sample Code

  - [Perceiving and adjusting the authentication process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication)
