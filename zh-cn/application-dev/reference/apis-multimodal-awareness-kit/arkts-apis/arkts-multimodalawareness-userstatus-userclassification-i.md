# UserClassification

表示用户年龄群组分类检测结果。

**起始版本：** 23

**废弃版本：** 24

<!--Device-userStatus-export interface UserClassification--><!--Device-userStatus-export interface UserClassification-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## ageGroup

```TypeScript
ageGroup?: UserAgeGroup
```

表示具体的年龄群组（例如，儿童、成人）。

**类型：** [UserAgeGroup](arkts-multimodalawareness-userstatus-useragegroup-e.md)

**起始版本：** 23

**废弃版本：** 24

<!--Device-UserClassification-ageGroup?: UserAgeGroup--><!--Device-UserClassification-ageGroup?: UserAgeGroup-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

## confidence

```TypeScript
confidence?: float
```

表示年龄群组检测结果的置信度，取值范围[0,1]的浮点数，数值越大代表置信度越高。

**类型：** float

**起始版本：** 23

**废弃版本：** 24

<!--Device-UserClassification-confidence?: float--><!--Device-UserClassification-confidence?: float-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

