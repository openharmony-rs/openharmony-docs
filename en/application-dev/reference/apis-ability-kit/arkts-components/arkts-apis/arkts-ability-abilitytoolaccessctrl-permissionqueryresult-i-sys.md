# PermissionQueryResult (System API)

```TypeScript
interface PermissionQueryResult
```

Permission query result.

**Since:** 26.0.0

<!--Device-abilityToolAccessCtrl-interface PermissionQueryResult--><!--Device-abilityToolAccessCtrl-interface PermissionQueryResult-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## Modules to Import

```TypeScript
```

## needDialog

```TypeScript
needDialog: boolean
```

Whether a dialog is required.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQueryResult-needDialog: boolean--><!--Device-PermissionQueryResult-needDialog: boolean-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## permissionResults

```TypeScript
permissionResults: PermissionInfo[]
```

Permission result list.

**Type:** [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i-sys.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQueryResult-permissionResults: PermissionInfo[]--><!--Device-PermissionQueryResult-permissionResults: PermissionInfo[]-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## ticket

```TypeScript
ticket?: TicketInfo
```

Ticket information.

**Type:** [TicketInfo](arkts-ability-abilitytoolaccessctrl-ticketinfo-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQueryResult-ticket?: TicketInfo--><!--Device-PermissionQueryResult-ticket?: TicketInfo-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.
