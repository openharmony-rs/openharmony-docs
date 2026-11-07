# Querying and Subscribing to User Recognition Results

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=42bb1d1cfb2c2a996a05066eb4307f1fcd2a7053 translatedAt=2026-10-31T02:54:39.666Z pushedAt=2026-10-31T06:09:02.923Z nl=1 -->

Starting from API version 26.0.1, the system supports user identification. The system continuously identifies the current user. Applications can query the latest identification result or subscribe to changes in the identification result to determine whether the current user matches the logged-in system user.

## Interface Description

For details about parameters, return values, error codes, and other descriptions, see [UserRecognitionMgr](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userrecognitionmgr).

| Interface Name | Description |
| -------- | -------- |
| getUserRecognitionMgr(): UserRecognitionMgr \| null | Obtains a UserRecognitionMgr instance for querying and subscribing to user recognition results. |
| getUserRecognitionResult(): Promise\<UserRecognitionResult\> | Obtains the latest user recognition result. |
| onUserRecognitionChange(callback: UserRecognitionResultCallback): void | Subscribes to user recognition result change events. |
| offUserRecognitionChange(callback?: UserRecognitionResultCallback): void | Unsubscribes from user recognition result change events. |

## Development Procedure

1. [Request the permission](prerequisites.md#requesting-permissions): ohos.permission.ACCESS_USER_PASSIVE_RECOGNITION.

   The permission is granted in system_grant mode. You only need to declare it in module.json5.

2. Call [getUserRecognitionMgr](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetuserrecognitionmgr) to obtain an instance.

3. Call [getUserRecognitionResult](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#getuserrecognitionresult) to obtain the latest recognition result, or call [onUserRecognitionChange](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#onuserrecognitionchange) to subscribe to change events.

<!-- @[user_recognition_result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
async obtainingUserRecognitionResult(): Promise<string> {
  try {
    // Obtain the instance.
    let mgr = userAuth.getUserRecognitionMgr();
    if (!mgr) {
      Logger.error('the device does not support user recognition.');
      return 'the device does not support user recognition.';
    }
    // Obtain the latest recognition result.
    let result = await mgr.getUserRecognitionResult();
    Logger.info(`status: ${result.status}, userId: ${result.userId}`);
    // Subscribe to recognition result changes.
    let callback: userAuth.UserRecognitionResultCallback = (recognitionResult: userAuth.UserRecognitionResult) => {
      Logger.info(`status: ${recognitionResult.status}, userId: ${recognitionResult.userId}`);
    };
    mgr.onUserRecognitionChange(callback);
    // Unsubscribe.
    mgr.offUserRecognitionChange(callback);
    return `status: ${result.status}, userId: ${result.userId}`;
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    const errMessage: string = `getUserRecognitionResult failed, Code: ${err?.code}, message: ${err?.message}`;
    Logger.error(errMessage);
    return errMessage;
  }
}
```

## Sample Code

For sample code, see [Querying and Subscribing to User Recognition Results](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/UserAuthentication).
