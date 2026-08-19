# UserGesturesData（系统接口）

表示用户手势数据。

**继承/实现关系：** UserGesturesData extends [UserFacesData](arkts-multimodalawareness-userstatus-userfacesdata-i-sys.md)

**起始版本：** 26.0.0

<!--Device-userStatus-export interface UserGesturesData--><!--Device-userStatus-export interface UserGesturesData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## directionAngle

```TypeScript
directionAngle?: double[]
```

表示用户手势与屏幕方向的夹角。数组包含手势在多个维度的角度值，每个元素取值范围[0,90]，单位：deg。

**类型：** double[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserGesturesData-directionAngle?: double[]--><!--Device-UserGesturesData-directionAngle?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## gestureSpeed

```TypeScript
gestureSpeed?: double[]
```

表示手势速度。数组长度为2，第一个元素表示速度值，第二个元素为保留位（固定为0），单位：帧/秒。

**类型：** double[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserGesturesData-gestureSpeed?: double[]--><!--Device-UserGesturesData-gestureSpeed?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## handPosition

```TypeScript
handPosition?: double[]
```

表示手相对于屏幕的坐标位置。数组长度为8，分别表示上下左右四个顶点的x、y坐标，归一化坐标系的取值范围是[0,640]。

**类型：** double[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserGesturesData-handPosition?: double[]--><!--Device-UserGesturesData-handPosition?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## handType

```TypeScript
handType?: int
```

表示用户静态手势类型。取值范围[0,3]。0：掌型，1：拳型，2：剪刀，3：比心。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserGesturesData-handType?: int--><!--Device-UserGesturesData-handType?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## isHandExist

```TypeScript
isHandExist?: boolean
```

表示用户手是否存在。取值范围[true,false]。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserGesturesData-isHandExist?: boolean--><!--Device-UserGesturesData-isHandExist?: boolean-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## motionGesture

```TypeScript
motionGesture?: int
```

表示用户动态手势类型。取值范围[0,3]。0：上翻，1：下翻，2：抓屏，3：释放。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserGesturesData-motionGesture?: int--><!--Device-UserGesturesData-motionGesture?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

