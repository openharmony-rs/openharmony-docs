# DomainAccountInfo

```TypeScript
interface DomainAccountInfo
```

Represents domain account information.

**Since:** 8

<!--Device-osAccount-interface DomainAccountInfo--><!--Device-osAccount-interface DomainAccountInfo-End-->

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## accountId

```TypeScript
accountId?: string
```

Domain account ID.

This is a system API and is **undefined** by default.

**Type:** string

**Since:** 10

<!--Device-DomainAccountInfo-accountId?: string--><!--Device-DomainAccountInfo-accountId?: string-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## isAuthenticated

```TypeScript
isAuthenticated?: boolean
```

Whether the domain account has been authenticated. The value **true** means that the specified domain account has been authenticated; the value **false** means the opposite.

This is a system API. The default value is **false**.

**Type:** boolean

**Since:** 11

<!--Device-DomainAccountInfo-isAuthenticated?: boolean--><!--Device-DomainAccountInfo-isAuthenticated?: boolean-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
