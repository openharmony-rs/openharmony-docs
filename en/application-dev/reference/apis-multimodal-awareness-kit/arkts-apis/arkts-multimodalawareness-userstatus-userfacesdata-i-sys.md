# UserFacesData (System API)

```TypeScript
export interface UserFacesData extends UserStatusData
```

Defines user face data.

**Inheritance/Implementation:** UserFacesData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**Since:** 26.0.0

<!--Device-userStatus-export interface UserFacesData extends UserStatusData--><!--Device-userStatus-export interface UserFacesData extends UserStatusData-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## angularVelocity

```TypeScript
angularVelocity?: number[]
```

Angular velocity of the device in the current state. The array length is 3, representing the angular velocity components of rotation around the x, y, and z axes respectively. Unit: rad/s.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserFacesData-angularVelocity?: double[]--><!--Device-UserFacesData-angularVelocity?: double[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## azimuth

```TypeScript
azimuth?: number[]
```

Azimuth of the device in the current state. The array length is 3, representing the yaw angle (around the y-axis), pitch angle (around the x-axis), and roll angle (around the z-axis) respectively. Value range: [0, 360]. Unit: deg.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserFacesData-azimuth?: double[]--><!--Device-UserFacesData-azimuth?: double[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## faceNum

```TypeScript
faceNum?: number
```

Number of detected faces. Value range: [0, 3].

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserFacesData-faceNum?: int--><!--Device-UserFacesData-faceNum?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## gravityAcceleration

```TypeScript
gravityAcceleration?: number[]
```

Gravity acceleration of the device in the current state. The array length is 3, representing the acceleration components in the x, y, and z directions respectively. Unit: m/s².

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserFacesData-gravityAcceleration?: double[]--><!--Device-UserFacesData-gravityAcceleration?: double[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## linearAcceleration

```TypeScript
linearAcceleration?: number[][]
```

Linear acceleration of the device in the current state. Two-dimensional array. The outer layer represents sampling at multiple points, and the inner layer is an array of length 3, representing the acceleration components in the x, y, and z directions respectively. Unit: m/s².

**Type:** number[][]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserFacesData-linearAcceleration?: double[][]--><!--Device-UserFacesData-linearAcceleration?: double[][]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## visualAngle

```TypeScript
visualAngle?: number[]
```

Viewing angle of the user looking at the screen. Value range: [0, 90]. Unit: deg.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserFacesData-visualAngle?: double[]--><!--Device-UserFacesData-visualAngle?: double[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
