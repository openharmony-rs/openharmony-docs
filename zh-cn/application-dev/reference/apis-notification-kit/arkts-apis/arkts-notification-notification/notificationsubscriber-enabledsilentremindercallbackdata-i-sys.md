# EnabledSilentReminderCallbackData（系统接口）

应用通知静默提醒开关状态的回调函数类型。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export interface EnabledSilentReminderCallbackData--><!--Device-unnamed-export interface EnabledSilentReminderCallbackData-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## bundle

```TypeScript
readonly bundle: string
```

应用的包名。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EnabledSilentReminderCallbackData-readonly bundle: string--><!--Device-EnabledSilentReminderCallbackData-readonly bundle: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## enableStatus

```TypeScript
readonly enableStatus: notificationManager.SwitchState
```

应用通知的静默提醒开关状态。 - USER\_MODIFIED\_OFF：用户设置的关闭状态。 - USER\_MODIFIED\_ON：用户设置的开启状态。 - SYSTEM\_DEFAULT\_OFF：用户设置前的初始关闭状态。 - SYSTEM\_DEFAULT\_ON：用户设置前的初始开启状态。

**类型：** notificationManager.SwitchState

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EnabledSilentReminderCallbackData-readonly enableStatus: notificationManager.SwitchState--><!--Device-EnabledSilentReminderCallbackData-readonly enableStatus: notificationManager.SwitchState-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
readonly uid: int
```

应用的uid。

**类型：** int

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EnabledSilentReminderCallbackData-readonly uid: int--><!--Device-EnabledSilentReminderCallbackData-readonly uid: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

