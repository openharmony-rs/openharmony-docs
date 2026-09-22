# @ohos.account.osAccount.authorization

提供操作系统本地账号授权管理能力。您可以使用该命名空间中的API请求对指定的Privilege进行授权，这些特权是基于授权策略和用户同意来进行授予的。

> **说明：** 
> 通过两个通道上报失败。抛出的[BusinessError](arkts-basicservices-base-businesserror-i.md)表示请求
> 根本不接受(例如，201表示调用方缺少API级别的权限
> ohos.permission.REQUEST_LOCAL_ACCOUNT_AUTHORATION;12300302表示需要用户交互，但不允许用户交互)。
> 解析结果中的[AuthorizationResultCode]{@链接授权.AuthorizationResultCode}表示请求被接受并报告
> 结果：
> {@链接授权.AuthorizationResultCode.AUTHORATION_CANCELED}表示用户取消了授权请求；
> Authorization_DENIED表示不满足授权策略；
> [Authorization_PRIVILEGE_NOT_SUPPORTED]{@链接授权.AuthorizationResultCode.AUTHORATION_PRIVILEGE_NOT_SUPPORTED}表示特权的配置未部署在当前系统版本中。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { authorization } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAuthorizationManager](arkts-basicservices-authorization-getauthorizationmanager-f.md) | 获取[AuthorizationManager](arkts-basicservices-authorization-authorizationmanager-i.md)实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AuthorizationManager](arkts-basicservices-authorization-authorizationmanager-i.md) | 定义授权管理器，用于请求和检查授权。 |
| [AuthorizationResult](arkts-basicservices-authorization-authorizationresult-i.md) | 定义授权结果。目前，所有[特权](arkts-basicservices-authorization-privilege-e.md) 的授权有效期均与调用进程的生命周期相绑定（随进程销毁而失效）。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AuthorizationResultCode](arkts-basicservices-authorization-authorizationresultcode-e.md) | 枚举授权结果码。 |
| [Privilege](arkts-basicservices-authorization-privilege-e.md) | 枚举所有可授权的特权。在请求对这些特权授权前，确保当前应用和运行环境满足授权策略要求。有关每个特权的详细定义（包括授权策略），请参见 [特权附录]（../../../reference/apis-basic-services-kit/appendix-osAccount-authorization-privileges.md）。 |
