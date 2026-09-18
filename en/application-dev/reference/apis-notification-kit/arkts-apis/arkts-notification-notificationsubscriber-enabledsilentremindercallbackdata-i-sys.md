# EnabledSilentReminderCallbackData (System API)

Returns the application notification silent reminder switch state.

**Since:** 24

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## bundle

```TypeScript
readonly bundle: string
```

Bundle name of the application.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## enableStatus

```TypeScript
readonly enableStatus: notificationManager.SwitchState
```

Enabling state of the application's silent reminder.  
- **USER_MODIFIED_OFF**: disabled state set by the user.  
- **USER_MODIFIED_ON**: enabled state set by the user.  
- **SYSTEM_DEFAULT_OFF**: initial disabled state before user setting.  
- **SYSTEM_DEFAULT_ON**: initial enabled state before user setting.

**Type:** [notificationManager.SwitchState](arkts-notification-notificationmanager-switchstate-e-sys.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## uid

```TypeScript
readonly uid: number
```

UID of the application.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
