# GetPropertyRequest (System API)

```TypeScript
interface GetPropertyRequest
```

Defines the request for obtaining property information.

**Since:** 8

<!--Device-osAccount-interface GetPropertyRequest--><!--Device-osAccount-interface GetPropertyRequest-End-->

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

<!--Device-GetPropertyRequest-accountId?: int--><!--Device-GetPropertyRequest-accountId?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## authType

```TypeScript
authType: AuthType
```

Authentication credential type.

**Type:** [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md)

**Since:** 8

<!--Device-GetPropertyRequest-authType: AuthType--><!--Device-GetPropertyRequest-authType: AuthType-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## keys

```TypeScript
keys: Array<GetPropertyType>
```

An array of the types of the properties to obtain.

**Type:** Array&lt;[GetPropertyType](arkts-basicservices-osaccount-getpropertytype-e-sys.md)&gt;

**Since:** 8

<!--Device-GetPropertyRequest-keys: Array<GetPropertyType>--><!--Device-GetPropertyRequest-keys: Array<GetPropertyType>-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
