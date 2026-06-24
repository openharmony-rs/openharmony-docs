# getSlots

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## getSlots

```TypeScript
function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void
```

获取当前应用的所有通知渠道。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;NotificationSlot&gt;&gt; | 是 | 回调函数。当获取通知渠道成功，err为undefined，data为获取到的NotificationSlot<br/>数组，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// getSlots回调
let getSlotsCallback = (err: BusinessError, data: Array<notificationManager.NotificationSlot>): void => {
  if (err) {
    console.error(`Failed to get slots. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting slots, data is ${JSON.stringify(data)}`);
  }
}
notificationManager.getSlots(getSlotsCallback);

```


## getSlots

```TypeScript
function getSlots(): Promise<Array<NotificationSlot>>
```

获取当前应用的所有通知渠道。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;NotificationSlot&gt;&gt; | Promise对象，返回通知渠道对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getSlots().then((data: Array<notificationManager.NotificationSlot>) => {
  console.info(`Succeeded in getting slots, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get slots. Code is ${err.code}, message is ${err.message}`);
});

```

