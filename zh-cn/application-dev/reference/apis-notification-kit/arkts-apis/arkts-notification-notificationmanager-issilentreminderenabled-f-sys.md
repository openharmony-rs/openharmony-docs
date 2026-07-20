# isSilentReminderEnabled（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="issilentreminderenabled"></a>
## isSilentReminderEnabled

```TypeScript
function isSilentReminderEnabled(bundle: BundleOption): Promise<SwitchState>
```

查询静默提醒的开关状态。使用Promise进行异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isSilentReminderEnabled(bundle: BundleOption): Promise<SwitchState>--><!--Device-notificationManager-function isSilentReminderEnabled(bundle: BundleOption): Promise<SwitchState>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SwitchState&gt; | Promise对象，返回指定应用的通知静默提醒开关状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundle: notificationManager.BundleOption = {
    bundle: "bundleName1",
};
notificationManager.isSilentReminderEnabled(bundle).then((data: notificationManager.SwitchState) => {
    hilog.info(0x0000, 'testTag', '%{public}s', `isSilentReminderEnabled success, switchState:  ${JSON.stringify(data)}.`);
}).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', '%{public}s', `isSilentReminderEnabled failed, code is ${err.code}, message is ${err.message}`);
});

```

