# UserAuthResult

用户认证结果。认证通过时，返回认证类型和认证通过的令牌信息；认证不通过时，返回相应的错误码。该接口用于描述认证完成后的结果信息，应用可通过[IAuthCallback](arkts-userauthentication-iauthcallback-i.md)的
onResult回调获取此结果。

**起始版本：** 10

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## authType

```TypeScript
authType?: UserAuthType
```

认证通过时，返回实际使用的认证类型。当[AuthParam](arkts-userauthentication-authparam-i.md)的authType指定了多种认证类型时，此字段标识用户实际选择并完成认证的类型。

**类型：** UserAuthType

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## enrolledState

```TypeScript
enrolledState?: EnrolledState
```

认证通过时，返回注册凭据的状态。包含当前认证类型的凭据摘要和数量。应用可通过对比此值与之前保存的值，判断用户凭据是否发生变化。若启用了认证结果复用且之前认证使用的凭据已被删除（人脸或指纹），返回的enrolledState中
credentialCount和credentialDigest均为0。

**类型：** EnrolledState

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## result

```TypeScript
result: number
```

用户认证结果。若成功返回SUCCESS(12500000)，若失败返回相应错误码。错误码包括：

- FAIL(12500001)：认证不通过。
- CANCELED(12500003)：认证取消。
- TIMEOUT(12500004)：认证超时。
- LOCKED(12500009)：认证器锁定。
- NOT_ENROLLED(12500010)：未注册凭据。
- PIN_EXPIRED(12500013)：锁屏密码过期。

完整错误码列表参见[UserAuthResultCode](arkts-userauthentication-userauthresultcode-e.md)。

**类型：** number

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## token

```TypeScript
token?: Uint8Array
```

认证通过时，返回认证通过的令牌信息。令牌最大长度为1024字节，包含用户身份认证的凭证，可用于后续的安全操作验证（如支付确认、敏感数据访问等）。令牌中包含认证时的挑战值，业务可通过验证挑战值来防止重放攻击。

**类型：** Uint8Array

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

