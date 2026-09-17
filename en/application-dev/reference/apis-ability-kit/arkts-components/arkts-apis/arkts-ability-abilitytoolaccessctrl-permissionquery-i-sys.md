# PermissionQuery (System API)

Permission query information.

**Since:** 26.0.0

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

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## domainId

```TypeScript
domainId?: string
```

Domain ID.

**Type:** string

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## needTicket

```TypeScript
needTicket?: boolean
```

Whether a ticket is required.

**Type:** boolean

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## operationInfo

```TypeScript
operationInfo: OperationInfo[]
```

Operation information list.

**Type:** [OperationInfo](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md)[]

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## remoteInfo

```TypeScript
remoteInfo?: RemoteInfo
```

Remote device information.

**Type:** [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md)

**Since:** 26.1.0

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## ticketExpireTimeMs

```TypeScript
ticketExpireTimeMs?: number
```

Ticket expiration time in milliseconds. Unit: milliseconds. The value must be greater than 0. Value constraint: Greater than 0.

**Type:** number

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.
