# cancel（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## cancel

```TypeScript
function cancel(representativeBundle: BundleOption, id: number): Promise<void>
```

代理取消当前用户其他应用的通知。使用Promise异步回调。

需要当前应用与其他应用存在代理关系，或者当前应用有ohos.permission.NOTIFICATION_AGENT_CONTROLLER权限。

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| representativeBundle | BundleOption | 是 | 应用的包信息。 |
| id | number | 是 | 通知ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist. |
| [1600012](../../errorcode-universal.md#1600012-No) | No memory space. |
| [1600017](../../errorcode-universal.md#1600017-There) | There is no corresponding agent relationship configuration. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundle: notificationManager.BundleOption = {
  bundle: "bundleName"
};
let id: number = 1;
notificationManager.cancel(bundle, id).then(() => {
  console.info("cancel success");
}).catch((err: BusinessError) => {
  console.error(`cancel failed, code is ${err.code}, message is ${err.message}`);
});

```

