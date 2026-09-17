# AcquireAuthorizationResult (System API)

Defines the result of the authorization.

**Since:** 24

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## isReused

```TypeScript
isReused?: boolean
```

Whether the authorization result is reused. The default value is **undefined**.

**true**: The authorization result is reused. **false**: The authorization result is not reused.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## privilege

```TypeScript
privilege: string
```

Privilege associated with the authorization.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## resultCode

```TypeScript
resultCode: AuthorizationResultCode
```

Authorization result code.

**Type:** [AuthorizationResultCode](arkts-basicservices-authorization-authorizationresultcode-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## token

```TypeScript
token?: Uint8Array
```

Authorization token. The default value is **undefined**.

**Type:** Uint8Array

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## validityPeriod

```TypeScript
validityPeriod?: number
```

Validity period of the authorization, in seconds. The default value is **300**.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
