# ConstraintChangeInfo（系统接口）

表示约束变更信息。

**起始版本：** 23

<!--Device-osAccount-interface ConstraintChangeInfo--><!--Device-osAccount-interface ConstraintChangeInfo-End-->

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

发生变更的[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)。

**类型：** string

**起始版本：** 23

<!--Device-ConstraintChangeInfo-constraint: string--><!--Device-ConstraintChangeInfo-constraint: string-End-->

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

<!--Device-ConstraintChangeInfo-isEnabled: boolean--><!--Device-ConstraintChangeInfo-isEnabled: boolean-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

