# SystemLiveViewSubscriber（系统接口）

系统实况窗订阅者。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-notificationManager-export interface SystemLiveViewSubscriber--><!--Device-notificationManager-export interface SystemLiveViewSubscriber-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## onResponse

```TypeScript
onResponse?: (notificationId: int, buttonOptions: ButtonOptions) => void
```

点击按钮的回调。

**类型：** (notificationId: int, buttonOptions: ButtonOptions) =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemLiveViewSubscriber-onResponse?: (notificationId: int, buttonOptions: ButtonOptions) => void--><!--Device-SystemLiveViewSubscriber-onResponse?: (notificationId: int, buttonOptions: ButtonOptions) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

