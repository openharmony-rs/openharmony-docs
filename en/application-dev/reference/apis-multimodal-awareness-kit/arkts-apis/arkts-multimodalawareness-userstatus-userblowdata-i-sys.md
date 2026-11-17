# UserBlowData (System API)

```TypeScript
export interface UserBlowData extends UserStatusData
```

Defines user blow data.

**Inheritance/Implementation:** UserBlowData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**Since:** 26.0.0

<!--Device-userStatus-export interface UserBlowData extends UserStatusData--><!--Device-userStatus-export interface UserBlowData extends UserStatusData-End-->

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

<!--Device-UserBlowData-blowDirection?: int--><!--Device-UserBlowData-blowDirection?: int-End-->

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

<!--Device-UserBlowData-emotion?: int--><!--Device-UserBlowData-emotion?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## facePosition

```TypeScript
facePosition?: number[]
```

Coordinates of the face relative to the screen. The array length is 8, representing the x and y coordinates of the four vertices (top, bottom, left, and right). The value range in the normalized coordinate system is [0,640]. Unit: px

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserBlowData-facePosition?: double[]--><!--Device-UserBlowData-facePosition?: double[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## gravityAcceleration

```TypeScript
gravityAcceleration?: number[]
```

Gravity acceleration of the device in the current state. The array length is 3, representing the acceleration components in the x, y, and z directions. Unit: m/s².

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserBlowData-gravityAcceleration?: double[]--><!--Device-UserBlowData-gravityAcceleration?: double[]-End-->

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

<!--Device-UserBlowData-isGazeStatus?: boolean--><!--Device-UserBlowData-isGazeStatus?: boolean-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## linearAcceleration

```TypeScript
linearAcceleration?: number[][]
```

Linear acceleration of the device in the current state. A two-dimensional array. The outer layer represents sampling at multiple points, and the inner layer is an array of length 3, representing the acceleration components in the x, y, and z directions. Unit: m/s².

**Type:** number[][]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserBlowData-linearAcceleration?: double[][]--><!--Device-UserBlowData-linearAcceleration?: double[][]-End-->

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

<!--Device-UserBlowData-strengthLevel?: int--><!--Device-UserBlowData-strengthLevel?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
