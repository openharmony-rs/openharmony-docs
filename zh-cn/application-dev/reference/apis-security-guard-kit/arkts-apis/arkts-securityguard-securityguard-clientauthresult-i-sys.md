# ClientAuthResult（系统接口）

```TypeScript
interface ClientAuthResult
```

单个客户端阻断结果。

**起始版本：** 26.1.0

<!--Device-securityGuard-interface ClientAuthResult--><!--Device-securityGuard-interface ClientAuthResult-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## authStrategy

```TypeScript
authStrategy: AuthStrategy
```

阻断策略。

**类型：** [AuthStrategy](arkts-securityguard-securityguard-authstrategy-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClientAuthResult-authStrategy: AuthStrategy--><!--Device-ClientAuthResult-authStrategy: AuthStrategy-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## clientId

```TypeScript
clientId: string
```

客户端会话唯一标识。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ClientAuthResult-clientId: string--><!--Device-ClientAuthResult-clientId: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。
