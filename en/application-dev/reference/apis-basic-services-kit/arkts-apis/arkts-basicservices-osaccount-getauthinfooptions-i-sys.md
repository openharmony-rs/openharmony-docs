# GetAuthInfoOptions (System API)

```TypeScript
interface GetAuthInfoOptions
```

Represents a set of optional parameters for [GetAuthInfo](arkts-basicservices-osaccount-useridentitymanager-c-sys.md#getauthinfo-3).

**Since:** 12

<!--Device-osAccount-interface GetAuthInfoOptions--><!--Device-osAccount-interface GetAuthInfoOptions-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## accountId

```TypeScript
accountId?: number
```

OS account ID, which is **undefined** by default.

**Type:** number

**Since:** 12

<!--Device-GetAuthInfoOptions-accountId?: int--><!--Device-GetAuthInfoOptions-accountId?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## authType

```TypeScript
authType?: AuthType
```

Authentication type, which is **undefined** by default.

**Type:** [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md)

**Since:** 12

<!--Device-GetAuthInfoOptions-authType?: AuthType--><!--Device-GetAuthInfoOptions-authType?: AuthType-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
