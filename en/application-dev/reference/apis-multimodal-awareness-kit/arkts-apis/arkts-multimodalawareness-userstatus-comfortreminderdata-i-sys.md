# ComfortReminderData (System API)

```TypeScript
export interface ComfortReminderData extends UserStatusData
```

Defines comfort reminder data.

**Inheritance/Implementation:** ComfortReminderData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**Since:** 26.0.0

<!--Device-userStatus-export interface ComfortReminderData extends UserStatusData--><!--Device-userStatus-export interface ComfortReminderData extends UserStatusData-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## eventType

```TypeScript
eventType: number
```

Event type. The value 0 indicates a gaze event, and 1 indicates an ambient sound event.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ComfortReminderData-eventType: int--><!--Device-ComfortReminderData-eventType: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## fusionReminderData

```TypeScript
fusionReminderData: ReminderLevel
```

Reminder level after comprehensive detection.

**Type:** [ReminderLevel](arkts-multimodalawareness-userstatus-reminderlevel-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ComfortReminderData-fusionReminderData: ReminderLevel--><!--Device-ComfortReminderData-fusionReminderData: ReminderLevel-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

## swingReminderData

```TypeScript
swingReminderData: ReminderLevel
```

Reminder level when gazing at the screen.

**Type:** [ReminderLevel](arkts-multimodalawareness-userstatus-reminderlevel-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ComfortReminderData-swingReminderData: ReminderLevel--><!--Device-ComfortReminderData-swingReminderData: ReminderLevel-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.
