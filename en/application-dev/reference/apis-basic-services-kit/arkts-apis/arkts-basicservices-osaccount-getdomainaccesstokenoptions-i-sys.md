# GetDomainAccessTokenOptions (System API)

```TypeScript
interface GetDomainAccessTokenOptions
```

Defines the options for obtaining a domain access token.

**Since:** 10

<!--Device-osAccount-interface GetDomainAccessTokenOptions--><!--Device-osAccount-interface GetDomainAccessTokenOptions-End-->

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

<!--Device-GetDomainAccessTokenOptions-businessParams: Record<string, Object>--><!--Device-GetDomainAccessTokenOptions-businessParams: Record<string, Object>-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## callerUid

```TypeScript
callerUid: number
```

Caller UID.

**Type:** number

**Since:** 10

<!--Device-GetDomainAccessTokenOptions-callerUid: int--><!--Device-GetDomainAccessTokenOptions-callerUid: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## domainAccountInfo

```TypeScript
domainAccountInfo: DomainAccountInfo
```

Domain account information.

**Type:** [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md)

**Since:** 10

<!--Device-GetDomainAccessTokenOptions-domainAccountInfo: DomainAccountInfo--><!--Device-GetDomainAccessTokenOptions-domainAccountInfo: DomainAccountInfo-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## domainAccountToken

```TypeScript
domainAccountToken: Uint8Array
```

Token of the domain account.

**Type:** Uint8Array

**Since:** 10

<!--Device-GetDomainAccessTokenOptions-domainAccountToken: Uint8Array--><!--Device-GetDomainAccessTokenOptions-domainAccountToken: Uint8Array-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
