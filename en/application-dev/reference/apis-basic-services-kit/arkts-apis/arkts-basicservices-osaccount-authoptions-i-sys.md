# AuthOptions (System API)

```TypeScript
interface AuthOptions
```

Represents a set of optional parameters for [auth](arkts-basicservices-osaccount-userauth-c-sys.md#auth2).

**Since:** 12

<!--Device-osAccount-interface AuthOptions--><!--Device-osAccount-interface AuthOptions-End-->

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

<!--Device-AuthOptions-accountId?: int--><!--Device-AuthOptions-accountId?: int-End-->

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

<!--Device-AuthOptions-additionalInfo?: string--><!--Device-AuthOptions-additionalInfo?: string-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## authIntent

```TypeScript
authIntent?: AuthIntent
```

Authentication intent, which is **undefined** by default.

**Type:** [AuthIntent](arkts-basicservices-osaccount-authintent-e-sys.md)

**Since:** 12

<!--Device-AuthOptions-authIntent?: AuthIntent--><!--Device-AuthOptions-authIntent?: AuthIntent-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## remoteAuthOptions

```TypeScript
remoteAuthOptions?: RemoteAuthOptions
```

Remote authentication options, which is **undefined** by default.

**Type:** [RemoteAuthOptions](arkts-basicservices-osaccount-remoteauthoptions-i-sys.md)

**Since:** 12

<!--Device-AuthOptions-remoteAuthOptions?: RemoteAuthOptions--><!--Device-AuthOptions-remoteAuthOptions?: RemoteAuthOptions-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
