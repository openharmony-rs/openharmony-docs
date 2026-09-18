# OsAccountInfo

Represents the OS account information.

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## isLoggedIn

```TypeScript
isLoggedIn?: boolean
```

Whether the OS account is logged in. The value **true** means that the OS account has logged in; the value **false** means the opposite.

This is a system API. The default value is **false**.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## shortName

```TypeScript
shortName?: string
```

Short name of the OS account.

This is a system API and is left blank by default.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
