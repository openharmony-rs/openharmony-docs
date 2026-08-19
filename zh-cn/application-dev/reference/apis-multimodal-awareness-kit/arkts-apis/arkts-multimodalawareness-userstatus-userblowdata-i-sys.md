# UserBlowData（系统接口）

表示用户吹气数据。

**继承/实现关系：** UserBlowData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**起始版本：** 26.0.0

<!--Device-userStatus-export interface UserBlowData--><!--Device-userStatus-export interface UserBlowData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## blowDirection

```TypeScript
blowDirection?: int
```

表示吹气方向。取值范围[0,2]。0：未吹气，1：底部麦克风，2：顶部麦克风。 取值范围为全体整数。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-blowDirection?: int--><!--Device-UserBlowData-blowDirection?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## emotion

```TypeScript
emotion?: int
```

表示用户情绪级别。取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。 取值限定为整数。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-emotion?: int--><!--Device-UserBlowData-emotion?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## facePosition

```TypeScript
facePosition?: double[]
```

表示人脸相对于屏幕的坐标位置。数组长度为8，分别表示上下左右四个顶点的x、y坐标，归一化坐标系的取值范围是[0,640]。单位：px

**类型：** double[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-facePosition?: double[]--><!--Device-UserBlowData-facePosition?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## gravityAcceleration

```TypeScript
gravityAcceleration?: double[]
```

表示当前状态下设备的重力加速度。数组长度为3，分别表示x、y、z三个方向的加速度分量，单位：m/s²。

**类型：** double[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-gravityAcceleration?: double[]--><!--Device-UserBlowData-gravityAcceleration?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## isGazeStatus

```TypeScript
isGazeStatus?: boolean
```

表示用户是否注视屏幕。取值范围[true,false]。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-isGazeStatus?: boolean--><!--Device-UserBlowData-isGazeStatus?: boolean-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## linearAcceleration

```TypeScript
linearAcceleration?: double[][]
```

表示当前状态下设备的线性加速度。二维数组，外层表示多个点位的采样，内层为长度3的数组，分别表示x、y、z三个方向的加速度分量，单位：m/s²。

**类型：** double[][]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-linearAcceleration?: double[][]--><!--Device-UserBlowData-linearAcceleration?: double[][]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## strengthLevel

```TypeScript
strengthLevel?: int
```

表示吹气力度。取值范围[1,12]。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-strengthLevel?: int--><!--Device-UserBlowData-strengthLevel?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

