# UserFacesData（系统接口）

表示用户朝向屏幕相关的数据。

**继承/实现关系：** UserFacesData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**起始版本：** 26.0.0

<!--Device-userStatus-export interface UserFacesData--><!--Device-userStatus-export interface UserFacesData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## angularVelocity

```TypeScript
angularVelocity?: double[]
```

表示当前状态下设备的角速度。数组长度为3，分别表示绕x、y、z三个轴旋转的角速度分量，单位：rad/s。

**类型：** double[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserFacesData-angularVelocity?: double[]--><!--Device-UserFacesData-angularVelocity?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## azimuth

```TypeScript
azimuth?: double[]
```

表示当前状态下设备的方位角。数组长度为3，分别表示偏航角（绕y轴）、俯仰角（绕x轴）和翻滚角（绕z轴），取值范围[0,360]。单位：deg。

**类型：** double[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserFacesData-azimuth?: double[]--><!--Device-UserFacesData-azimuth?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## faceNum

```TypeScript
faceNum?: int
```

表示检测到的人脸数量。取值范围[0,3]。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserFacesData-faceNum?: int--><!--Device-UserFacesData-faceNum?: int-End-->

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

<!--Device-UserFacesData-gravityAcceleration?: double[]--><!--Device-UserFacesData-gravityAcceleration?: double[]-End-->

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

<!--Device-UserFacesData-linearAcceleration?: double[][]--><!--Device-UserFacesData-linearAcceleration?: double[][]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## visualAngle

```TypeScript
visualAngle?: double[]
```

表示用户看屏幕的视角。取值范围[0,90]。单位：deg。

**类型：** double[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserFacesData-visualAngle?: double[]--><!--Device-UserFacesData-visualAngle?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

