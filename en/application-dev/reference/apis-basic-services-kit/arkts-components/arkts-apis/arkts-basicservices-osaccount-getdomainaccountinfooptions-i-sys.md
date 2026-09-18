# GetDomainAccountInfoOptions (System API)

Defines the options for obtaining domain account information.

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

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

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## domain

```TypeScript
domain?: string
```

Domain name, which is **undefined** by default.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## serverConfigId

```TypeScript
serverConfigId?: string
```

Configuration ID of the server to which the domain account belongs, which is **undefined** by default.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
