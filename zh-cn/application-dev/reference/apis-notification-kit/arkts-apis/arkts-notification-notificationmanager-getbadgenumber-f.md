# getBadgeNumber

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getBadgeNumber

```TypeScript
function getBadgeNumber(): Promise<number>
```

获取当前应用角标数量。使用Promise异步回调。

用于查询当前应用桌面图标上显示的角标数字。

**起始版本：** 22

<!--Device-notificationManager-function getBadgeNumber(): Promise<long>--><!--Device-notificationManager-function getBadgeNumber(): Promise<long>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回当前应用角标数量。（查询的角标数量与当前应用通知开关，桌面角标开关是否开启无关） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getBadgeNumber().then((badgeNumber: number) => {
  console.info(`Succeeded in getting badge number, badgeNumber is ${JSON.stringify(badgeNumber)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get badge number. Code is ${err.code}, message is ${err.message}`);
});

```

