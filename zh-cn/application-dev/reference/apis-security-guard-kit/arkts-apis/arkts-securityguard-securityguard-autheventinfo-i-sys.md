# AuthEventInfo（系统接口）

```TypeScript
interface AuthEventInfo
```

阻断事件信息。

**起始版本：** 26.1.0

<!--Device-securityGuard-interface AuthEventInfo--><!--Device-securityGuard-interface AuthEventInfo-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## clientStatus

```TypeScript
clientStatus?: AuthClientStatus[]
```

客户端会话状态列表。

**类型：** [AuthClientStatus](arkts-securityguard-securityguard-authclientstatus-i-sys.md)[]

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthEventInfo-clientStatus?: AuthClientStatus[]--><!--Device-AuthEventInfo-clientStatus?: AuthClientStatus[]-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## content

```TypeScript
content: string
```

事件内容，JSON字符串格式。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthEventInfo-content: string--><!--Device-AuthEventInfo-content: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## eventId

```TypeScript
eventId: number
```

事件类型ID。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthEventInfo-eventId: number--><!--Device-AuthEventInfo-eventId: number-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: string
```

事件版本号。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthEventInfo-version: string--><!--Device-AuthEventInfo-version: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。
