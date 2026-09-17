# GetDomainAccessTokenOptions (System API)

Defines the options for obtaining a domain access token.

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## businessParams

```TypeScript
businessParams: Record<string, Object>
```

Business parameters customized by the business party based on the request protocol.

**Type:** Record&lt;string, Object&gt;

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## callerUid

```TypeScript
callerUid: number
```

Caller UID.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## domainAccountInfo

```TypeScript
domainAccountInfo: DomainAccountInfo
```

Domain account information.

**Type:** [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md)

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## domainAccountToken

```TypeScript
domainAccountToken: Uint8Array
```

Token of the domain account.

**Type:** Uint8Array

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
