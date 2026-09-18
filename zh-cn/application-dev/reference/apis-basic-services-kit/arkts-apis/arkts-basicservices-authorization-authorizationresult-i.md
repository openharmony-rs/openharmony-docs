# AuthorizationResult

定义授权结果。目前，所有[特权](arkts-basicservices-authorization-privilege-e.md) 的授权有效期均与调用进程的生命周期相绑定（随进程销毁而失效）。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { authorization } from '@kit.BasicServicesKit';
```

## privilege

```TypeScript
privilege: Privilege
```

该授权所对应的特权。

**类型：** [Privilege](arkts-basicservices-authorization-privilege-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

## resultCode

```TypeScript
resultCode: AuthorizationResultCode
```

授权结果码。如果授权获批，则返回 [AUTHORIZATION_GRANTED](arkts-basicservices-authorization-authorizationresultcode-e.md#authorization_granted)。否则，返回相应的错误码。详情请参见 [AuthorizationResultCode](arkts-basicservices-authorization-authorizationresultcode-e.md)。

**类型：** [AuthorizationResultCode](arkts-basicservices-authorization-authorizationresultcode-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount
