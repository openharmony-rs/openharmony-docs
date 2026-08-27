# SystemLiveViewSubscriber（系统接口）

系统实况窗订阅者。

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## onResponse

```TypeScript
onResponse?: (notificationId: number, buttonOptions: ButtonOptions) => void
```

点击按钮的回调。

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| notificationId | number | 是 |  |
| buttonOptions | ButtonOptions | 是 |  |
