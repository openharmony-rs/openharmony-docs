# AuthResult（系统接口）

```TypeScript
interface AuthResult
```

所有客户端阻断结果。

**起始版本：** 26.1.0

<!--Device-securityGuard-interface AuthResult--><!--Device-securityGuard-interface AuthResult-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## clientAuthResult

```TypeScript
clientAuthResult: ClientAuthResult[]
```

客户端阻断结果列表。

**类型：** [ClientAuthResult](arkts-securityguard-securityguard-clientauthresult-i-sys.md)[]

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthResult-clientAuthResult: ClientAuthResult[]--><!--Device-AuthResult-clientAuthResult: ClientAuthResult[]-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## mergedAuthStrategy

```TypeScript
mergedAuthStrategy: AuthStrategy
```

所有客户端汇聚后的阻断策略。

**类型：** [AuthStrategy](arkts-securityguard-securityguard-authstrategy-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthResult-mergedAuthStrategy: AuthStrategy--><!--Device-AuthResult-mergedAuthStrategy: AuthStrategy-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。
