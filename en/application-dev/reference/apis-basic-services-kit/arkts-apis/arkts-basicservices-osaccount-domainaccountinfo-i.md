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

## accountName

```TypeScript
accountName: string
```

Domain account name.

**Type:** string

**Since:** 8

<!--Device-DomainAccountInfo-accountName: string--><!--Device-DomainAccountInfo-accountName: string-End-->

**System capability:** SystemCapability.Account.OsAccount

## additionalInfo

```TypeScript
additionalInfo?: Record<string, Object>
```

Additional information about the domain account. By default, no value is passed in.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DomainAccountInfo-additionalInfo?: Record<string, Object>--><!--Device-DomainAccountInfo-additionalInfo?: Record<string, Object>-End-->

**System capability:** SystemCapability.Account.OsAccount

## domain

```TypeScript
domain: string
```

Domain name.

**Type:** string

**Since:** 8

<!--Device-DomainAccountInfo-domain: string--><!--Device-DomainAccountInfo-domain: string-End-->

**System capability:** SystemCapability.Account.OsAccount

## serverConfigId

```TypeScript
serverConfigId?: string
```

Domain account configuration ID, which is an empty string by default.

**Type:** string

**Since:** 18

<!--Device-DomainAccountInfo-serverConfigId?: string--><!--Device-DomainAccountInfo-serverConfigId?: string-End-->

**System capability:** SystemCapability.Account.OsAccount
