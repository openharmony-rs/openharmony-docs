# AuthorizationManager

定义授权管理器，用于请求和检查授权。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { authorization } from '@kit.BasicServicesKit';
```

## hasAuthorization

```TypeScript
hasAuthorization(privilege: Privilege): Promise<boolean>
```

检查当前进程是否拥有指定特权的授权。该接口使用Promise返回结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| privilege | [Privilege](arkts-basicservices-authorization-privilege-e.md) | 是 | 目标特权。可用值请参阅[Privilege](arkts-basicservices-authorization-privilege-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise用于返回结果。**true**表示表示当前进程具有指定特权的授权，**false**表示相反。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

## requestAuthorization

```TypeScript
requestAuthorization(privilege: Privilege, context: UIAbilityContext): Promise<AuthorizationResult>
```

请求将指定的特权授予当前进程。该接口使用promise返回结果。

当应用处于前台且不存在有效授权时，将以模应用方式显示授权弹窗。若已存在有效授权，则会直接复用。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.REQUEST_LOCAL_ACCOUNT_AUTHORIZATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| privilege | [Privilege](arkts-basicservices-authorization-privilege-e.md) | 是 | 目标特权。有关可用值，请参阅[Privilege](arkts-basicservices-authorization-privilege-e.md)。 |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | 是 | 承载授权对话框的[UIAbility context](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AuthorizationResult](arkts-basicservices-authorization-authorizationresult-i.md)&gt; | Promise用于返回授权结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300302](../errorcode-account.md#12300302-授权操作需要用户交互但当前交互操作受限) | User interaction is required but not allowed. Possible causes: 1. The specified UI context is invalid; 2. The application is not in the foreground. Suggested solutions: Ensure the application is in the foreground and pass a valid UIAbilityContext. |
| [12300304](../errorcode-account.md#12300304-授权服务忙) | Authorization service is busy. Possible cause: Another authorization is being processed. |
