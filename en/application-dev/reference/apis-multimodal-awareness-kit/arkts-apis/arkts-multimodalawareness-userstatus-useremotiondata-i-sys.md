# UserEmotionData (System API)

Defines user emotion data.

**Inheritance/Implementation:** UserEmotionData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**Since:** 26.0.0

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## confidence

```TypeScript
confidence?: number
```

User emotion confidence. The value ranges from 0 to 100. A larger value indicates a higher confidence.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## emotionNonRealTime

```TypeScript
emotionNonRealTime ?: number[]
```

User non-real-time emotion level. The value ranges from 0 to 5. 0: Very happy, 1: A little happy, 2: Calm, 3: A little unhappy, 4: Angry, 5: Crying.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## emotionRealTime

```TypeScript
emotionRealTime ?: number
```

User real-time emotion level. The value ranges from 0 to 5. 0: Very happy, 1: A little happy, 2: Calm, 3: A little unhappy, 4: Angry, 5: Crying.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## gravityAcceleration

```TypeScript
gravityAcceleration?: number[]
```

Gravity acceleration of user motion status, in m/s².

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## isRealTime

```TypeScript
isRealTime?: boolean
```

Whether emotion data is real-time.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## linearAcceleration

```TypeScript
linearAcceleration?: number[][]
```

Linear acceleration of user motion status, in m/s².

**Type:** number[][]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
