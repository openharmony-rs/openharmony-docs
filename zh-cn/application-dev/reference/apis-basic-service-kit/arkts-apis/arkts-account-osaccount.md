# @ohos.account.osAccount

本模块提供管理系统账号的基础能力，包括系统账号的添加、删除、查询、设置、订阅、启动等功能。

**起始版本：** 7

<!--Device-unnamed-declare namespace osAccount--><!--Device-unnamed-declare namespace osAccount-End-->

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAccountManager](arkts-basicservices-osaccount-getaccountmanager-f.md#getaccountmanager-1) | 获取系统账号管理对象。 |
| [isDomainAccountSupported](arkts-basicservices-osaccount-isdomainaccountsupported-f.md#isdomainaccountsupported-1) | 检查是否支持域账号。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAuthorizationManager](arkts-basicservices-osaccount-getauthorizationmanager-f-sys.md#getauthorizationmanager-1) | 获取系统账号授权管理器。 |
| [getOsAccountSubProfileManager](arkts-basicservices-osaccount-getosaccountsubprofilemanager-f-sys.md#getosaccountsubprofilemanager-1) | 获取系统账号子身份资料管理器。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [DomainAccountManager](arkts-basicservices-osaccount-domainaccountmanager-c.md) | 域账号管理类。 |
| [DomainServerConfigManager](arkts-basicservices-osaccount-domainserverconfigmanager-c.md) | 域服务器配置管理类。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DomainAccountManager](arkts-basicservices-osaccount-domainaccountmanager-c-sys.md) | 域账号管理类。 |
| [InputerManager](arkts-basicservices-osaccount-inputermanager-c-sys.md) | 凭据输入管理器。 |
| [PINAuth](arkts-basicservices-osaccount-pinauth-c-sys.md) | PIN码认证基类。 |
| [UserAuth](arkts-basicservices-osaccount-userauth-c-sys.md) | 用户认证类。 |
| [UserIdentityManager](arkts-basicservices-osaccount-useridentitymanager-c-sys.md) | 获取用户身份管理类。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccountManager](arkts-basicservices-osaccount-accountmanager-i.md) | 系统账号管理类。 |
| [CreateOsAccountForDomainOptions](arkts-basicservices-osaccount-createosaccountfordomainoptions-i.md) | 表示用于创建与指定域账号绑定的系统账号的可选参数。继承自[CreateOsAccountOptions](arkts-basicservices-osaccount-createosaccountoptions-i-sys.md)。 |
| [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 表示域账号信息。 |
| [DomainServerConfig](arkts-basicservices-osaccount-domainserverconfig-i.md) | 域服务器配置。 |
| [OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md) | 表示系统账号信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccountManager](arkts-basicservices-osaccount-accountmanager-i-sys.md) | 系统账号管理类。 |
| [AcquireAuthorizationOptions](arkts-basicservices-osaccount-acquireauthorizationoptions-i-sys.md) | 表示获取授权的选项。 |
| [AcquireAuthorizationResult](arkts-basicservices-osaccount-acquireauthorizationresult-i-sys.md) | 表示获取授权的结果。 |
| [AuthOptions](arkts-basicservices-osaccount-authoptions-i-sys.md) | 表示[认证用户](arkts-basicservices-osaccount-userauth-c-sys.md#auth-2)的可选参数集合。 |
| [AuthResult](arkts-basicservices-osaccount-authresult-i-sys.md) | 表示认证结果的信息。 |
| [AuthStatusInfo](arkts-basicservices-osaccount-authstatusinfo-i-sys.md) | 表示认证状态信息。 |
| [AuthorizationManager](arkts-basicservices-osaccount-authorizationmanager-i-sys.md) | 系统账号授权管理类，用于管理系统账号授权。 |
| [ConstraintChangeInfo](arkts-basicservices-osaccount-constraintchangeinfo-i-sys.md) | 表示约束变更信息。 |
| [ConstraintSourceTypeInfo](arkts-basicservices-osaccount-constraintsourcetypeinfo-i-sys.md) | 表示约束来源类型信息。 |
| [CreateOsAccountOptions](arkts-basicservices-osaccount-createosaccountoptions-i-sys.md) | 表示用于创建系统账号的可选参数。 |
| [CredentialChangeInfo](arkts-basicservices-osaccount-credentialchangeinfo-i-sys.md) | 表示凭据变更信息。 |
| [CredentialInfo](arkts-basicservices-osaccount-credentialinfo-i-sys.md) | 表示凭证信息。 |
| [DomainAccountAuthOptions](arkts-basicservices-osaccount-domainaccountauthoptions-i-sys.md) | 表示域账号认证的选项。 |
| [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 表示域账号信息。 |
| [DomainPlugin](arkts-basicservices-osaccount-domainplugin-i-sys.md) | 域插件，提供域账号认证功能。 |
| [EnrolledCredInfo](arkts-basicservices-osaccount-enrolledcredinfo-i-sys.md) | 表示已注册凭据的信息。 |
| [ExecutorProperty](arkts-basicservices-osaccount-executorproperty-i-sys.md) | 提供执行器的属性。 |
| [GetAuthInfoOptions](arkts-basicservices-osaccount-getauthinfooptions-i-sys.md) | 表示[查询认证凭据信息](arkts-basicservices-osaccount-useridentitymanager-c-sys.md#getauthinfo-4)的可选参数集合。 |
| [GetDomainAccessTokenOptions](arkts-basicservices-osaccount-getdomainaccesstokenoptions-i-sys.md) | 表示获取域访问令牌的选项。 |
| [GetDomainAccountInfoOptions](arkts-basicservices-osaccount-getdomainaccountinfooptions-i-sys.md) | 表示查询域账号信息的选项。 |
| [GetDomainAccountInfoPluginOptions](arkts-basicservices-osaccount-getdomainaccountinfopluginoptions-i-sys.md) | 表示插件查询域账号信息的选项。GetDomainAccountInfoPluginOptions类继承[GetDomainAccountInfoOptions](arkts-basicservices-osaccount-getdomainaccountinfooptions-i-sys.md) |
| [GetInputDataOptions](arkts-basicservices-osaccount-getinputdataoptions-i-sys.md) | 表示[通知调用者获取数据](../../../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#ongetdata8)的可选参数集合。 |
| [GetPropertyRequest](arkts-basicservices-osaccount-getpropertyrequest-i-sys.md) | 提供获取属性请求的信息。 |
| [IIdmCallback](arkts-basicservices-osaccount-iidmcallback-i-sys.md) | 表示身份管理回调类。 |
| [IInputData](arkts-basicservices-osaccount-iinputdata-i-sys.md) | 密码数据回调。 |
| [IInputer](arkts-basicservices-osaccount-iinputer-i-sys.md) | 凭据输入器回调。 |
| [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 表示用户认证回调类。 |
| [OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i-sys.md) | 表示系统账号信息。 |
| [OsAccountSubProfile](arkts-basicservices-osaccount-osaccountsubprofile-i-sys.md) | 系统账号子Profile的定义 |
| [OsAccountSubProfileEventData](arkts-basicservices-osaccount-osaccountsubprofileeventdata-i-sys.md) | 表示系统账号子Profile事件数据。 |
| [OsAccountSubProfileManager](arkts-basicservices-osaccount-osaccountsubprofilemanager-i-sys.md) | 系统账号子身份资料管理器类。 |
| [OsAccountSwitchEventData](arkts-basicservices-osaccount-osaccountswitcheventdata-i-sys.md) | 表示系统账号前后台开始切换和结束切换事件的数据结构。 |
| [RemoteAuthOptions](arkts-basicservices-osaccount-remoteauthoptions-i-sys.md) | 表示远程认证的可选参数集合。 |
| [RemoveOsAccountOptions](arkts-basicservices-osaccount-removeosaccountoptions-i-sys.md) | 表示用于删除系统账号的可选参数。 |
| [RequestResult](arkts-basicservices-osaccount-requestresult-i-sys.md) | 表示请求结果的信息。 |
| [SetOsAccountTypeOptions](arkts-basicservices-osaccount-setosaccounttypeoptions-i-sys.md) | 设置系统账号类型的选项。 |
| [SetPropertyRequest](arkts-basicservices-osaccount-setpropertyrequest-i-sys.md) | 提供设置属性请求的信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md) | 表示系统账号类型的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthIntent](arkts-basicservices-osaccount-authintent-e-sys.md) | 表示认证意图的枚举。 |
| [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md) | 表示用于认证的凭据子类型的枚举。 |
| [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | 表示认证结果的受信任级别的枚举。 |
| [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | 表示身份验证的凭据类型的枚举。 |
| [AuthorizationResultCode](arkts-basicservices-osaccount-authorizationresultcode-e-sys.md) | 表示授权结果码的枚举。 |
| [ConstraintSourceType](arkts-basicservices-osaccount-constraintsourcetype-e-sys.md) | 表示约束来源类型的枚举。 |
| [CredentialChangeType](arkts-basicservices-osaccount-credentialchangetype-e-sys.md) | 表示凭据变更类型的枚举。 |
| [FaceTipsCode](arkts-basicservices-osaccount-facetipscode-e-sys.md) | 表示人脸验证过程中提示的枚举。 |
| [FingerprintTips](arkts-basicservices-osaccount-fingerprinttips-e-sys.md) | 表示指纹身份验证过程中提示的枚举。 |
| [GetPropertyType](arkts-basicservices-osaccount-getpropertytype-e-sys.md) | 表示要获取的属性类型的枚举。 |
| [Module](arkts-basicservices-osaccount-module-e-sys.md) | 表示获取信息的模块的枚举。 |
| [OsAccountSubProfileEvent](arkts-basicservices-osaccount-osaccountsubprofileevent-e-sys.md) | 枚举系统账号子profile的事件。 |
| [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e-sys.md) | 表示系统账号类型的枚举。 |
| [ResultCode](arkts-basicservices-osaccount-resultcode-e-sys.md) | 表示身份验证结果码。 |
| [SetPropertyType](arkts-basicservices-osaccount-setpropertytype-e-sys.md) | 表示要设置的属性类型的枚举。 |
<!--DelEnd-->

