# GatheringPolicyType（系统接口）

DLP沙箱聚合策略类型的枚举。沙箱聚合表示同一权限类型的DLP文件，在同一个沙箱内打开，例如在同一个沙箱内使用不同tab页打开；沙箱非聚合表示不同DLP文件在不同沙箱打开。

**起始版本：** 10

<!--Device-dlpPermission-export enum GatheringPolicyType--><!--Device-dlpPermission-export enum GatheringPolicyType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## GATHERING

```TypeScript
GATHERING = 1
```

表示沙箱聚合。

**起始版本：** 10

<!--Device-GatheringPolicyType-GATHERING = 1--><!--Device-GatheringPolicyType-GATHERING = 1-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## NON_GATHERING

```TypeScript
NON_GATHERING = 2
```

表示沙箱非聚合。

**起始版本：** 10

<!--Device-GatheringPolicyType-NON_GATHERING = 2--><!--Device-GatheringPolicyType-NON_GATHERING = 2-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

