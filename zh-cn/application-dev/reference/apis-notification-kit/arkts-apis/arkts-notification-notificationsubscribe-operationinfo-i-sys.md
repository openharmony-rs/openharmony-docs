# OperationInfo（系统接口）

跨设备协同操作信息。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-notificationSubscribe-export interface OperationInfo--><!--Device-notificationSubscribe-export interface OperationInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## actionName

```TypeScript
actionName?: string
```

描述通知中显示的操作按钮（与通知 [NotificationActionButton]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中title字段保持一致）。

**类型：** string

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-OperationInfo-actionName?: string--><!--Device-OperationInfo-actionName?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## buttonIndex

```TypeScript
buttonIndex?: int
```

用户点击的非实况通知按钮序号或实况通知辅助区序号。

**类型：** int

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-OperationInfo-buttonIndex?: int--><!--Device-OperationInfo-buttonIndex?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## operationType

```TypeScript
operationType?: int
```

用户点击操作类型。 - 0：用户点击非实况通知本体。 - 1：用户点击非实况通知按钮。 - 32：用户点击实况通知本体。 - 33：用户点击实况通知辅助区

**类型：** int

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-OperationInfo-operationType?: int--><!--Device-OperationInfo-operationType?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## userInput

```TypeScript
userInput?: string
```

用户输入（用于通知跨设备快捷回复场景传递用户输入，与通知 [NotificationUserInput]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中inputKey字段保持一致）。

**类型：** string

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-OperationInfo-userInput?: string--><!--Device-OperationInfo-userInput?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

