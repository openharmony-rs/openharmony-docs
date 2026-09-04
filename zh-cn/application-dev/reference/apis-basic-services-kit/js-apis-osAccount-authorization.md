# @ohos.account.osAccount.authorization (系统账号授权管理)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->

本模块提供操作系统本地账号授权管理能力。您可以使用该命名空间中的API请求对指定的[Privilege](#privilege)进行授权，这些特权是基于授权策略和用户同意来进行授予的。

**起始版本：** 26.1.0

## 导入模块

```ts
import { authorization } from '@kit.BasicServicesKit';
```

## authorization.getAuthorizationManager

getAuthorizationManager(): AuthorizationManager

获取[AuthorizationManager](#authorizationmanager)实例。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                                            | 说明               |
| ----------------------------------------------- | ------------------ |
| [AuthorizationManager](#authorizationmanager) | 授权管理器实例。 |

**示例：**

```ts
import { authorization } from '@kit.BasicServicesKit';

let authorizationManager: authorization.AuthorizationManager = authorization.getAuthorizationManager();
```

## AuthorizationManager

定义授权管理器，用于请求和检查授权。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

### requestAuthorization

requestAuthorization(privilege: Privilege, context: UIAbilityContext): Promise&lt;AuthorizationResult&gt;

请求将指定的特权授予当前进程。使用Promise异步回调。

当应用处于前台且不存在有效授权时，将以模应用弹窗方式显示授权弹窗。若已存在有效授权，则会直接复用。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.REQUEST_LOCAL_ACCOUNT_AUTHORIZATION

**参数：**

| 参数名    | 类型                                                | 必填 | 说明                                                             |
| --------- | --------------------------------------------------- | ---- | ---------------------------------------------------------------- |
| privilege | [Privilege](#privilege)                             | 是   | 目标特权。      |
| context   | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 是   | 承载授权弹窗的UIAbility上下文。 |

**返回值：**

| 类型                                                  | 说明                         |
| ----------------------------------------------------- | ---------------------------- |
| Promise&lt;[AuthorizationResult](#authorizationresult)&gt; | Promise对象，返回授权结果。 |

**错误码：**

以下错误码的详细介绍请参见[账号管理错误码](errorcode-account.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 12300001 | The system service works abnormally.                         |
| 12300302 | User interaction is required but not allowed.<br>Possible causes: 1. The specified UI context is invalid; 2. The application is not in the foreground.<br>Suggested solutions: Ensure the application is in the foreground and pass a valid UIAbilityContext.                |
| 12300304 | Authorization service is busy. <br>Possible cause: Another authorization is being processed.                               |

**示例：**

```ts
import { authorization, BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 获取UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

try {
  authorization.getAuthorizationManager().requestAuthorization(
    authorization.Privilege.PRIVILEGE_OPERATE_RAW_NET_PACKETS, context
  ).then((result: authorization.AuthorizationResult) => {
    console.info('requestAuthorization successfully, resultCode: ' + result.resultCode);
  }).catch((err: BusinessError) => {
    console.error(`requestAuthorization failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`requestAuthorization exception: code is ${err.code}, message is ${err.message}`);
}
```

### hasAuthorization

hasAuthorization(privilege: Privilege): Promise&lt;boolean&gt;

检查当前进程是否拥有指定特权的授权。使用Promise异步回调。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                   |
| --------- | ----------------------- | ---- | ------------------------------------------------------ |
| privilege | [Privilege](#privilege) | 是   | 目标特权。|

**返回值：**

| 类型                   | 说明                                                               |
| --------------------- | ------------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前进程拥有指定特权的授权；返回false表示相反。 |

**错误码：**

以下错误码的详细介绍请参见[账号管理错误码](errorcode-account.md)。

| 错误码ID | 错误信息                             |
| -------- | ------------------------------------ |
| 12300001 | The system service works abnormally. |

**示例：**

```ts
import { authorization, BusinessError } from '@kit.BasicServicesKit';

try {
  authorization.getAuthorizationManager().hasAuthorization(
    authorization.Privilege.PRIVILEGE_OPERATE_RAW_NET_PACKETS
  ).then((isAuthorized: boolean) => {
    console.info('hasAuthorization successfully, isAuthorized: ' + isAuthorized);
  }).catch((err: BusinessError) => {
    console.error(`hasAuthorization failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`hasAuthorization exception: code is ${err.code}, message is ${err.message}`);
}
```

## Privilege

枚举所有可授权的特权。

在请求对这些特权授权前，确保当前应用和运行环境满足授权策略要求。有关每个特权的详细定义（包括授权策略），请参见[系统账号特权列表](appendix-osAccount-authorization-privileges.md)。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称                             | 值                                            | 说明                 |
| -------------------------------- | --------------------------------------------- | -------------------- |
| PRIVILEGE_OPERATE_RAW_NET_PACKETS | 'ohos.privilege.operate_raw_net_packets' | 操作原始网络包的特权。 |

## AuthorizationResultCode

枚举授权结果码。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称                       | 值       | 说明                                                                                                                              |
| -------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| AUTHORIZATION_GRANTED      | 0        | 授权成功。                                                                                                                        |
| AUTHORIZATION_CANCELED     | 12300301 | 授权已被用户取消。<br>可能原因：用户选择关闭授权控件，或者用户在授权控件窗口中点击“取消”按钮。                        |
| AUTHORIZATION_DENIED       | 12300303 | 授权被系统策略拒绝。<br>可能原因：未满足该特权所对应的授权策略。例如：该特权要求调用方必须持有指定的应用权限，且必须在管理员类型的系统账号会话下运行。|
| AUTHORIZATION_NOT_SUPPORTED | 12300305 | 不支持该授权请求。<br>可能原因：所请求的目标特权在当前系统版本中完全未注册或缺失，其关联功能通常亦不受支持。                                        |

## AuthorizationResult

定义授权结果。目前，所有[Privilege](#privilege)的授权有效期均与调用进程的生命周期相绑定（随进程销毁而失效）。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称         | 类型                                              | 只读  | 可选 |说明                                                                                             |
| ------------ | ------------------------------------------------- | ----- | ---- | ----------------------------------------------------------------------------------------------- |
| resultCode   | [AuthorizationResultCode](#authorizationresultcode) |  否 | 否  | 授权结果码。如果授权获批，则返回AUTHORIZATION_GRANTED；否则返回相应的错误码。|
| privilege    | [Privilege](#privilege)                           |  否 | 否  | 该授权所对应的特权。 |
