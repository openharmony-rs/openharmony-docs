# @ohos.multimodalAwareness.userStatus(User state awareness)

The **UserStatus** module, designed for user state awareness, empowers the system to perceive specific conditions of users, such as determining their age group or recognizing environmental sounds, among other functions.

**Since:** 20

<!--Device-unnamed-declare namespace userStatus--><!--Device-unnamed-declare namespace userStatus-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off('userAgeGroupDetected')](arkts-multimodalawareness-userstatus-off-f.md#offuseragegroupdetected) | Disables the age group detection function. |
| [on('userAgeGroupDetected')](arkts-multimodalawareness-userstatus-on-f.md#onuseragegroupdetected) | Enables the age group detection function. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [configure](arkts-multimodalawareness-userstatus-configure-f-sys.md#configure-1) | Configures feature parameters. After a successful call, the configuration parameters of the specified feature are updated, affecting the subsequent detection behavior of the feature, such as detection sensitivity, sampling frequency, and enabled detection items. It is recommended to call configure() to configure feature parameters before subscribe() to ensure that the configuration takes effect upon subscription. For features that require specific configuration (such as the real-time/non-real-time mode of USER_MOOD), it is recommended to call configure() before subscribe(). |
| [queryCapabilities](arkts-multimodalawareness-userstatus-querycapabilities-f-sys.md#querycapabilities-1) | Queries the atomic capabilities supported by the device. This method determines whether the specified atomic capabilities are supported through the underlying interface and returns the list of capabilities actually supported by the device. |
| [subscribe](arkts-multimodalawareness-userstatus-subscribe-f-sys.md#subscribe-1) | Subscribes to user status monitoring to obtain user status data. After calling subscribe(), you must call unsubscribe() to cancel the subscription and release callback resources when they are no longer needed. Failure to call unsubscribe() causes callback resource leakage and affects application performance. It is recommended to call configure() to configure feature parameters before calling subscribe() to start the subscription. |
| [unsubscribe](arkts-multimodalawareness-userstatus-unsubscribe-f-sys.md#unsubscribe-1) | Unsubscribes from user status monitoring. This method is used in pair with subscribe() to cancel the subscription callback and release resources. It must be called after subscribe(). Unsubscribing from a featureId that is not subscribed returns a failure. It is recommended to call unsubscribe() when the application exits or no longer needs monitoring. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [UserClassification](arkts-multimodalawareness-userstatus-userclassification-i.md) | Defines the user age group detection result. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ComfortReminderData](arkts-multimodalawareness-userstatus-comfortreminderdata-i-sys.md) | Defines comfort reminder data. |
| [DeviceInfo](arkts-multimodalawareness-userstatus-deviceinfo-i-sys.md) | Defines device information. |
| [UserBlowData](arkts-multimodalawareness-userstatus-userblowdata-i-sys.md) | Defines user blow data. |
| [UserEmotionData](arkts-multimodalawareness-userstatus-useremotiondata-i-sys.md) | Defines user emotion data. |
| [UserFaceAngleData](arkts-multimodalawareness-userstatus-userfaceangledata-i-sys.md) | Defines user face angle data. |
| [UserFacesData](arkts-multimodalawareness-userstatus-userfacesdata-i-sys.md) | Defines user face data. |
| [UserGesturesData](arkts-multimodalawareness-userstatus-usergesturesdata-i-sys.md) | Defines user gesture data. |
| [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md) | Defines user status data. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [UserAgeGroup](arkts-multimodalawareness-userstatus-useragegroup-e.md) | Enumerates the user age groups, for example, child or adult. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DeviceType](arkts-multimodalawareness-userstatus-devicetype-e-sys.md) | Enumerates device types. |
| [ReminderLevel](arkts-multimodalawareness-userstatus-reminderlevel-e-sys.md) | Enumerates comfort reminder levels required for triggering specific alert ringtones. |
| [UserStatusAtomicCap](arkts-multimodalawareness-userstatus-userstatusatomiccap-e-sys.md) | Enumerates user status atomic capabilities. |
| [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | Enumerates user status detection features. |
<!--DelEnd-->
