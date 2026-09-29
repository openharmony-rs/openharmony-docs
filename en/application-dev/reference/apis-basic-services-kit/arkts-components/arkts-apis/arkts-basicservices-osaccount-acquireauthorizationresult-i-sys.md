# AcquireAuthorizationResult (System API)

```TypeScript
interface AcquireAuthorizationResult
```

Defines the result of the authorization.

**Since:** 24

<!--Device-osAccount-interface AcquireAuthorizationResult--><!--Device-osAccount-interface AcquireAuthorizationResult-End-->

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

<!--Device-AcquireAuthorizationResult-isReused?: boolean--><!--Device-AcquireAuthorizationResult-isReused?: boolean-End-->

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

<!--Device-AcquireAuthorizationResult-privilege: string--><!--Device-AcquireAuthorizationResult-privilege: string-End-->

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

<!--Device-AcquireAuthorizationResult-resultCode: AuthorizationResultCode--><!--Device-AcquireAuthorizationResult-resultCode: AuthorizationResultCode-End-->

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

<!--Device-AcquireAuthorizationResult-token?: Uint8Array--><!--Device-AcquireAuthorizationResult-token?: Uint8Array-End-->

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

<!--Device-AcquireAuthorizationResult-validityPeriod?: int--><!--Device-AcquireAuthorizationResult-validityPeriod?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
