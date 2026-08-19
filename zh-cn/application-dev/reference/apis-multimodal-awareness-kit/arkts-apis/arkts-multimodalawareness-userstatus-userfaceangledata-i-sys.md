# UserFaceAngleData（系统接口）

表示用户朝向角度数据。

**继承/实现关系：** UserFaceAngleData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**起始版本：** 26.0.0

<!--Device-userStatus-export interface UserFaceAngleData--><!--Device-userStatus-export interface UserFaceAngleData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## hpeNetworkId

```TypeScript
hpeNetworkId: string
```

表示用户所面向的设备的网络ID。字符串长度范围[0,128]。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserFaceAngleData-hpeNetworkId: string--><!--Device-UserFaceAngleData-hpeNetworkId: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

