# UserBlowData（系统接口）

用户吹气数据。

**继承/实现关系：** UserBlowData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md#UserStatusData（系统接口）)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-userStatus-export interface UserBlowData--><!--Device-userStatus-export interface UserBlowData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## blowDirection

```TypeScript
blowDirection?: int
```

吹气方向。取值范围为0到2。0：未吹气，1：从底部麦克风吹气，2：从顶部麦克风吹气。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-blowDirection?: int--><!--Device-UserBlowData-blowDirection?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## emotion

```TypeScript
emotion?: int
```

用户情绪级别。取值范围为0到5。0：非常开心，1：有些开心，2：平静，3：有些不开心，4：生气，5：哭泣。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-emotion?: int--><!--Device-UserBlowData-emotion?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## facePosition

```TypeScript
facePosition?: double[]
```

面部相对于屏幕的位置。归一化坐标系范围为0到640。

**类型：** double[]

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-facePosition?: double[]--><!--Device-UserBlowData-facePosition?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## gravityAcceleration

```TypeScript
gravityAcceleration?: double[]
```

用户运动状态的重力加速度，单位：m/s²。

**类型：** double[]

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-gravityAcceleration?: double[]--><!--Device-UserBlowData-gravityAcceleration?: double[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## isGazeStatus

```TypeScript
isGazeStatus?: boolean
```

用户是否正在注视屏幕。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-isGazeStatus?: boolean--><!--Device-UserBlowData-isGazeStatus?: boolean-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## linearAcceleration

```TypeScript
linearAcceleration?: double[][]
```

用户运动状态的线性加速度，单位：m/s²。

**类型：** double[][]

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-linearAcceleration?: double[][]--><!--Device-UserBlowData-linearAcceleration?: double[][]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## strengthLevel

```TypeScript
strengthLevel?: int
```

吹气强度级别。取值范围为[1,12]的整数。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserBlowData-strengthLevel?: int--><!--Device-UserBlowData-strengthLevel?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

