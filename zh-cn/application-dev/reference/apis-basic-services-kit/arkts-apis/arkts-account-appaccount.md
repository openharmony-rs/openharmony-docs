# @ohos.account.appAccount(应用账号管理)

本模块提供应用账号信息的添加、删除、修改和查询基础能力。应用账号管理采用应用级账号隔离机制，每个应用的账号信息独立管理。

**起始版本：** 7

**系统能力：** SystemCapability.Account.AppAccount

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAppAccountManager(应用账号管理)](arkts-basicservices-appaccount-createappaccountmanager-f.md) | 创建应用账号管理器对象。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Authenticator(应用账号管理)](arkts-basicservices-appaccount-authenticator-c.md) | 认证器基类。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AppAccountInfo(应用账号管理)](arkts-basicservices-appaccount-appaccountinfo-i.md) | 表示应用账号信息。 |
| [AppAccountManager(应用账号管理)](arkts-basicservices-appaccount-appaccountmanager-i.md) | 应用账号管理器，可用于管理应用自身的账号信息。 |
| [AuthCallback(应用账号管理)](arkts-basicservices-appaccount-authcallback-i.md) | 认证器回调类。 |
| [AuthenticatorCallback(应用账号管理)](arkts-basicservices-appaccount-authenticatorcallback-i.md) | OAuth认证器回调接口。 |
| [AuthenticatorInfo(应用账号管理)](arkts-basicservices-appaccount-authenticatorinfo-i.md) | 表示OAuth认证器信息。 |
| [AuthResult(应用账号管理)](arkts-basicservices-appaccount-authresult-i.md) | 表示认证结果信息。 |
| [AuthTokenInfo(应用账号管理)](arkts-basicservices-appaccount-authtokeninfo-i.md) | 表示Auth令牌信息。 |
| [CreateAccountImplicitlyOptions(应用账号管理)](arkts-basicservices-appaccount-createaccountimplicitlyoptions-i.md) | 表示隐式创建账号的选项。 |
| [CreateAccountOptions(应用账号管理)](arkts-basicservices-appaccount-createaccountoptions-i.md) | 表示创建账号的选项。 |
| [OAuthTokenInfo(应用账号管理)](arkts-basicservices-appaccount-oauthtokeninfo-i.md) | 表示OAuth令牌信息。 |
| [SelectAccountsOptions(应用账号管理)](arkts-basicservices-appaccount-selectaccountsoptions-i.md) | 表示用于选择账号的选项。 |
| [SetPropertiesOptions(应用账号管理)](arkts-basicservices-appaccount-setpropertiesoptions-i.md) | 表示用于设置属性的选项。 |
| [VerifyCredentialOptions(应用账号管理)](arkts-basicservices-appaccount-verifycredentialoptions-i.md) | 表示用于验证凭据的选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Constants(应用账号管理)](arkts-basicservices-appaccount-constants-e.md) | 表示常量的枚举。 |
| [ResultCode(应用账号管理)](arkts-basicservices-appaccount-resultcode-e.md) | 表示返回码的枚举。 |
