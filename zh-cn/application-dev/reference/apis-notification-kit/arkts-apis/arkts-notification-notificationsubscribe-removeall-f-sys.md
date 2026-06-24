# removeAll（系统接口）

## 导入模块

```TypeScript
import { notificationSubscribe } from '@ohos.notificationSubscribe';
```

## removeAll

```TypeScript
function removeAll(bundle: BundleOption, callback: AsyncCallback<void>): void
```

删除指定应用的所有通知。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 删除指定应用的所有通知回调函数。 |

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

let removeAllCallback = (err: BusinessError) => {
  if (err) {
    console.error(`removeAll failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("removeAll success");
  }
}
let bundle: notificationSubscribe.BundleOption = {
  bundle: "bundleName1",
};
notificationSubscribe.removeAll(bundle, removeAllCallback);

```


## removeAll

```TypeScript
function removeAll(callback: AsyncCallback<void>): void
```

删除所有通知。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 删除所有通知回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let removeAllCallback = (err: BusinessError) => {
    if (err) {
        console.error(`removeAll failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("removeAll success");
    }
}
notificationSubscribe.removeAll(removeAllCallback);

```


## removeAll

```TypeScript
function removeAll(userId: number, callback: AsyncCallback<void>): void
```

删除指定用户下的所有通知。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 删除指定用户所有通知回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600008](../../errorcode-universal.md#1600008-The) | The user does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let removeAllCallback = (err: BusinessError) => {
  if (err) {
    console.error(`removeAll failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("removeAll success");
  }
}
// 用户ID，使用时需替换为真实的userId。
let userId: number = 1;
notificationSubscribe.removeAll(userId, removeAllCallback);

```


## removeAll

```TypeScript
function removeAll(userId: number): Promise<void>
```

删除指定用户下的所有通知。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600008](../../errorcode-universal.md#1600008-The) | The user does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 1;
notificationSubscribe.removeAll(userId).then(() => {
  console.info("removeAll success");
}).catch((err: BusinessError) => {
  console.error(`removeAll fail: ${JSON.stringify(err)}`);
});

```


## removeAll

```TypeScript
function removeAll(bundle?: BundleOption): Promise<void>
```

删除指定应用的所有通知。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 否 | 指定应用的包信息。默认为空，表示删除所有通知。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

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

// 不指定应用时，删除所有通知
notificationSubscribe.removeAll().then(() => {
  console.info("removeAll success");
}).catch((err: BusinessError) => {
  console.error(`removeAll fail: ${JSON.stringify(err)}`);
});

```

