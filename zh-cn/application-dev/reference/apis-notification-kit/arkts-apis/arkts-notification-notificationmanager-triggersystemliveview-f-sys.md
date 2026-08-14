# triggerSystemLiveView（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## triggerSystemLiveView

```TypeScript
function triggerSystemLiveView(bundle: BundleOption, notificationId: int, buttonOptions: ButtonOptions): Promise<void>
```

触发系统实况窗。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function triggerSystemLiveView(bundle: BundleOption, notificationId: int, buttonOptions: ButtonOptions): Promise<void>--><!--Device-notificationManager-function triggerSystemLiveView(bundle: BundleOption, notificationId: int, buttonOptions: ButtonOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| notificationId | int | 是 | 通知ID。 |
| buttonOptions | ButtonOptions | 是 | 按钮信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 包信息
let bundle: notificationManager.BundleOption = {
    bundle: 'bundleName1',
};
// 通知ID
let notificationId = 1;
// 按钮信息
let buttonOptions: notificationManager.ButtonOptions = {
    buttonName: 'buttonName1',
}
notificationManager.triggerSystemLiveView(bundle, notificationId, buttonOptions).then(() => {
  console.info('triggerSystemLiveView success');
}).catch((err: BusinessError) => {
  console.error(`triggerSystemLiveView failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 包信息
let bundle: notificationManager.BundleOption = {
    // 需根据实际情况进行替换
    bundle: 'bundleName1',
};
// 通知ID
let notificationId: int = 1;
// 按钮信息
let buttonOptions: notificationManager.ButtonOptions = {
    // 需根据实际情况进行替换
    buttonName: 'buttonName1',
}
notificationManager.triggerSystemLiveView(bundle, notificationId, buttonOptions).then(() => {
  console.info('triggerSystemLiveView success');
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`triggerSystemLiveView failed, code is ${error.code}, message is ${error.message}`);
});
```

