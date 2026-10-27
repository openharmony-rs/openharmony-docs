# AuthClientInfo（系统接口）

```TypeScript
interface AuthClientInfo
```

客户端会话信息。

**起始版本：** 26.1.0

<!--Device-securityGuard-interface AuthClientInfo--><!--Device-securityGuard-interface AuthClientInfo-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthClientInfo-bundleName: string--><!--Device-AuthClientInfo-bundleName: string-End-->

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

<!--Device-AuthClientInfo-clientId: string--><!--Device-AuthClientInfo-clientId: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## defaultTimeoutMs

```TypeScript
defaultTimeoutMs: number
```

客户端响应超时时间。单位为：毫秒。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthClientInfo-defaultTimeoutMs: number--><!--Device-AuthClientInfo-defaultTimeoutMs: number-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## defaultTimeoutStrategy

```TypeScript
defaultTimeoutStrategy: AuthStrategy
```

超时默认阻断策略。

**类型：** [AuthStrategy](arkts-securityguard-securityguard-authstrategy-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthClientInfo-defaultTimeoutStrategy: AuthStrategy--><!--Device-AuthClientInfo-defaultTimeoutStrategy: AuthStrategy-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## subscribedEvents

```TypeScript
subscribedEvents: number[]
```

客户端订阅的事件类型ID列表。

**类型：** number[]

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthClientInfo-subscribedEvents: number[]--><!--Device-AuthClientInfo-subscribedEvents: number[]-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。
