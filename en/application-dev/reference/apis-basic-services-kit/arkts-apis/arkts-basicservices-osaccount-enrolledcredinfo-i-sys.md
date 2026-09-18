# EnrolledCredInfo (System API)

Defines enrolled credential information.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## authSubType

```TypeScript
authSubType: AuthSubType
```

Authentication credential subtype.

**Type:** [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## authType

```TypeScript
authType: AuthType
```

Authentication credential type.

**Type:** [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## credentialId

```TypeScript
credentialId: Uint8Array
```

Credential ID.

**Type:** Uint8Array

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## isAbandoned

```TypeScript
isAbandoned?: boolean
```

Whether the credential is abandoned. The abandoned credential may be stored as a backup credential for a period of time. The value **true** indicates that the credential is abandoned, and the value **false** indicates the opposite. The default value is **undefined**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## templateId

```TypeScript
templateId: Uint8Array
```

Authentication credential template ID.

**Type:** Uint8Array

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## validityPeriod

```TypeScript
validityPeriod?: number
```

Credential validity period, in milliseconds. The default value is **undefined**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
