# @ohos.multimodalAwareness.userStatus

The **UserStatus** module, designed for user state awareness, empowers the system to perceive specific conditions of users, such as determining their age group or recognizing environmental sounds, among other functions.

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off](arkts-multimodalawareness-userstatus-off-f.md#offuseragegroupdetected) | Disables the age group detection function. |
| [on](arkts-multimodalawareness-userstatus-on-f.md#onuseragegroupdetected) | Enables the age group detection function. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [configure](arkts-multimodalawareness-userstatus-configure-f-sys.md) | Configures feature parameters. |
| [queryCapabilities](arkts-multimodalawareness-userstatus-querycapabilities-f-sys.md) | Queries device-supported atomic capabilities. |
| [subscribe](arkts-multimodalawareness-userstatus-subscribe-f-sys.md) | Subscribes to user status monitoring. |
| [unsubscribe](arkts-multimodalawareness-userstatus-unsubscribe-f-sys.md) | Unsubscribes from user status monitoring. |
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
