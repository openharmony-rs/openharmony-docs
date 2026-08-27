# SecurityEvent（系统接口）

提供SecurityEvent类型，包括事件ID、版本信息和上报内容。

**起始版本：** 12

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

安全事件内容，json格式。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## eventId

```TypeScript
eventId: number
```

安全事件类型。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp?: string
```

事件时间戳，格式为YYYYMMDDHHMMSS。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: string
```

安全事件版本号。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。
