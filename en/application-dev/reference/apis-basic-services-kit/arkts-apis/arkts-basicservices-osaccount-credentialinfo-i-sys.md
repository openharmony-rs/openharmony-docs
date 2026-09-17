# CredentialInfo (System API)

Defines the credential information.

**Since:** 8

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

Additional information about the credential, which is an empty string by default.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## credSubType

```TypeScript
credSubType: AuthSubType
```

Authentication credential subtype.

**Type:** [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## credType

```TypeScript
credType: AuthType
```

Authentication credential type.

**Type:** [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## token

```TypeScript
token: Uint8Array
```

Authentication token.

**Type:** Uint8Array

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
