# NotificationFilter（系统接口）

描述查询普通实况窗时的筛选条件。

**起始版本：** 11

<!--Device-unnamed-export interface NotificationFilter--><!--Device-unnamed-export interface NotificationFilter-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## bundle

```TypeScript
bundle: BundleOption
```

实况通知的包信息。

**类型：** BundleOption

**起始版本：** 11

<!--Device-NotificationFilter-bundle: BundleOption--><!--Device-NotificationFilter-bundle: BundleOption-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## extraInfoKeys

```TypeScript
extraInfoKeys?: Array<string>
```

筛选附加信息的键值列表。不填表示查询所有的附加信息。

**类型：** Array<string>

**起始版本：** 11

<!--Device-NotificationFilter-extraInfoKeys?: Array<string>--><!--Device-NotificationFilter-extraInfoKeys?: Array<string>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## notificationKey

```TypeScript
notificationKey: notificationSubscribe.NotificationKey
```

通知信息，包含通知ID和通知标签。

**类型：** notificationSubscribe.NotificationKey

**起始版本：** 11

<!--Device-NotificationFilter-notificationKey: notificationSubscribe.NotificationKey--><!--Device-NotificationFilter-notificationKey: notificationSubscribe.NotificationKey-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

