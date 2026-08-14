# setPriorityIntelligentEnabled（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setPriorityIntelligentEnabled

```TypeScript
function setPriorityIntelligentEnabled(enable: boolean): Promise<void>
```

设置优先通知智能服务使能状态。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function setPriorityIntelligentEnabled(enable: boolean): Promise<void>--><!--Device-notificationManager-function setPriorityIntelligentEnabled(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 优先通知智能服务使能状态。&lt;br&gt; - true：优先通知智能服务为打开状态。&lt;br&gt; - false：优先通知智能服务为关闭状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

notificationManager.setPriorityIntelligentEnabled(false).then(() => {
  hilog.info(0x0000, 'testTag', `setPriorityIntelligentEnabled success`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', `setPriorityIntelligentEnabled failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.setPriorityIntelligentEnabled(false).then(() => {
    console.info(`setPriorityIntelligentEnabled success`);
}).catch((err: Error) => {
    let error: BusinessError = err as BusinessError;
    console.error(`setPriorityIntelligentEnabled failed, code is ${error.code}, message is ${error.message}`);
});
```

