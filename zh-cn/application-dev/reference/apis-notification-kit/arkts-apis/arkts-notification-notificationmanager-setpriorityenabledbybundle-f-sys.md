# setPriorityEnabledByBundle（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setPriorityEnabledByBundle

```TypeScript
function setPriorityEnabledByBundle(bundle: BundleOption, enableStatus: PriorityEnableStatus): Promise<void>
```

设置应用通知优先级开关。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setPriorityEnabledByBundle(bundle: BundleOption, enableStatus: PriorityEnableStatus): Promise<void>--><!--Device-notificationManager-function setPriorityEnabledByBundle(bundle: BundleOption, enableStatus: PriorityEnableStatus): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| enableStatus | [PriorityEnableStatus](arkts-notification-notificationmanager-priorityenablestatus-e-sys.md) | 是 | 应用通知优先级开关状态。&lt;br&gt; - DISABLE：不允许设置为优先通知。&lt;br&gt; - ENABLE_BY_INTELLIGENT：允 许经智能识别、用户关键词匹配、应用规则匹配等方式设置为优先通知。&lt;br&gt; - ENABLE：应用通知均设置为优先通知。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const bundleOption : notificationManager.BundleOption = { bundle: 'bundleName', uid: 0 };
notificationManager.setPriorityEnabledByBundle(bundleOption, notificationManager.PriorityEnableStatus.ENABLE).then(() => {
  hilog.info(0x0000, 'testTag', `setPriorityEnabledByBundle success`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', `setPriorityEnabledByBundle failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const bundleOption : notificationManager.BundleOption = { bundle: 'bundleName', uid: 0 };
notificationManager.setPriorityEnabledByBundle(bundleOption, notificationManager.PriorityEnableStatus.ENABLE).then(() => {
  console.info(`setPriorityEnabledByBundle success`);
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`setPriorityEnabledByBundle failed, code is ${error.code}, message is ${error.message}`);
});
```

