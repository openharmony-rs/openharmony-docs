# NotificationSorting（系统接口）

提供有关活动通知的排序信息。
> **说明：**  
>  
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
>  
> 本模块为系统接口。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationSorting--><!--Device-unnamed-export interface NotificationSorting-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## hashCode

```TypeScript
readonly hashCode: string
```

通知唯一标识。

**类型：** string

**起始版本：** 7

<!--Device-NotificationSorting-readonly hashCode: string--><!--Device-NotificationSorting-readonly hashCode: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## ranking

```TypeScript
readonly ranking: number
```

通知级别，不设置则根据通知渠道类型有默认值。

**类型：** number

**起始版本：** 7

<!--Device-NotificationSorting-readonly ranking: long--><!--Device-NotificationSorting-readonly ranking: long-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## slot

```TypeScript
readonly slot: NotificationSlot
```

通道类型。

**类型：** NotificationSlot

**起始版本：** 7

<!--Device-NotificationSorting-readonly slot: NotificationSlot--><!--Device-NotificationSorting-readonly slot: NotificationSlot-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

