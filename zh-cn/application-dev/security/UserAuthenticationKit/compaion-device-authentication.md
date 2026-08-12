# 伴随设备认证

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，用户认证服务新增伴随设备认证方式。用户可通过佩戴的伴随设备完成身份认证。

## 接口说明

具体参数、返回值、错误码等描述，请参考对应的[@ohos.userIAM.userAuth (用户认证)](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md)

| 接口名称 | 功能描述 |
| -------- | -------- |
| getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance | 获取UserAuthInstance对象，用于执行用户身份认证。发起伴随设备认证时，[AuthParam](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authparam10)的authType需指定为[UserAuthType.COMPANION_DEVICE](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8)。 |
| on(type: 'result', callback: IAuthCallback): void | 订阅用户身份认证结果。 |
| off(type: 'result', callback?: IAuthCallback): void | 取消订阅用户身份认证结果。 |
| start(): void | 执行用户认证。 |

## 伴随设备无感认证

发起伴随设备认证前需先在主设备上“设置->生物识别与密码->协同认证”页面添加伴随设备。具体流程如下图：

![companion_device_auth_1](figures/companion_device_auth_1.png)

> **说明：**
>
> 发起伴随设备认证时，[AuthParam](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authparam10)的authType只能指定为[UserAuthType.COMPANION_DEVICE](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8)，不能与PIN、FACE、FINGERPRINT同时指定。

## 开发准备

1. [申请权限](prerequisites.md#申请权限)：ohos.permission.ACCESS_BIOMETRIC。

2. 指定用户认证相关参数[AuthParam](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authparam10)（包括挑战值、认证类型[UserAuthType.COMPANION_DEVICE](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8)和认证等级[AuthTrustLevel](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authtrustlevel8)）、配置认证控件界面[WidgetParam](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#widgetparam10)，调用[getUserAuthInstance](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetuserauthinstance10)获取认证对象。

3. 调用[UserAuthInstance.on('result')](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#onresult10-1)接口订阅认证结果。

4. 调用[UserAuthInstance.start](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#start10)接口发起认证，通过[IAuthCallback](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#iauthcallback10)回调返回认证结果[UserAuthResult](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthresult10)。当认证成功时返回认证通过类型（[UserAuthType](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8)）和令牌信息（AuthToken）。

**示例**

发起伴随设备认证，采用认证可信等级≥ATL2的伴随设备认证，获取认证结果。

<!-- @[companion_device_authentication_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
initiatingCompanionDeviceAuthentication() {
  try {
    const randData = getRandData();
    if (!randData) {
      return;
    }
    // 设置认证参数，认证类型指定为伴随设备认证
    const authParam: userAuth.AuthParam = {
      challenge: randData,
      authType: [userAuth.UserAuthType.COMPANION_DEVICE],
      authTrustLevel: userAuth.AuthTrustLevel.ATL2,
    };
    // 配置认证界面
    const widgetParam: userAuth.WidgetParam = {
      title: resourceToString($r('app.string.title')),
    };
    // 获取认证对象
    const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
    Logger.info('get userAuth instance successfully.');
    // 订阅认证结果
    userAuthInstance.on('result', {
      onResult: (result: userAuth.UserAuthResult) => {
        try {
          Logger.info('userAuthInstance callback.');
          this.result[ResultIndex.EXAMPLE_1] = (`${result.result}`);
          // 可在认证结束或其他业务需要场景，取消订阅认证结果。
          userAuthInstance.off('result');
        } catch (error) {
          const err: BusinessError = error as BusinessError;
          Logger.error(`onResult failed, code: ${err?.code}, Message: ${err?.message}`);
        }
      }
    });
    // 启动认证
    userAuthInstance.start();
    Logger.info('auth start successfully.');
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    Logger.error(`auth failed, code is ${err?.code}, message is ${err?.message}`);
  }
}
```

## 示例代码

  - [伴随设备认证](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/UserAuthentication)
