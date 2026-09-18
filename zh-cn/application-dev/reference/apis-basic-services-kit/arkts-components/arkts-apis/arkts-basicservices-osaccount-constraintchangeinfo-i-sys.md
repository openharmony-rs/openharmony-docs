# ConstraintChangeInfo（系统接口）

表示约束变更信息。

**起始版本：** 23

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## constraint

```TypeScript
constraint: string
```

发生变更的[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## isEnabled

```TypeScript
isEnabled: boolean
```

发生变更的约束的使能状态。默认：false。

true表示目标约束已使能；false表示目标约束未使能。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。
