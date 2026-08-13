# @ohos.multimodalAwareness.userStatus

本模块提供用户状态感知能力，包括年龄群组检测等功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace userStatus--><!--Device-unnamed-declare namespace userStatus-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offUserAgeGroupDetected](arkts-multimodalawareness-userstatus-offuseragegroupdetected-f.md#offUserAgeGroupDetected) | 取消订阅年龄群组检测功能。 |
| off_userAgeGroupDetected | 取消订阅年龄群组检测功能。 |
| [onUserAgeGroupDetected](arkts-multimodalawareness-userstatus-onuseragegroupdetected-f.md#onUserAgeGroupDetected) | 订阅年龄群组检测功能。 |
| on_userAgeGroupDetected | 订阅年龄群组检测功能。 订阅成功后，可以获取用户年龄群组的分类结果，应用可根据此结果做相应的内容推荐。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [configure](arkts-multimodalawareness-userstatus-configure-f-sys.md#configure) | 配置特性参数。 |
| [queryCapabilities](arkts-multimodalawareness-userstatus-querycapabilities-f-sys.md#queryCapabilities) | 查询设备支持的原子能力。 |
| [subscribe](arkts-multimodalawareness-userstatus-subscribe-f-sys.md#subscribe) | 订阅用户状态监测。 |
| [unsubscribe](arkts-multimodalawareness-userstatus-unsubscribe-f-sys.md#unsubscribe) | 取消订阅用户状态监测。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [UserClassification](arkts-multimodalawareness-userstatus-userclassification-i.md) | 表示用户年龄群组分类检测结果。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ComfortReminderData](arkts-multimodalawareness-userstatus-comfortreminderdata-i-sys.md) | 舒适提醒数据。 |
| [DeviceInfo](arkts-multimodalawareness-userstatus-deviceinfo-i-sys.md) | 设备信息。 |
| [UserBlowData](arkts-multimodalawareness-userstatus-userblowdata-i-sys.md) | 用户吹气数据。 |
| [UserEmotionData](arkts-multimodalawareness-userstatus-useremotiondata-i-sys.md) | 用户情绪数据。 |
| [UserFaceAngleData](arkts-multimodalawareness-userstatus-userfaceangledata-i-sys.md) | 用户面部角度数据。 |
| [UserFacesData](arkts-multimodalawareness-userstatus-userfacesdata-i-sys.md) | 用户面部数据。 |
| [UserGesturesData](arkts-multimodalawareness-userstatus-usergesturesdata-i-sys.md) | 用户手势数据。 |
| [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md) | 用户状态数据。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [UserAgeGroup](arkts-multimodalawareness-userstatus-useragegroup-e.md) | 表示用户具体的年龄分类群组，例如，儿童或成年人。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceType](arkts-multimodalawareness-userstatus-devicetype-e-sys.md) | 设备类型枚举。 |
| [ReminderLevel](arkts-multimodalawareness-userstatus-reminderlevel-e-sys.md) | 触发特定提醒铃声所需的舒适提醒级别枚举。 |
| [UserStatusAtomicCap](arkts-multimodalawareness-userstatus-userstatusatomiccap-e-sys.md) | 用户状态原子能力枚举。 |
| [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | 用户状态检测特性枚举。 |
<!--DelEnd-->

