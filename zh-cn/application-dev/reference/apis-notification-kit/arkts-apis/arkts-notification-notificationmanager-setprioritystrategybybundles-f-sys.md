# setPriorityStrategyByBundles（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setPriorityStrategyByBundles

```TypeScript
function setPriorityStrategyByBundles(strategies: Map<BundleOption, long>): Promise<void>
```

批量设置应用通知优先策略。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function setPriorityStrategyByBundles(strategies: Map<BundleOption, long>): Promise<void>--><!--Device-notificationManager-function setPriorityStrategyByBundles(strategies: Map<BundleOption, long>): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategies | Map&lt;BundleOption, long&gt; | 是 | 应用通知优先策略的键值对集合。与 PriorityStrategyStatus的枚举进行按位或运算得到值。 |

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
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const bundleOption : notificationManager.BundleOption = { bundle: 'bundleName', uid: 1000 };
let strategies: Map<notificationManager.BundleOption, number> = new Map([[bundleOption, notificationManager.PriorityStrategyStatus.STATUS_APPLICATION_DEFINED]]);
notificationManager.setPriorityStrategyByBundles(strategies).then(() => {
  hilog.info(0x0000, 'testTag', `setPriorityStrategyByBundles success`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'testTag', `setPriorityStrategyByBundles failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const bundleOption : notificationManager.BundleOption = { bundle: 'bundleName', uid: 1000 };
let strategies: Map<notificationManager.BundleOption, long> =
    new Map<notificationManager.BundleOption, long>([[bundleOption, notificationManager.PriorityStrategyStatus.STATUS_APPLICATION_DEFINED]]);
notificationManager.setPriorityStrategyByBundles(strategies).then(() => {
    console.info(`setPriorityStrategyByBundles success`);
}).catch((err: Error) => {
    let error: BusinessError = err as BusinessError;
    console.error(`setPriorityStrategyByBundles failed, code is ${error.code}, message is ${error.message}`);
});
```

