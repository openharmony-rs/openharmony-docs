# OsAccountSubProfileEventData（系统接口）

系统账号子身份资料事件数据。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## event

```TypeScript
event: OsAccountSubProfileEvent
```

表示发生的事件。

**类型：** [OsAccountSubProfileEvent](arkts-basicservices-osaccount-osaccountsubprofileevent-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## osAccountLocalId

```TypeScript
osAccountLocalId: number
```

表示系统账号本地ID。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## previousSubProfileId

```TypeScript
previousSubProfileId?: number
```

表示上一个系统账号子身份资料标识符。仅在SWITCHING和SWITCHED事件中有效。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## subProfileId

```TypeScript
subProfileId: number
```

系统账号子身份资料的标识符。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。
