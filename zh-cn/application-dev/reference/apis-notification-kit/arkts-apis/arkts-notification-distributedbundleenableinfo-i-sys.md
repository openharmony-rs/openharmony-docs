# DistributedBundleEnableInfo（系统接口）

描述多设备协同的包信息。

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## bundleName

```TypeScript
bundleName: string
```

包名。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## enable

```TypeScript
enable?: boolean
```

是否支持跨设备协同，返回true表示支持，返回false表示不支持，默认为false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

应用程序的UID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

