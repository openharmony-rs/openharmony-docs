# RemoteAuthOptions (System API)

```TypeScript
interface RemoteAuthOptions
```

Represents a set of optional parameters for remote authentication.

**Since:** 12

<!--Device-osAccount-interface RemoteAuthOptions--><!--Device-osAccount-interface RemoteAuthOptions-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## collectorNetworkId

```TypeScript
collectorNetworkId?: string
```

Network ID of the credential collector, which is left blank by default.

**Type:** string

**Since:** 12

<!--Device-RemoteAuthOptions-collectorNetworkId?: string--><!--Device-RemoteAuthOptions-collectorNetworkId?: string-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## collectorTokenId

```TypeScript
collectorTokenId?: number
```

Token ID of the credential collector, which is **undefined** by default.

**Type:** number

**Since:** 12

<!--Device-RemoteAuthOptions-collectorTokenId?: int--><!--Device-RemoteAuthOptions-collectorTokenId?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## verifierNetworkId

```TypeScript
verifierNetworkId?: string
```

Network ID of the credential verifier, which is left blank by default.

**Type:** string

**Since:** 12

<!--Device-RemoteAuthOptions-verifierNetworkId?: string--><!--Device-RemoteAuthOptions-verifierNetworkId?: string-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
