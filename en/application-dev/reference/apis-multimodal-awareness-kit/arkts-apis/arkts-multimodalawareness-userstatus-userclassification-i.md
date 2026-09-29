# UserClassification

```TypeScript
export interface UserClassification
```

Defines the user age group detection result.

**Since:** 20

**Deprecated since:** 24

<!--Device-userStatus-export interface UserClassification--><!--Device-userStatus-export interface UserClassification-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## ageGroup

```TypeScript
ageGroup?: UserAgeGroup
```

User age group, for example, child or adult.

**Type:** [UserAgeGroup](arkts-multimodalawareness-userstatus-useragegroup-e.md)

**Since:** 20

**Deprecated since:** 24

<!--Device-UserClassification-ageGroup?: UserAgeGroup--><!--Device-UserClassification-ageGroup?: UserAgeGroup-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

## confidence

```TypeScript
confidence?: float
```

Confidence of the detection result. The value is a floating point number ranging from 0 to 1. A larger value indicates a higher confidence.

**Type:** float

**Since:** 20

**Deprecated since:** 24

<!--Device-UserClassification-confidence?: float--><!--Device-UserClassification-confidence?: float-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus
