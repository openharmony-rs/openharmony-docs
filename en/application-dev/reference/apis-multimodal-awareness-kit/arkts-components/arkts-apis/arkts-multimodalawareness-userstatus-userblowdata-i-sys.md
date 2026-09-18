# UserBlowData (System API)

Defines user blow data.

**Inheritance/Implementation:** UserBlowData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**Since:** 26.0.0

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## blowDirection

```TypeScript
blowDirection?: number
```

Blow direction. The value ranges from 0 to 2. 0: Not blowing, 1: Blowing from bottom mic, 2: Blowing from top mic.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## emotion

```TypeScript
emotion?: number
```

User emotion level. The value ranges from 0 to 5. 0: Very happy, 1: A little happy, 2: Calm, 3: A little unhappy, 4: Angry, 5: Crying.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## facePosition

```TypeScript
facePosition?: number[]
```

Face position relative to screen. The normalized coordinate system ranges from 0 to 640.

**Type:** number[]

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

## isGazeStatus

```TypeScript
isGazeStatus?: boolean
```

Whether user is gazing at screen.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## linearAcceleration

```TypeScript
linearAcceleration?: number[][]
```

Linear acceleration of user motion status, in m/s²..

**Type:** number[][]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## strengthLevel

```TypeScript
strengthLevel?: number
```

Blow strength level. The value must be an integer within [1,12].

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
