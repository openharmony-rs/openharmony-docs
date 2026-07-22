# @ohos.userIAM.userAuth

**userAuth**模块是OpenHarmony系统中用于用户身份认证的核心模块，提供了设备解锁、支付验证、应用登录等场景下的身份认证能力。

该模块支持多种生物特征认证方式（人脸、指纹）和密码认证（PIN），并提供不同级别的安全信任等级。从API版本26.0.0开始，新增伴随设备认证的方式。

该模块主要用于以下场景：

- 设备解锁认证。  
- 金融支付验证。  
- 应用登录保护。  
- 敏感操作确认。

**起始版本：** 6

<!--Device-unnamed-declare namespace userAuth--><!--Device-unnamed-declare namespace userAuth-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAuthInstance](arkts-userauthentication-userauth-getauthinstance-f.md#getauthinstance) | 获取AuthInstance对象，用于执行用户身份认证。 |
| [getAuthLockState](arkts-userauthentication-userauth-getauthlockstate-f.md#getauthlockstate) | 查询指定认证类型的冻结状态，使用Promise异步回调。 |
| [getAuthenticator](arkts-userauthentication-userauth-getauthenticator-f.md#getauthenticator) | 获取Authenticator对象，用于执行用户身份认证。 |
| [getAvailableStatus](arkts-userauthentication-userauth-getavailablestatus-f.md#getavailablestatus) | 查询指定类型和等级的认证能力是否支持。该接口用于检查当前设备是否支持指定的认证类型和认证可信等级，帮助应用在发起认证前判断认证能力是否可用，从而避免不必要的认证不通过。若查询通过（无错误抛出），表示认证能力可用；若抛出错误，应用应根据错误码判断具体原因并采取相应处理。 |
| [getEnrolledState](arkts-userauthentication-userauth-getenrolledstate-f.md#getenrolledstate) | 查询凭据注册的状态，以检测用户注册凭据的变更。该接口用于获取指定认证类型的凭据注册信息，包括凭据摘要和数量。应用可通过对比当前查询结果与之前保存的结果，判断用户是否新增或删除了凭据，从而采取相应的业务处理。 |
| [getUserAuthInstance](arkts-userauthentication-userauth-getuserauthinstance-f.md#getuserauthinstance) | 获取[UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md)对象，执行用户身份认证，并支持使用统一用户身份认证控件。该接口用于创建一个用户认证实例，配置认证参数和界面参数后，可通过返回的实例对象启动认证、订阅认证结果等。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getUserAuthWidgetMgr](arkts-userauthentication-userauth-getuserauthwidgetmgr-f-sys.md#getuserauthwidgetmgr) | 获取身份认证组件管理器对象。用于获取UserAuthWidgetMgr实例，通过该实例可将自定义身份认证控件注册到系统进行统一管理。 |
| [queryReusableAuthResult](arkts-userauthentication-userauth-queryreusableauthresult-f-sys.md#queryreusableauthresult) | 查询是否有可复用的身份认证结果。该接口用于在发起认证前查询是否存在满足复用条件的认证结果，若存在则直接返回可复用的AuthToken，无需用户再次进行认证交互。 |
| [registerRemoteAuthCallback](arkts-userauthentication-userauth-registerremoteauthcallback-f-sys.md#registerremoteauthcallback) | 注册远程认证回调。 |
| [sendNotice](arkts-userauthentication-userauth-sendnotice-f-sys.md#sendnotice) | 发送来自身份认证组件的通知。在使用统一身份认证控件进行用户身份认证时，该接口用于接收来自统一身份认证组件的通知，并将通知发送给用户认证框架。 |
| [unregisterRemoteAuthCallback](arkts-userauthentication-userauth-unregisterremoteauthcallback-f-sys.md#unregisterremoteauthcallback) | 取消注册远程身份验证的回调。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [UserAuth](arkts-userauthentication-userauth-userauth-c.md) | 认证器对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AuthEvent](arkts-userauthentication-userauth-authevent-i.md) | 认证接口的异步回调对象。 |
| [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md) | 执行用户认证的对象。 |
| [AuthLockState](arkts-userauthentication-userauth-authlockstate-i.md) | 认证类型的身份认证冻结状态。该接口用于查询指定认证类型（如人脸、指纹、PIN）当前的冻结状态，包括是否被冻结、剩余尝试次数和冻结时长等信息。当用户多次认证不通过后，认证器可能进入临时冻结或永久冻结状态，应用可根据冻结信息提示用户。 |
| [AuthParam](arkts-userauthentication-userauth-authparam-i.md) | 用户认证相关参数。该接口用于配置用户认证的各项参数，包括挑战值、认证类型列表、认证信任等级、认证结果复用配置等。通过合理配置这些参数，可以满足不同业务场景下的认证需求。 |
| [AuthResult](arkts-userauthentication-userauth-authresult-i.md) | 表示认证结果的对象。 |
| [AuthResultInfo](arkts-userauthentication-userauth-authresultinfo-i.md) | 表示认证结果信息，用于描述认证结果。 |
| [AuthTipInfo](arkts-userauthentication-userauth-authtipinfo-i.md) | 用户认证中间状态。该接口用于描述认证过程中产生的各种中间状态信息，包括状态对应的认证类型和具体的状态码。应用可通过[AuthTipCallback](arkts-userauthentication-userauth-authtipcallback-t.md)获取这些中间状态，以便在认证过程中提供更精细的用户反馈和状态感知。 |
| [Authenticator](arkts-userauthentication-userauth-authenticator-i.md) | 认证器对象。 |
| [EnrolledState](arkts-userauthentication-userauth-enrolledstate-i.md) | 用户注册凭据的状态。该接口用于描述用户已注册的认证凭据（如人脸、指纹、伴随设备）的当前状态，包括凭据摘要和数量。应用可通过[getEnrolledState](arkts-userauthentication-userauth-getenrolledstate-f.md#getenrolledstate)接口查询凭据状态，用于检测用户凭据是否发生变化（如新增或删除指纹/人脸/伴随设备），以便做出相应的业务处理。 |
| [IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md) | 返回认证结果的回调对象。该接口定义了认证结果的回调方法，用于在认证完成后获取认证结果。应用通过实现onResult方法，可以在认证通过时获取认证令牌，在认证不通过时获取错误码和相关信息。 |
| [IUserAuthCallback](arkts-userauthentication-userauth-iuserauthcallback-i.md) | 返回认证结果的回调对象。 |
| [ReuseUnlockResult](arkts-userauthentication-userauth-reuseunlockresult-i.md) | 复用解锁认证结果。该接口用于配置认证结果复用的相关参数，包括复用模式和有效时长。通过合理配置认证结果复用，可以在保证安全性的前提下提升用户体验，避免用户频繁重复认证。 |
| [TipInfo](arkts-userauthentication-userauth-tipinfo-i.md) | 表示认证过程中的提示信息，用于提供认证过程的反馈。 |
| [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md) | 用于执行用户身份认证，并支持使用统一用户身份认证控件。该接口提供了完整的用户认证能力，包括订阅认证结果、订阅认证中间状态、启动认证和取消认证等操作。通过统一认证控件，可以为用户提供标准化的认证界面和一致的认证体验。  使用以下接口前，需先通过[getUserAuthInstance](arkts-userauthentication-userauth-getuserauthinstance-f.md#getuserauthinstance)方法获取UserAuthInstance对象。 |
| [UserAuthResult](arkts-userauthentication-userauth-userauthresult-i.md) | 用户认证结果。认证通过时，返回认证类型和认证通过的令牌信息；认证不通过时，返回相应的错误码。该接口用于描述认证完成后的结果信息，应用可通过[IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md)的onResult回调获取此结果。 |
| [WidgetParam](arkts-userauthentication-userauth-widgetparam-i.md) | 用户认证界面配置相关参数。该接口用于配置认证界面的显示样式和交互方式，包括标题、导航按钮文本、窗口模式等。通过合理配置这些参数，可以为用户提供清晰的认证引导和良好的交互体验。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthParam](arkts-userauthentication-userauth-authparam-i-sys.md) | 用户认证相关参数。该接口用于配置用户认证的各项参数，包括挑战值、认证类型列表、认证信任等级、认证结果复用配置等。通过合理配置这些参数，可以满足不同业务场景下的认证需求。 |
| [IAuthWidgetCallback](arkts-userauthentication-userauth-iauthwidgetcallback-i-sys.md) | 身份认证组件回调接口。认证组件通过该回调接口获取用户认证框架发送的命令，并根据命令内容执行相应的认证操作。 |
| [IRemoteAuthCallback](arkts-userauthentication-userauth-iremoteauthcallback-i-sys.md) | 提供远端认证场景下获取WigetParam的接口。 |
| [UserAuthWidgetMgr](arkts-userauthentication-userauth-userauthwidgetmgr-i-sys.md) | 身份认证组件管理器。用于将自定义身份认证控件注册到UserAuthWidgetMgr中，由UserAuthWidgetMgr进行统一管理和调度。通过该接口，自定义身份认证控件可以接收来自用户认证框架的命令并执行相应操作。 |
| [WidgetParam](arkts-userauthentication-userauth-widgetparam-i-sys.md) | 用户认证界面配置相关参数。该接口用于配置认证界面的显示样式和交互方式，包括标题、导航按钮文本、窗口模式等。通过合理配置这些参数，可以为用户提供清晰的认证引导和良好的交互体验。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md) | 表示认证结果的信任等级枚举。该枚举定义了四个认证可信等级，用于描述认证结果的安全强度。认证可信等级越高，表示认证方案的活体检测能力越强、用户身份识别越精确，适用于更高安全要求的业务场景。应用应根据业务场景的安全需求选择合适的认证可信等级。  典型场景及举例可参考[生物认证可信等级划分原则](../../../security/UserAuthenticationKit/user-authentication-overview.md#生物认证可信等级划分原则)。 |
| [AuthenticationResult](arkts-userauthentication-userauth-authenticationresult-e.md) | 表示认证结果的枚举。 |
| [FaceTips](arkts-userauthentication-userauth-facetips-e.md) | 表示人脸认证过程中提示码的枚举。 |
| [FingerprintTips](arkts-userauthentication-userauth-fingerprinttips-e.md) | 表示指纹认证过程中提示码的枚举。 |
| [ResultCode](arkts-userauthentication-userauth-resultcode-e.md) | 表示返回码的枚举。 |
| [ReuseMode](arkts-userauthentication-userauth-reusemode-e.md) | 复用解锁认证结果的模式。该枚举定义了认证结果复用的四种模式，用于控制何种认证结果可以在何种条件下被复用。应用可根据业务场景选择合适的复用模式，以在安全性和用户体验之间取得平衡。 |
| [UserAuthResultCode](arkts-userauthentication-userauth-userauthresultcode-e.md) | 表示返回码的枚举。该枚举定义了用户认证操作可能返回的所有结果码，包括成功码和各类错误码。应用可根据返回码判断认证结果，并采取相应的处理措施。 |
| [UserAuthTipCode](arkts-userauthentication-userauth-userauthtipcode-e.md) | 表示身份认证中间状态的枚举。该枚举用于描述认证过程中的各种中间状态，包括认证不通过、超时、冻结状态以及认证界面的加载和释放等。应用可通过[on('authTip')](userAuth.UserAuthInstance.on(type: 'authTip', callback: AuthTipCallback))接口订阅这些中间状态，以便在认证过程中提供更精细的用户反馈和状态感知。 |
| [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | 表示身份认证的凭据类型枚举。该枚举定义了系统支持的认证类型，包括锁屏密码认证（PIN）、生物特征认证（人脸、指纹）等。应用在发起认证时需指定认证类型列表，用户可选择其中任意一种完成认证。不同认证类型具有不同的安全强度和用户体验特点，应用应根据业务场景选择合适的认证类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [NoticeType](arkts-userauthentication-userauth-noticetype-e-sys.md) | 用户身份认证的通知类型枚举。该枚举定义了系统支持的通知类型，用于标识通知的来源。 |
| [UserAuthResultCode](arkts-userauthentication-userauth-userauthresultcode-e-sys.md) | 表示返回码的枚举。该枚举定义了用户认证操作可能返回的所有结果码，包括成功码和各类错误码。应用可根据返回码判断认证结果，并采取相应的处理措施。 |
| [UserAuthType](arkts-userauthentication-userauth-userauthtype-e-sys.md) | 表示身份认证的凭据类型枚举。该枚举定义了系统支持的认证类型，包括锁屏密码认证（PIN）、生物特征认证（人脸、指纹）等。应用在发起认证时需指定认证类型列表，用户可选择其中任意一种完成认证。不同认证类型具有不同的安全强度和用户体验特点，应用应根据业务场景选择合适的认证类型。 |
| [WindowModeType](arkts-userauthentication-userauth-windowmodetype-e-sys.md) | 用户认证界面的显示类型枚举。该枚举定义了认证界面可使用的显示模式，用于控制系统身份认证组件的窗口样式 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md) | 表示认证事件类型的关键字，作为[on](arkts-userauthentication-userauth-authinstance-i.md#on)接口的参数。  该类型为下表类型取值中的联合类型。 |
| [AuthTipCallback](arkts-userauthentication-userauth-authtipcallback-t.md) | 回调函数，返回认证中间状态。该回调用于在认证过程中获取各种中间状态信息，包括每次认证不通过、冻结状态、界面加载和释放等。通过订阅这些中间状态，应用可以在认证过程中提供更精细的用户交互和状态管理。 |
| [AuthType](arkts-userauthentication-userauth-authtype-t.md) | 表示认证类型。 |
| [EventInfo](arkts-userauthentication-userauth-eventinfo-t.md) | 表示认证过程中事件信息的类型。  该类型为下表类型取值中的联合类型。 |
| [SecureLevel](arkts-userauthentication-userauth-securelevel-t.md) | 表示认证的安全级别。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ResultCallback](arkts-userauthentication-userauth-resultcallback-t-sys.md) | 调用返回认证结果。如果鉴权成功。UserAuthResult中包含token信息。 |
| [WidgetParamCallback](arkts-userauthentication-userauth-widgetparamcallback-t-sys.md) | 调用以获取远程身份验证的用户身份验证页面上显示的信息。 |
<!--DelEnd-->

### 常量

| 名称 | 说明 |
| --- | --- |
| [MAX_ALLOWABLE_REUSE_DURATION](arkts-userauthentication-userauth-con.md#max_allowable_reuse_duration) | 复用解锁认证结果最大有效时长，值为300000毫秒（5分钟）。用于限制认证结果复用的最大时长，防止长时间复用过期的认证结果带来的安全风险。该常量可作为[ReuseUnlockResult](arkts-userauthentication-userauth-reuseunlockresult-i.md)中reuseDuration参数的最大值。 |
| [PERMANENT_LOCKOUT_DURATION](arkts-userauthentication-userauth-con.md#permanent_lockout_duration) | 永久冻结时间，值为0x7fffffff毫秒。当认证不通过次数达到上限后，认证器将进入永久冻结状态，此时需要通过PIN认证才能解锁。该值用于标识认证器的永久冻结状态，可通过[AuthLockState](arkts-userauthentication-userauth-authlockstate-i.md)的lockoutDuration字段返回。 |

