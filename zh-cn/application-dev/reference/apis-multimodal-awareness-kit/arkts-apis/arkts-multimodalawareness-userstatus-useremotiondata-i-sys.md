# UserEmotionData（系统接口）

表示用户情绪数据。

**继承/实现关系：** UserEmotionData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**起始版本：** 26.0.0

<!--Device-userStatus-export interface UserEmotionData--><!--Device-userStatus-export interface UserEmotionData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## confidence

```TypeScript
confidence?: int
```

表示用户情绪置信度百分比。取值范围[0,100]。 取值范围为全体整数。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserEmotionData-confidence?: int--><!--Device-UserEmotionData-confidence?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## emotionNonRealTime

```TypeScript
emotionNonRealTime ?: int[]
```

表示用户非实时情绪级别。数组包含一段时间内采集的多个情绪值，每个元素取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。

**类型：** int[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserEmotionData-emotionNonRealTime ?: int[]--><!--Device-UserEmotionData-emotionNonRealTime ?: int[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## emotionRealTime

```TypeScript
emotionRealTime ?: int
```

表示用户实时情绪级别。取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。 取值限定为整数。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserEmotionData-emotionRealTime ?: int--><!--Device-UserEmotionData-emotionRealTime ?: int-End-->

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

<!--Device-UserEmotionData-gravityAcceleration?: double[]--><!--Device-UserEmotionData-gravityAcceleration?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## isRealTime

```TypeScript
isRealTime?: boolean
```

表示情绪数据是否为实时数据。取值范围[true,false]。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserEmotionData-isRealTime?: boolean--><!--Device-UserEmotionData-isRealTime?: boolean-End-->

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

<!--Device-UserEmotionData-linearAcceleration?: double[][]--><!--Device-UserEmotionData-linearAcceleration?: double[][]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

