# TimeZoneType

Enumerates the time zone types. When the time zone is changed, the reminder time is recalculated based on the new time zone.

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.ReminderAgent

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default value. When the time zone is changed, the reminder time is calculated in the same way as that for the time zone type of **FIXED_TIME_ZONE**. When the time is changed, the reminder time is calculated in the same way as that for the time zone type of **SYSTEM_TIME_ZONE**. You are advised to set the time zone type to **FIXED_TIME_ZONE** or **SYSTEM_TIME_ZONE** based on the service scenario.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## FIXED_TIME_ZONE

```TypeScript
FIXED_TIME_ZONE = 1
```

Fixed time zone, which is used in scenarios such as ticket booking and meetings. For example, if the reminder time is set to 08:00 (GMT+8), the reminder will be triggered at 08:00 (GMT+8) no matter whether the device time zone is changed. If the device time zone is changed to GMT+4, the reminder will be triggered at 04:00. The reminder time is not affected by the change of the system time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## SYSTEM_TIME_ZONE

```TypeScript
SYSTEM_TIME_ZONE = 2
```

System time zone, which is used in scenarios such as setting the alarm clock, fixed time for exercise, and sleep time. For example, if the reminder time is set to 08:00 (GMT+8), and the time zone is changed to GMT+4, the reminder will still be triggered at 08:00. The reminder time is not affected by the change of the system time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent
