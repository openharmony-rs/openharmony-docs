# NotificationProgress

描述通知进度，用于在实况窗中展示进度条信息。
> **说明：**  
>  
> 实际显示效果依赖于设备能力和通知中心UI样式。

**起始版本：** 11

<!--Device-unnamed-export interface NotificationProgress--><!--Device-unnamed-export interface NotificationProgress-End-->

**系统能力：** SystemCapability.Notification.Notification

## currentValue

```TypeScript
currentValue?: number
```

进度当前值。取值范围为全体非负整数。

**类型：** number

**起始版本：** 11

<!--Device-NotificationProgress-currentValue?: int--><!--Device-NotificationProgress-currentValue?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## isPercentage

```TypeScript
isPercentage?: boolean
```

是否按百分比展示进度。默认为false。

- true：进度以百分比形式展示。  
- false：进度以绝对值形式展示。

**类型：** boolean

**起始版本：** 11

<!--Device-NotificationProgress-isPercentage?: boolean--><!--Device-NotificationProgress-isPercentage?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## maxValue

```TypeScript
maxValue?: number
```

进度最大值。取值范围为全体非负整数。

**类型：** number

**起始版本：** 11

<!--Device-NotificationProgress-maxValue?: int--><!--Device-NotificationProgress-maxValue?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

