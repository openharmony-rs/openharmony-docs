# SecurityEvent（系统接口）

```TypeScript
interface SecurityEvent
```

Provides the SecurityEvent type, including the event id, version info, report content.

**起始版本：** 12

<!--Device-securityGuard-interface SecurityEvent--><!--Device-securityGuard-interface SecurityEvent-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## content

```TypeScript
content: string
```

The report content

**类型：** string

**起始版本：** 12

<!--Device-SecurityEvent-content: string--><!--Device-SecurityEvent-content: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## eventId

```TypeScript
eventId: number
```

The event id

**类型：** number

**起始版本：** 12

<!--Device-SecurityEvent-eventId: number--><!--Device-SecurityEvent-eventId: number-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp?: string
```

The event timestamp, format is YYYYMMDDHHMMSS.

**类型：** string

**起始版本：** 12

<!--Device-SecurityEvent-timestamp?: string--><!--Device-SecurityEvent-timestamp?: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: string
```

The version of a security event. Different versions indicate different data formats.

**类型：** string

**起始版本：** 12

<!--Device-SecurityEvent-version: string--><!--Device-SecurityEvent-version: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。
