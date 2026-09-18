# AuthOptions (System API)

Represents a set of optional parameters for [auth](arkts-basicservices-osaccount-userauth-c-sys.md#auth).

**Since:** 12

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

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## additionalInfo

```TypeScript
additionalInfo?: string
```

Additional information for identity authentication. The default value is **undefined**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## authIntent

```TypeScript
authIntent?: AuthIntent
```

Authentication intent, which is **undefined** by default.

**Type:** [AuthIntent](arkts-basicservices-osaccount-authintent-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## remoteAuthOptions

```TypeScript
remoteAuthOptions?: RemoteAuthOptions
```

Remote authentication options, which is **undefined** by default.

**Type:** [RemoteAuthOptions](arkts-basicservices-osaccount-remoteauthoptions-i-sys.md)

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
