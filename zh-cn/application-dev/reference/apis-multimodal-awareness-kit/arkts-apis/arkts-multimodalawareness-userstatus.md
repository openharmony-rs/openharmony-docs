# @ohos.multimodalAwareness.userStatus

本模块提供用户状态感知能力，包括年龄群组检测，用户手势识别、人脸位姿识别、手眼协同检测、用户吹气状态检测、用户情绪检测、用户环境音检测等功能。 <br>适用于需要感知用户状态来优化交互体验的场景，能够帮助应用提供更自然、更个性化的用户体验。模块采用订阅/回调机制，通过底层传感器数据采集、 <br>特征提取和状态判断三个阶段实现用户状态检测，开发者可根据业务需求订阅相应的检测功能。

**起始版本：** 23

<!--Device-unnamed-declare namespace userStatus--><!--Device-unnamed-declare namespace userStatus-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offUserAgeGroupDetected](arkts-multimodalawareness-userstatus-offuseragegroupdetected-f.md) | 取消订阅年龄群组检测功能。 |
| [off_userAgeGroupDetected](arkts-multimodalawareness-userstatus-offuseragegroupdetected-f.md) | 取消订阅年龄群组检测功能。 |
| [onUserAgeGroupDetected](arkts-multimodalawareness-userstatus-onuseragegroupdetected-f.md) | 订阅年龄群组检测功能。 |
| [on_userAgeGroupDetected](arkts-multimodalawareness-userstatus-onuseragegroupdetected-f.md) | 订阅年龄群组检测功能。 订阅成功后，可以获取用户年龄群组的分类结果，应用可根据此结果做相应的内容推荐。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [configure](arkts-multimodalawareness-userstatus-configure-f-sys.md) | 配置功能参数。调用成功后，将更新指定功能的配置参数，影响后续该功能的检测行为，如检测灵敏度、采样频率、启用的检测项等。建议在subscribe()之前调用configure()配置功能参数， <br>确保配置在订阅时生效。对于需要特定配置的功能（如USER_MOOD的实时/非实时模式），建议先configure()再subscribe()。 |
| [queryCapabilities](arkts-multimodalawareness-userstatus-querycapabilities-f-sys.md) | 查询设备支持的原子化服务能力。该方法通过底层接口判断是否支持指定的原子化服务能力，返回设备实际支持的能力列表。 |
| [subscribe](arkts-multimodalawareness-userstatus-subscribe-f-sys.md) | 订阅用户状态监控，以获取用户状态数据。调用subscribe()后，必须在使用完毕后调用unsubscribe()取消订阅以释放回调资源，未调用unsubscribe()会导致回调资源泄漏， <br>影响应用性能。建议先调用configure()配置功能参数，再调用subscribe()开始订阅。 |
| [unsubscribe](arkts-multimodalawareness-userstatus-unsubscribe-f-sys.md) | 取消订阅用户状态监控。与subscribe()方法成对使用，用于取消订阅回调并释放资源。必须在subscribe()之后调用，取消未订阅的featureId返回失败。 <br>建议在应用退出或不再需要监控时调用unsubscribe()。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [UserClassification](arkts-multimodalawareness-userstatus-userclassification-i.md) | 表示用户年龄群组分类检测结果。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ComfortReminderData](arkts-multimodalawareness-userstatus-comfortreminderdata-i-sys.md) | 表示舒适提醒数据。 |
| [DeviceInfo](arkts-multimodalawareness-userstatus-deviceinfo-i-sys.md) | 表示设备信息。 |
| [UserBlowData](arkts-multimodalawareness-userstatus-userblowdata-i-sys.md) | 表示用户吹气数据。 |
| [UserEmotionData](arkts-multimodalawareness-userstatus-useremotiondata-i-sys.md) | 表示用户情绪数据。 |
| [UserFaceAngleData](arkts-multimodalawareness-userstatus-userfaceangledata-i-sys.md) | 表示用户朝向角度数据。 |
| [UserFacesData](arkts-multimodalawareness-userstatus-userfacesdata-i-sys.md) | 表示用户朝向屏幕相关的数据。 |
| [UserGesturesData](arkts-multimodalawareness-userstatus-usergesturesdata-i-sys.md) | 表示用户手势数据。 |
| [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md) | 表示用户状态数据。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [UserAgeGroup](arkts-multimodalawareness-userstatus-useragegroup-e.md) | 表示用户具体的年龄分类群组，例如，儿童或成年人。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceType](arkts-multimodalawareness-userstatus-devicetype-e-sys.md) | 表示设备类型。 |
| [ReminderLevel](arkts-multimodalawareness-userstatus-reminderlevel-e-sys.md) | 表示提醒强度级别，触发提醒铃声时使用。 |
| [UserStatusAtomicCap](arkts-multimodalawareness-userstatus-userstatusatomiccap-e-sys.md) | 表示用户状态支持的原子化服务能力。 |
| [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | 表示用户状态检测功能类型。 |
<!--DelEnd-->

