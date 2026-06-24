# NotificationSlot

描述通知渠道，不同通知渠道对应的通知提醒方式不同。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## authorizedStatus

```TypeScript
readonly authorizedStatus?: number
```

授权状态。

- 0：表示已授权。
- 1：表示待授权。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## reminderMode

```TypeScript
readonly reminderMode?: number
```

通知提醒模式。

- bit0：铃声提示。0表示关闭，1表示开启。
- bit1：锁屏。0表示关闭，1表示开启。
- bit2：横幅。0表示关闭，1表示开启。
- bit3：亮屏。0表示关闭，1表示开启。
- bit4：振动。0表示关闭，1表示开启。
- bit5：状态栏通知图标。0表示关闭，1表示开启。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

