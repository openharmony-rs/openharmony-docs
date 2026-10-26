# AuthClientStatus（系统接口）

```TypeScript
interface AuthClientStatus
```

客户端会话状态。

**起始版本：** 26.1.0

<!--Device-securityGuard-interface AuthClientStatus--><!--Device-securityGuard-interface AuthClientStatus-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## clientId

```TypeScript
clientId: string
```

客户端会话唯一标识。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthClientStatus-clientId: string--><!--Device-AuthClientStatus-clientId: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## isDegraded

```TypeScript
isDegraded: boolean
```

事件是否降级，降级的事件仅上报通知，不需要接收阻断结果。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthClientStatus-isDegraded: boolean--><!--Device-AuthClientStatus-isDegraded: boolean-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。
