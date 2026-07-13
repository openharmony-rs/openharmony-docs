# BundleNotificationStatistics（系统接口）

描述指定应用通知统计信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## bundle

```TypeScript
bundle: BundleOption
```

指定应用的包信息。

**类型：** BundleOption

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## lastTime

```TypeScript
lastTime: number
```

应用最后一次发布通知的时间。数据格式：时间戳。单位：ms。

**类型：** number

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## recentCount

```TypeScript
recentCount: number
```

应用最近7天发布的通知总量。

**类型：** number

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

