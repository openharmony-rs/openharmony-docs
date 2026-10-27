# TicketQueryResult

```TypeScript
interface TicketQueryResult
```

票据查询结果。

**起始版本：** 26.1.0

<!--Device-abilityToolAccessCtrl-interface TicketQueryResult--><!--Device-abilityToolAccessCtrl-interface TicketQueryResult-End-->

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## permissionResults

```TypeScript
permissionResults: PermissionInfo[]
```

权限结果列表。

**类型：** [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i.md)[]

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-TicketQueryResult-permissionResults: PermissionInfo[]--><!--Device-TicketQueryResult-permissionResults: PermissionInfo[]-End-->

**系统能力：** SystemCapability.Security.Asset

## ticket

```TypeScript
ticket: string
```

票证信息。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-TicketQueryResult-ticket: string--><!--Device-TicketQueryResult-ticket: string-End-->

**系统能力：** SystemCapability.Security.Asset
