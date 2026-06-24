# cancelAsBundle（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## cancelAsBundle

```TypeScript
function cancelAsBundle(
    id: number,
    representativeBundle: string,
    userId: number,
    callback: AsyncCallback<void>
  ): void
```

取消代理通知。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 通知ID。 |
| representativeBundle | string | 是 | 被代理应用的包名。 |
| userId | number | 是 | 用户ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 取消代理通知的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist. |
| [1600008](../../errorcode-universal.md#1600008-The) | The user does not exist. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// cancelAsBundle
let cancelAsBundleCallback = (err: BusinessError): void => {
    if (err) {
        console.error(`cancelAsBundle failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("cancelAsBundle success");
    }
}
// 被代理应用的包名
let representativeBundle: string = "com.example.demo";
// 用户ID，使用时需替换为真实的userId。
let userId: number = 100;
notificationManager.cancelAsBundle(0, representativeBundle, userId, cancelAsBundleCallback);

```


## cancelAsBundle

```TypeScript
function cancelAsBundle(id: number, representativeBundle: string, userId: number): Promise<void>
```

取消代理通知。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 通知ID。 |
| representativeBundle | string | 是 | 被代理应用的包名。 |
| userId | number | 是 | 用户ID。 |

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
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist. |
| [1600008](../../errorcode-universal.md#1600008-The) | The user does not exist. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 被代理应用的包名
let representativeBundle: string = "com.example.demo";
// 用户ID，使用时需替换为真实的userId。
let userId: number = 100;
notificationManager.cancelAsBundle(0, representativeBundle, userId).then(() => {
    console.info("cancelAsBundle success");
}).catch((err: BusinessError) => {
    console.error(`cancelAsBundle failed, code is ${err.code}, message is ${err.message}`);
});

```


## cancelAsBundle

```TypeScript
function cancelAsBundle(representativeBundle: BundleOption, id: number): Promise<void>
```

取消代理通知。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| representativeBundle | BundleOption | 是 | 被代理应用的包信息。 |
| id | number | 是 | 通知ID。 |

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
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist. |
| [1600008](../../errorcode-universal.md#1600008-The) | The user does not exist. |
| [1600012](../../errorcode-universal.md#1600012-No) | No memory space. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let representativeBundle: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
notificationManager.cancelAsBundle(representativeBundle, 1).then(() => {
    console.info("cancelAsBundle success");
}).catch((err: BusinessError) => {
    console.error(`cancelAsBundle failed, code is ${err.code}, message is ${err.message}`);
});

```

