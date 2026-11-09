# getNotificationSwitchLimitedBundles（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getNotificationSwitchLimitedBundles

```TypeScript
function getNotificationSwitchLimitedBundles(userId: number): Promise<Map<string, boolean>>
```

获取通知开关受限的应用列表。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function getNotificationSwitchLimitedBundles(userId: int): Promise<Map<string, boolean>>--><!--Device-notificationManager-function getNotificationSwitchLimitedBundles(userId: int): Promise<Map<string, boolean>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。<br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Map&lt;string, boolean&gt;&gt; | Promise对象，返回应用通知开关状态的键值对集合。<br> - true: 表示开启。<br> - false: 表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600008](../errorcode-notification.md#1600008-用户不存在) | The user does not exist. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
