# 查询和订阅用户识别结果

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

从API版本26.0.1开始，系统支持用户识别。系统持续识别当前使用者。应用可查询最新识别结果或订阅识别结果变化，用于判断当前使用者是否与已登录的系统用户匹配。

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
// The API 26 public SDK removed getUserRecognitionMgr / UserRecognitionResult /
// UserRecognitionResultCallback (passive recognition); keep the entry and report unsupported.
async obtainingUserRecognitionResult(): Promise<string> {
  const message: string = 'user recognition is not supported by current SDK (API 26).';
  Logger.info(message);
  return message;
}
```

## 示例代码

  - 可参考[用户认证服务](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/UserAuthentication)示例代码。
