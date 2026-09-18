# UserClassification

Defines the user age group detection result.

**Since:** 20

**Deprecated since:** 24

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

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

## confidence

```TypeScript
confidence?: float
```

Confidence of the detection result. The value is a floating point number ranging from 0 to 1. A larger value indicates a higher confidence.

**Type:** float

**Since:** 20

**Deprecated since:** 24

**System capability:** SystemCapability.MultimodalAwareness.UserStatus
