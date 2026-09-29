# NotificationSwitchChangedCallbackData (System API)

```TypeScript
export interface NotificationSwitchChangedCallbackData
```

Returns the changes of the notification switch state.

**Since:** 26.0.0

<!--Device-unnamed-export interface NotificationSwitchChangedCallbackData--><!--Device-unnamed-export interface NotificationSwitchChangedCallbackData-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## enableStatus

```TypeScript
readonly enableStatus: notificationManager.SwitchState
```

Notification switch state.

**Type:** [notificationManager.SwitchState](arkts-notification-notificationmanager-switchstate-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSwitchChangedCallbackData-readonly enableStatus: notificationManager.SwitchState--><!--Device-NotificationSwitchChangedCallbackData-readonly enableStatus: notificationManager.SwitchState-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## switchName

```TypeScript
readonly switchName: string
```

Notification switch name. The value can be **DEAL** (aggregated switch for transaction notifications) or **LOGISTICS** (aggregated switch for logistics notifications).

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSwitchChangedCallbackData-readonly switchName: string--><!--Device-NotificationSwitchChangedCallbackData-readonly switchName: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## userId

```TypeScript
readonly userId: number
```

User ID.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSwitchChangedCallbackData-readonly userId: int--><!--Device-NotificationSwitchChangedCallbackData-readonly userId: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
