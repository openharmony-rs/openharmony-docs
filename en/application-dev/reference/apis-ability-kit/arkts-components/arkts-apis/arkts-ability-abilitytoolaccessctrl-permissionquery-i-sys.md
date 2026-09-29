# PermissionQuery (System API)

```TypeScript
interface PermissionQuery
```

Permission query information.

**Since:** 26.0.0

<!--Device-abilityToolAccessCtrl-interface PermissionQuery--><!--Device-abilityToolAccessCtrl-interface PermissionQuery-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## Modules to Import

```TypeScript
```

## callerTokenId

```TypeScript
callerTokenId?: number
```

Caller token ID. Value range: (-∞,+∞).

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQuery-callerTokenId?: long--><!--Device-PermissionQuery-callerTokenId?: long-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## domainId

```TypeScript
domainId?: string
```

Domain ID.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQuery-domainId?: string--><!--Device-PermissionQuery-domainId?: string-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## needTicket

```TypeScript
needTicket?: boolean
```

Whether a ticket is required.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQuery-needTicket?: boolean--><!--Device-PermissionQuery-needTicket?: boolean-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## operationInfo

```TypeScript
operationInfo: OperationInfo[]
```

Operation information list.

**Type:** [OperationInfo](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQuery-operationInfo: OperationInfo[]--><!--Device-PermissionQuery-operationInfo: OperationInfo[]-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## remoteInfo

```TypeScript
remoteInfo?: RemoteInfo
```

Remote device information.

**Type:** [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQuery-remoteInfo?: RemoteInfo--><!--Device-PermissionQuery-remoteInfo?: RemoteInfo-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## ticketExpireTimeMs

```TypeScript
ticketExpireTimeMs?: number
```

Ticket expiration time in milliseconds. Unit: milliseconds. The value must be greater than 0. Value constraint: Greater than 0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionQuery-ticketExpireTimeMs?: long--><!--Device-PermissionQuery-ticketExpireTimeMs?: long-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.
