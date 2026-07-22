# setGeofenceEnabled（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setGeofenceEnabled

```TypeScript
function setGeofenceEnabled(enabled: boolean): Promise<void>
```

设置地理围栏的启用状态。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setGeofenceEnabled(enabled: boolean): Promise<void>--><!--Device-notificationManager-function setGeofenceEnabled(enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置地理围栏开关。true表示开启地理围栏，false表示关闭地理围栏。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.setGeofenceEnabled(true).then(() => {
  hilog.info(0x0000, 'testTag', '%{public}s', "setGeofenceEnabled success");
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', '%{public}s',`setGeofenceEnabled failed, code is ${err.code}, message is ${err.message}`);
});

```

