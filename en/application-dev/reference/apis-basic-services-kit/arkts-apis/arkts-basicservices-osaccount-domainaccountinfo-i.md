# DomainAccountInfo

Represents domain account information.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## accountName

```TypeScript
accountName: string
```

Domain account name.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## additionalInfo

```TypeScript
additionalInfo?: Record<string, Object>
```

Additional information about the domain account. By default, no value is passed in.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

## domain

```TypeScript
domain: string
```

Domain name.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

## serverConfigId

```TypeScript
serverConfigId?: string
```

Domain account configuration ID, which is an empty string by default.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Account.OsAccount
