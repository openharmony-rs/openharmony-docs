# UserStatusData (System API)

```TypeScript
export interface UserStatusData
```

Defines user status data.

**Since:** 26.0.0

<!--Device-userStatus-export interface UserStatusData--><!--Device-userStatus-export interface UserStatusData-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## errCode

```TypeScript
errCode: number
```

Business error code. The value `0` indicates success, and other values indicate failure.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserStatusData-errCode: int--><!--Device-UserStatusData-errCode: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## feature

```TypeScript
feature: UserStatusFeature
```

User status detection feature type.

**Type:** [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserStatusData-feature: UserStatusFeature--><!--Device-UserStatusData-feature: UserStatusFeature-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## result

```TypeScript
result: number
```

User status detection result. The value `0` indicates success, and other values indicate failure.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserStatusData-result: int--><!--Device-UserStatusData-result: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## status

```TypeScript
status: string
```

Multi-stage detection status under a specific function. The string value indicates the corresponding detection status, and the maximum length of the string is 64.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserStatusData-status: string--><!--Device-UserStatusData-status: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
