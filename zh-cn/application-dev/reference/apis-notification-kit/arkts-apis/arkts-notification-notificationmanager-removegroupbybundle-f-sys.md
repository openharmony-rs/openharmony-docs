# removeGroupByBundle（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string, callback: AsyncCallback<void>): void
```

删除指定应用的指定组下的通知。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 应用的包信息。 |
| groupName | string | 是 | 通知组名称。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 删除指定应用指定组下通知的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let removeGroupByBundleCallback = (err: BusinessError): void => {
    if (err) {
        console.error(`removeGroupByBundle failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("removeGroupByBundle success");
    }
}

let bundleOption: notificationManager.BundleOption = { bundle: "Bundle" };
let groupName: string = "GroupName";

notificationManager.removeGroupByBundle(bundleOption, groupName, removeGroupByBundleCallback);

```


## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>
```

删除指定应用的指定组下的通知。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 应用的包信息。 |
| groupName | string | 是 | 通知组名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleOption: notificationManager.BundleOption = { bundle: "Bundle" };
let groupName: string = "GroupName";

notificationManager.removeGroupByBundle(bundleOption, groupName).then(() => {
    console.info("removeGroupByBundle success");
}).catch((err: BusinessError) => {
    console.error(`removeGroupByBundle failed, code is ${err.code}, message is ${err.message}`);
});

```

