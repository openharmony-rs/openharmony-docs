# 查询指定认证类型的认证冻结状态

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

调用者需确认指定认证类型是否冻结时，可以使用该接口查询指定认证类型的认证冻结状态，以及剩余可认证次数或还需等待的认证冻结时间。

## 接口说明

具体参数、返回值、错误码等描述，请参考对应的[API文档](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetauthlockstate22)。

| 接口名称 | 功能描述 |
| -------- | -------- |
| getAuthLockState(authType: UserAuthType): Promise\<AuthLockState> | 根据指定的认证类型，查询认证冻结状态，用于判断是否可以发起认证。 | 

## 开发步骤

1. [申请权限](prerequisites.md#申请权限)：ohos.permission.ACCESS_BIOMETRIC。

2. 指定认证类型（[UserAuthType](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8)），并调用[getAuthLockState](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetauthlockstate22)接口查询指定认证类型的认证冻结状态。

以查询PIN认证类型的认证冻结状态为例：

<!-- @[obtain_auth_lock_state_capabilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets) -->

## 示例代码

  - [查询指定认证类型的认证冻结状态](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication)
