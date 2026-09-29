# SetPropertyRequest (System API)

```TypeScript
interface SetPropertyRequest
```

Defines the request for setting property information.

**Since:** 8

<!--Device-osAccount-interface SetPropertyRequest--><!--Device-osAccount-interface SetPropertyRequest-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## authType

```TypeScript
authType: AuthType
```

Authentication credential type.

**Type:** [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md)

**Since:** 8

<!--Device-SetPropertyRequest-authType: AuthType--><!--Device-SetPropertyRequest-authType: AuthType-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## key

```TypeScript
key: SetPropertyType
```

Type of the property to set.

**Type:** [SetPropertyType](arkts-basicservices-osaccount-setpropertytype-e-sys.md)

**Since:** 8

<!--Device-SetPropertyRequest-key: SetPropertyType--><!--Device-SetPropertyRequest-key: SetPropertyType-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## setInfo

```TypeScript
setInfo: Uint8Array
```

Information to set.

**Type:** Uint8Array

**Since:** 8

<!--Device-SetPropertyRequest-setInfo: Uint8Array--><!--Device-SetPropertyRequest-setInfo: Uint8Array-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
