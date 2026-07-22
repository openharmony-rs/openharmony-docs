# isGeofenceEnabled

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isGeofenceEnabled

```TypeScript
function isGeofenceEnabled(): Promise<boolean>
```

检查地理围栏功能是否已启用。使用Promise异步回调。

**起始版本：** 23

<!--Device-notificationManager-function isGeofenceEnabled(): Promise<boolean>--><!--Device-notificationManager-function isGeofenceEnabled(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回地理围栏开关状态的Promise对象。返回true表示地理围栏功能已启用，返回false表示地理围栏功能未启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.isGeofenceEnabled().then((data: boolean) => {
  hilog.info(0x0000, 'testTag', '%{public}s', `isGeofenceEnabled success, enabled:  ${JSON.stringify(data)}.`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', '%{public}s',`isGeofenceEnabled failed, code is ${err.code}, message is ${err.message}`);
});

```

