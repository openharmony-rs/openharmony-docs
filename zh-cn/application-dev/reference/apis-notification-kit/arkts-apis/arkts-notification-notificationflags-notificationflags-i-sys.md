# NotificationFlags

描述通知标志位。

**起始版本：** 8

<!--Device-unnamed-export interface NotificationFlags--><!--Device-unnamed-export interface NotificationFlags-End-->

**系统能力：** SystemCapability.Notification.Notification

## reminderFlags

```TypeScript
readonly reminderFlags?: number
```

是否启用输入信息提示功能。

- bit0：铃声提示。0表示关闭，1表示开启。  
- bit1：锁屏。0表示关闭，1表示开启。  
- bit2：横幅。0表示关闭，1表示开启。  
- bit3：亮屏。0表示关闭，1表示开启。  
- bit4：振动。0表示关闭，1表示开启。  
- bit5：状态栏通知图标。0表示关闭，1表示开启。

**类型：** number

**起始版本：** 11

<!--Device-NotificationFlags-readonly reminderFlags?: long--><!--Device-NotificationFlags-readonly reminderFlags?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

