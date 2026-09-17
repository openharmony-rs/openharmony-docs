# 查询和订阅用户识别结果

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

从API版本26.1.0开始，系统支持用户识别。系统持续识别当前使用者。应用可查询最新识别结果或订阅识别结果变化，用于判断当前使用者是否与已登录的系统用户匹配。

## 接口说明

具体参数、返回值、错误码等描述，请参考[UserRecognitionMgr](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userrecognitionmgr)。

| 接口名称 | 功能描述 |
| -------- | -------- |
| getUserRecognitionMgr(): UserRecognitionMgr \| null | 获取UserRecognitionMgr实例，用于查询和订阅用户识别结果。 |
| getUserRecognitionResult(): Promise\<UserRecognitionResult\> | 获取最新的用户识别结果。 |
| onUserRecognitionChange(callback: UserRecognitionResultCallback): void | 订阅用户识别结果变化事件。 |
| offUserRecognitionChange(callback?: UserRecognitionResultCallback): void | 取消订阅用户识别结果变化事件。 |

## 开发步骤

1. [申请权限](prerequisites.md#申请权限)：ohos.permission.ACCESS_USER_PASSIVE_RECOGNITION。

   该权限授权方式为system_grant，在module.json5中声明即可获取。

2. 调用[getUserRecognitionMgr](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetuserrecognitionmgr)获取实例。

3. 调用[getUserRecognitionResult](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#getuserrecognitionresult)获取最新识别结果，或调用[onUserRecognitionChange](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#onuserrecognitionchange)订阅变化事件。

<!-- @[user_recognition_result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
async obtainingUserRecognitionResult(): Promise<string> {
  try {
    // 获取实例
    let mgr = userAuth.getUserRecognitionMgr();
    if (!mgr) {
      Logger.error('the device does not support user recognition.');
      return 'the device does not support user recognition.';
    }
    // 获取最新识别结果
    let result = await mgr.getUserRecognitionResult();
    Logger.info(`status: ${result.status}, userId: ${result.userId}`);
    // 订阅识别结果变化
    let callback: userAuth.UserRecognitionResultCallback = (recognitionResult: userAuth.UserRecognitionResult) => {
      Logger.info(`status: ${recognitionResult.status}, userId: ${recognitionResult.userId}`);
    };
    mgr.onUserRecognitionChange(callback);
    // 取消订阅
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

## 示例代码

示例代码可参考[查询和订阅用户识别结果](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/UserAuthentication)。
