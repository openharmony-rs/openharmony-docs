# NotificationSortingMap（系统接口）

提供有关已订阅的所有通知中的活动通知的排序信息。

> **说明：**  
>  
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
>  
> 本模块为系统接口。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationSortingMap--><!--Device-unnamed-export interface NotificationSortingMap-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## sortedHashCode

```TypeScript
readonly sortedHashCode: Array<string>
```

通知排序的HashCode。

**类型：** Array<string>

**起始版本：** 7

<!--Device-NotificationSortingMap-readonly sortedHashCode: Array<string>--><!--Device-NotificationSortingMap-readonly sortedHashCode: Array<string>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## sortings

```TypeScript
readonly sortings: Record<string, NotificationSorting>
```

通知排序信息。

**类型：** Record<string, NotificationSorting>

**起始版本：** 7

<!--Device-NotificationSortingMap-readonly sortings: Record<string, NotificationSorting>--><!--Device-NotificationSortingMap-readonly sortings: Record<string, NotificationSorting>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

