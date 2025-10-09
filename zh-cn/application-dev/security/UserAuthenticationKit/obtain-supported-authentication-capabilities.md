# 查询支持的认证能力

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

不同的设备对于认证能力（人脸、指纹、口令）的支持性各有差异，开发者在发起认证前应当先查询当前设备支持的用户认证能力。

## 接口说明

具体参数、返回值、错误码等描述，请参考对应的[API文档](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetavailablestatus9)。

| 接口名称 | 功能描述 | 
| -------- | -------- |
| getAvailableStatus(authType : UserAuthType, authTrustLevel : AuthTrustLevel): void | 根据指定的认证类型、认证等级，检测当前设备是否支持相应的认证能力。 | 

## 开发步骤

1. [申请权限](prerequisites.md#申请权限)：ohos.permission.ACCESS_BIOMETRIC。

2. 指定认证类型（[UserAuthType](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8)）和认证等级（[AuthTrustLevel](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authtrustlevel8)），调用[getAvailableStatus](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetavailablestatus9)接口查询当前的设备是否支持相应的认证能力。

   认证可信等级的详细介绍请参见[认证可信等级划分原则](../../security/UserAuthenticationKit/user-authentication-overview.md#生物认证可信等级划分原则)。

以查询设备是否支持认证可信等级≥ATL3的人脸认证功能为例：

<!-- @[obtain_supported_capabilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  obtainingSupported() {
    try {
      // 查询认证能力是否支持
      userAuth.getAvailableStatus(userAuth.UserAuthType.PIN, userAuth.AuthTrustLevel.ATL1);
      Logger.info('current auth trust level is supported');
      return true;
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      Logger.error(`current auth trust level is not supported, code is ${err?.code}, message is ${err?.message}`);
      return false;
    }
  }

```


## 示例代码

  - [查询支持的认证能力](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication)
