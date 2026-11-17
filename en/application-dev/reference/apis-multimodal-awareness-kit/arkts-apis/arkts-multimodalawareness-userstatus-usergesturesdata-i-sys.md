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

Angle between the user's gesture and the screen direction. The array contains the angle values of the gesture in multiple dimensions. The value range of each elementis [0, 90]. Unit: deg.

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

Coordinate position of the hand relative to the screen. The array length is 8, representing the x and y coordinates of the four vertices (top, bottom, left, and right). The value range in the normalized coordinate system is [0, 640].

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

User's static gesture type. Value range: [0, 3]. 0: palm, 1: fist, 2: scissors, 3: heart.

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

Whether the user's hand exists. Value range: [true, false].

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

User's dynamic gesture type. Value range: [0, 3]. 0: flip up, 1: flip down, 2: grab screen, 3: release.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UserGesturesData-motionGesture?: int--><!--Device-UserGesturesData-motionGesture?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
