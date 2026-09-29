# SecurityEventRule（系统接口）

```TypeScript
interface SecurityEventRule
```

用户获取安全数据的规则。

@interface SecurityEventRule

**起始版本：** 12

<!--Device-securityGuard-interface SecurityEventRule--><!--Device-securityGuard-interface SecurityEventRule-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## beginTime

```TypeScript
beginTime?: string
```

需要获取数据的起始时间，格式为YYYYMMDDHHMMSS。

**类型：** string

**起始版本：** 12

<!--Device-SecurityEventRule-beginTime?: string--><!--Device-SecurityEventRule-beginTime?: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## endTime

```TypeScript
endTime?: string
```

需要获取数据的终止时间，格式为YYYYMMDDHHMMSS。

**类型：** string

**起始版本：** 12

<!--Device-SecurityEventRule-endTime?: string--><!--Device-SecurityEventRule-endTime?: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## eventId

```TypeScript
eventId: number
```

需要获取的安全事件ID。

**类型：** number

**起始版本：** 12

<!--Device-SecurityEventRule-eventId: number--><!--Device-SecurityEventRule-eventId: number-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

## param

```TypeScript
param?: string
```

额外查询参数。

**类型：** string

**起始版本：** 12

<!--Device-SecurityEventRule-param?: string--><!--Device-SecurityEventRule-param?: string-End-->

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。
