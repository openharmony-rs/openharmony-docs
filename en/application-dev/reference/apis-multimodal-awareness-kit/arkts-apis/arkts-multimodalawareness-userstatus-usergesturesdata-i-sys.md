# UserGesturesData (System API)

```TypeScript
export interface UserGesturesData extends UserFacesData
```

Defines user gesture data.

**Inheritance/Implementation:** UserGesturesData extends [UserFacesData](arkts-multimodalawareness-userstatus-userfacesdata-i-sys.md)

**Since:** 26.0.0

<!--Device-userStatus-export interface UserGesturesData extends UserFacesData--><!--Device-userStatus-export interface UserGesturesData extends UserFacesData-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## directionAngle

```TypeScript
directionAngle?: number[]
```

Angle between user gesture and screen directions. The value ranges from 0 to 90, in degrees.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGesturesData-directionAngle?: double[]--><!--Device-UserGesturesData-directionAngle?: double[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## gestureSpeed

```TypeScript
gestureSpeed?: number[]
```

Gesture speed, in frames per second (fps).

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGesturesData-gestureSpeed?: double[]--><!--Device-UserGesturesData-gestureSpeed?: double[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## handPosition

```TypeScript
handPosition?: number[]
```

Hand position relative to screen. The normalized coordinate system ranges from 0 to 640.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGesturesData-handPosition?: double[]--><!--Device-UserGesturesData-handPosition?: double[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## handType

```TypeScript
handType?: number
```

User static gesture type. The value ranges from 0 to 3. 0: Palm, 1: Fist, 2: Scissors, 3: Finger heart.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGesturesData-handType?: int--><!--Device-UserGesturesData-handType?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## isHandExist

```TypeScript
isHandExist?: boolean
```

Whether user hand exists.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGesturesData-isHandExist?: boolean--><!--Device-UserGesturesData-isHandExist?: boolean-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## motionGesture

```TypeScript
motionGesture?: number
```

User dynamic gesture type. The value ranges from 0 to 3. 0: Up, 1: Down, 2: Screen capture, 3: Release.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGesturesData-motionGesture?: int--><!--Device-UserGesturesData-motionGesture?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
