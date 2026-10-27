# TaskIdentityInfo (System API)

```TypeScript
interface TaskIdentityInfo
```

Task identity input info used to generate TaskIdentity.

**Since:** 26.1.0

<!--Device-abilityToolAccessCtrl-interface TaskIdentityInfo--><!--Device-abilityToolAccessCtrl-interface TaskIdentityInfo-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## allowableDuration

```TypeScript
allowableDuration?: number
```

Valid duration of auth token. Unit: seconds. Value range: (0,60].

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-TaskIdentityInfo-allowableDuration?: number--><!--Device-TaskIdentityInfo-allowableDuration?: number-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## allowScreenLockExecution

```TypeScript
allowScreenLockExecution: boolean
```

Whether task is allowed to execute under screen locks.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-TaskIdentityInfo-allowScreenLockExecution: boolean--><!--Device-TaskIdentityInfo-allowScreenLockExecution: boolean-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## authToken

```TypeScript
authToken?: Uint8Array
```

Auth token of trusted device.

**Type:** Uint8Array

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-TaskIdentityInfo-authToken?: Uint8Array--><!--Device-TaskIdentityInfo-authToken?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## executeType

```TypeScript
executeType: ExecuteType
```

Task execute type.

**Type:** [ExecuteType](arkts-ability-abilitytoolaccessctrl-executetype-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-TaskIdentityInfo-executeType: ExecuteType--><!--Device-TaskIdentityInfo-executeType: ExecuteType-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## taskExpireTime

```TypeScript
taskExpireTime: number
```

Task expire time. Unit: seconds.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-TaskIdentityInfo-taskExpireTime: number--><!--Device-TaskIdentityInfo-taskExpireTime: number-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## taskId

```TypeScript
taskId: string
```

Task ID.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-TaskIdentityInfo-taskId: string--><!--Device-TaskIdentityInfo-taskId: string-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.
