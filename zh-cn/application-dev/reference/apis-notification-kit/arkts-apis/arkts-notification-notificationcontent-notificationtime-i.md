# NotificationTime

描述通知计时信息。

> **说明：**  
>  
> 实际显示效果依赖于设备能力和通知中心UI样式。

**起始版本：** 11

<!--Device-unnamed-export interface NotificationTime--><!--Device-unnamed-export interface NotificationTime-End-->

**系统能力：** SystemCapability.Notification.Notification

## initialTime

```TypeScript
initialTime?: number
```

计时起始时间，用于设置实况窗中的计时起点。取值范围为全体非负整数。默认值为0。单位：毫秒。

**类型：** number

**起始版本：** 11

<!--Device-NotificationTime-initialTime?: int--><!--Device-NotificationTime-initialTime?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## isCountDown

```TypeScript
isCountDown?: boolean
```

是否为倒计时模式。默认为false。

- true：时间从initialTime开始递减显示。  
- false：时间从initialTime开始递增显示。

**类型：** boolean

**起始版本：** 11

<!--Device-NotificationTime-isCountDown?: boolean--><!--Device-NotificationTime-isCountDown?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## isInTitle

```TypeScript
isInTitle?: boolean
```

时间信息是否展示在通知标题中。默认为false。

- true：计时信息将嵌入标题区域展示。  
- false：计时信息在独立区域展示。

**类型：** boolean

**起始版本：** 11

<!--Device-NotificationTime-isInTitle?: boolean--><!--Device-NotificationTime-isInTitle?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## isPaused

```TypeScript
isPaused?: boolean
```

计时是否暂停。默认为false。

- true：计时暂停在当前值。  
- false：计时正常运行。

**类型：** boolean

**起始版本：** 11

<!--Device-NotificationTime-isPaused?: boolean--><!--Device-NotificationTime-isPaused?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

