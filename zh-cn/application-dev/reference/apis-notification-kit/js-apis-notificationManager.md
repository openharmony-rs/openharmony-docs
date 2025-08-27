# @ohos.notificationManager (NotificationManager模块)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->

本模块提供通知管理的能力，包括发布、更新、取消通知，创建、获取、移除通知渠道，获取发布通知应用的使能状态，获取通知的相关信息等。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { notificationManager } from '@kit.NotificationKit';
```

## notificationManager.publish

publish(request: NotificationRequest, callback: AsyncCallback\<void\>): void

发布通知。使用callback异步回调。

如果新发布通知与已发布通知的ID相同，且label相同，则新通知将取代原有通知。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                                        | 必填 | 说明                                        |
| -------- | ------------------------------------------- | ---- | ------------------------------------------- |
| request  | [NotificationRequest](js-apis-inner-notification-notificationRequest.md#notificationrequest-1) | 是   | 用于设置要发布通知的内容和相关配置信息。 |
| callback | AsyncCallback\<void\>                       | 是   | 发布通知的回调方法。                        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[通知错误码](./errorcode-notification.md)、[HTTP错误码](../apis-network-kit/errorcode-net-http.md)。

| 错误码ID | 错误信息                                              |
| -------- | ---------------------------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.    | 
| 1600001  | Internal error.                                      |
| 1600002  | Marshalling or unmarshalling error.                  |
| 1600003  | Failed to connect to the service.                    |
| 1600004  | Notification disabled.                               |
| 1600005  | Notification slot disabled.                          |
| 1600007  | The notification does not exist.                     |
| 1600009  | The notification sending frequency reaches the upper limit.            |
| 1600012  | No memory space.                                     |
| 1600014  | No permission.                                       |
| 1600015  | The current notification status does not support duplicate configurations. |
| 1600016  | The notification version for this update is too low. |
| 1600020  | The application is not allowed to send notifications due to permission settings. |
| 2300007  | Network unreachable.                                 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// publish回调
let publishCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in publishing notification.`);
  }
}
// 通知Request对象
let notificationRequest: notificationManager.NotificationRequest = {
  id: 1,
  content: {
    notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "test_title",
      text: "test_text",
      additionalText: "test_additionalText"
    }
  }
};
notificationManager.publish(notificationRequest, publishCallback);
```

## notificationManager.publish

publish(request: NotificationRequest): Promise\<void\>

发布通知。使用Promise异步回调。

如果新发布通知与已发布通知的ID相同，且label相同，则新通知将取代原有通知。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                                        | 必填 | 说明                                        |
| -------- | ------------------------------------------- | ---- | ------------------------------------------- |
| request  | [NotificationRequest](js-apis-inner-notification-notificationRequest.md#notificationrequest-1) | 是   | 用于设置要发布通知的内容和相关配置信息。 |

**返回值：**

| 类型     | 说明 | 
| ------- |--|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[通知错误码](./errorcode-notification.md)、[HTTP错误码](../apis-network-kit/errorcode-net-http.md)。

| 错误码ID | 错误信息                                              |
| -------- | ---------------------------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.    | 
| 1600001  | Internal error.                                      |
| 1600002  | Marshalling or unmarshalling error.                  |
| 1600003  | Failed to connect to the service.                    |
| 1600004  | Notification disabled.                               |
| 1600005  | Notification slot disabled.                          |
| 1600007  | The notification does not exist.                     |
| 1600009  | The notification sending frequency reaches the upper limit.            |
| 1600012  | No memory space.                                     |
| 1600014  | No permission.                                       |
| 1600015  | The current notification status does not support duplicate configurations. |
| 1600016  | The notification version for this update is too low. |
| 1600020  | The application is not allowed to send notifications due to permission settings. |
| 2300007  | Network unreachable.                                 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 通知Request对象
let notificationRequest: notificationManager.NotificationRequest = {
  id: 1,
  content: {
    notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "test_title",
      text: "test_text",
      additionalText: "test_additionalText"
    }
  }
};
notificationManager.publish(notificationRequest).then(() => {
  console.info(`Succeeded in publishing notification.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
});

```

## notificationManager.cancel

cancel(id: number, label: string, callback: AsyncCallback\<void\>): void

通过通知ID和通知标签取消已发布的通知。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| id       | number                | 是   | 通知ID。               |
| label    | string                | 是   | 通知标签。             |
| callback | AsyncCallback\<void\> | 是   | 表示被指定通知的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600007  | The notification does not exist.      |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// cancel回调
let cancelCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling notification.`);
  } 
}
notificationManager.cancel(0, "label", cancelCallback);
```

## notificationManager.cancel

cancel(id: number, label?: string): Promise\<void\>

通过通知ID和通知标签取消已发布的通知，若label为空表示取消与指定通知ID相匹配的已发布通知。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名  | 类型   | 必填 | 说明     |
| ----- | ------ | ---- | -------- |
| id    | number | 是   | 通知ID。   |
| label | string | 否   | 通知标签，默认为空。 |

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600007  | The notification does not exist.      |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.cancel(0).then(() => {
  console.info(`Succeeded in canceling notification.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to cancel notification. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.cancel

cancel(id: number, callback: AsyncCallback\<void\>): void

取消与指定通知ID相匹配的已发布通知。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| id       | number                | 是   | 通知ID。               |
| callback | AsyncCallback\<void\> | 是   | 表示被指定通知的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600007  | The notification does not exist.      |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// cancel回调
let cancelCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling notification.`);
  }
}
notificationManager.cancel(0, cancelCallback);
```

## notificationManager.cancelAll

cancelAll(callback: AsyncCallback\<void\>): void

取消当前应用所有已发布的通知。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| callback | AsyncCallback\<void\> | 是   | 表示被指定通知的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// cancel回调
let cancelAllCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel all notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling all notification.`);
  }
}
notificationManager.cancelAll(cancelAllCallback);
```

## notificationManager.cancelAll

cancelAll(): Promise\<void\>

取消当前应用所有已发布的通知。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.cancelAll().then(() => {
  console.info(`Succeeded in canceling all notification.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to cancel all notification. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.addSlot

addSlot(type: SlotType, callback: AsyncCallback\<void\>): void

创建指定类型的通知渠道。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                  | 必填 | 说明                   |
| -------- | --------------------- | ---- | ---------------------- |
| type     | [SlotType](#slottype)              | 是   | 要创建的通知渠道的类型。 |
| callback | AsyncCallback\<void\> | 是   | 表示被指定通道的回调方法。   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600012  | No memory space.                    |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// addSlot回调
let addSlotCallBack = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to add slot. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in adding slot.`);
  }
}
notificationManager.addSlot(notificationManager.SlotType.SOCIAL_COMMUNICATION, addSlotCallBack);
```

## notificationManager.addSlot

addSlot(type: SlotType): Promise\<void\>

创建指定类型的通知渠道。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型     | 必填 | 说明                   |
| ---- | -------- | ---- | ---------------------- |
| type | [SlotType](#slottype) | 是   | 要创建的通知渠道的类型。 |

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600012  | No memory space.                    |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.addSlot(notificationManager.SlotType.SOCIAL_COMMUNICATION).then(() => {
  console.info(`Succeeded in adding slot.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to add slot. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.getSlot

getSlot(slotType: SlotType, callback: AsyncCallback\<NotificationSlot\>): void

获取一个指定类型的通知渠道。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                              | 必填 | 说明                                                        |
| -------- | --------------------------------- | ---- | ----------------------------------------------------------- |
| slotType | [SlotType](#slottype)                          | 是   | 通知渠道类型，例如社交通信、服务提醒、内容咨询等类型。 |
| callback | AsyncCallback\<[NotificationSlot](js-apis-inner-notification-notificationSlot.md)\> | 是   | 表示被指定通道的回调方法。                                        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// getSlot回调
let getSlotCallback = (err: BusinessError, data: notificationManager.NotificationSlot): void => {
  if (err) {
    console.error(`Failed to get slot. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
  }
}
let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.getSlot(slotType, getSlotCallback);
```

## notificationManager.getSlot

getSlot(slotType: SlotType): Promise\<NotificationSlot\>

获取一个指定类型的通知渠道。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型     | 必填 | 说明                                                        |
| -------- | -------- | ---- | ----------------------------------------------------------- |
| slotType | [SlotType](#slottype) | 是   | 通知渠道类型，例如社交通信、服务提醒、内容咨询等类型。 |

**返回值：**

| 类型                                                        | 说明                                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| Promise\<[NotificationSlot](js-apis-inner-notification-notificationSlot.md)\> | 以Promise形式返回获取一个通知渠道。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.getSlot(slotType).then((data: notificationManager.NotificationSlot) => {
  console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get slot. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.getSlots

getSlots(callback: AsyncCallback\<Array\<NotificationSlot>>): void

获取此应用程序的所有通知渠道。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                              | 必填 | 说明                 |
| -------- | --------------------------------- | ---- | -------------------- |
| callback | AsyncCallback\<Array\<[NotificationSlot](js-apis-inner-notification-notificationSlot.md)\>\> | 是   | 以callback形式返回获取此应用程序的所有通知渠道的结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。


| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
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

## notificationManager.getSlots

getSlots(): Promise\<Array\<NotificationSlot>>

获取此应用程序的所有通知渠道。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型                                                        | 说明                                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| Promise\<Array\<[NotificationSlot](js-apis-inner-notification-notificationSlot.md)\>\> | 以Promise形式返回获取此应用程序的所有通知渠道的结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getSlots().then((data: Array<notificationManager.NotificationSlot>) => {
  console.info(`Succeeded in getting slots, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get slots. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.removeSlot

removeSlot(slotType: SlotType, callback: AsyncCallback\<void\>): void

删除此应用程序指定类型的通知渠道。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                  | 必填 | 说明                                                        |
| -------- | --------------------- | ---- | ----------------------------------------------------------- |
| slotType | [SlotType](#slottype)              | 是   | 通知渠道类型，例如社交通信、服务提醒、内容咨询等类型。 |
| callback | AsyncCallback\<void\> | 是   | 表示被指定通道的回调方法。                                        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// removeSlot回调
let removeSlotCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to remove slot. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in removing slot.`);
  }
}
let slotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.removeSlot(slotType, removeSlotCallback);
```

## notificationManager.removeSlot

removeSlot(slotType: SlotType): Promise\<void\>

删除此应用程序指定类型的通知渠道。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型     | 必填 | 说明                                                        |
| -------- | -------- | ---- | ----------------------------------------------------------- |
| slotType | [SlotType](#slottype) | 是   | 通知渠道类型，例如社交通信、服务提醒、内容咨询等类型。 |

**返回值：**

| 类型      | 说明        | 
|---------|-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.removeSlot(slotType).then(() => {
  console.info(`Succeeded in removing slot.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to remove slot. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.removeAllSlots

removeAllSlots(callback: AsyncCallback\<void\>): void

删除此应用程序所有通知渠道。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| callback | AsyncCallback\<void\> | 是   | 表示被指定通道的回调方法。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let removeAllSlotsCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to remove all slots. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in removing all slots.`);
  }
}
notificationManager.removeAllSlots(removeAllSlotsCallback);
```

## notificationManager.removeAllSlots

removeAllSlots(): Promise\<void\>

删除此应用程序所有通知渠道。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型      | 说明        | 
|---------|-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.removeAllSlots().then(() => {
  console.info(`Succeeded in removing all slots.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to remove all slots. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.isNotificationEnabled<sup>11+</sup>

isNotificationEnabled(callback: AsyncCallback\<boolean\>): void

获取通知使能状态。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                  | 必填 | 说明                     |
| -------- | --------------------- | ---- | ------------------------ |
| callback | AsyncCallback\<boolean\> | 是   | 回调函数。返回true，表示允许发布通知；返回false，表示禁止发布通知；调用失败返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[通知错误码](./errorcode-notification.md)、[包管理子系统通用错误码](../../reference/apis-ability-kit/errorcode-bundle.md)。

| 错误码ID | 错误信息                                  |
| -------- | ---------------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      |
| 1600001  | Internal error.                          |
| 1600002  | Marshalling or unmarshalling error.      |
| 1600003  | Failed to connect to the service.               |
| 1600008  | The user does not exist.                   |
| 17700001 | The specified bundle name was not found. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let isNotificationEnabledCallback = (err: BusinessError, data: boolean): void => {
  if (err) {
    console.error(`isNotificationEnabled failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`isNotificationEnabled success, data is ${JSON.stringify(data)}`);
  }
}

notificationManager.isNotificationEnabled(isNotificationEnabledCallback);
```

## notificationManager.isNotificationEnabled<sup>11+</sup>

isNotificationEnabled(): Promise\<boolean\>

获取通知使能状态。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型                                                        | 说明                                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| Promise\<boolean\> | 以Promise形式返回获取通知使能状态的结果（true：使能，false：禁止）。 |

**错误码：**

以下错误码的详细介绍请参见[通知错误码](./errorcode-notification.md)、[包管理子系统通用错误码](../../reference/apis-ability-kit/errorcode-bundle.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 1600001  | Internal error.                          |
| 1600002  | Marshalling or unmarshalling error.      |
| 1600003  | Failed to connect to the service.               |
| 1600008  | The user does not exist.                   |
| 17700001 | The specified bundle name was not found. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.isNotificationEnabled().then((data: boolean) => {
  console.info(`isNotificationEnabled success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`isNotificationEnabled failed, code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.isNotificationEnabledSync<sup>12+</sup>

isNotificationEnabledSync(): boolean

同步获取通知使能状态。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型                                                        | 说明                                                     |
| ----------------------------------------------------------- |--------------------------------------------------------- |
| boolean | 返回获取通知使能状态的结果。返回true，表示通知使能状态为开；返回false，表示通知使能状态为关。 |

**错误码：**

以下错误码的详细介绍请参见[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                                 |
| -------- | ---------------------------------------- |
| 1600001  | Internal error.                          |
| 1600002  | Marshalling or unmarshalling error.      |
| 1600003  | Failed to connect to the service.               |

**示例：**

```ts
let enabled = notificationManager.isNotificationEnabledSync();
console.info(`isNotificationEnabledSync success, data is : ${JSON.stringify(enabled)}`);
```

## notificationManager.setBadgeNumber<sup>10+</sup>

setBadgeNumber(badgeNumber: number): Promise\<void\>

设定角标个数，在应用的桌面图标上呈现。使用Promise异步回调。

当角标设定个数取值小于或等于0时，表示清除角标。取值大于99时，通知角标将显示99+。

该接口不支持wearable设备。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名      | 类型   | 必填 | 说明       |
| ----------- | ------ | ---- | ---------- |
| badgeNumber | number | 是   | 角标个数。 |

**返回值：**

| 类型      | 说明        | 
|---------|-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 801 | Capability not supported. |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600012  | No memory space.                          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let badgeNumber: number = 10;
notificationManager.setBadgeNumber(badgeNumber).then(() => {
  console.info(`Succeeded in setting badge number.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set badge number. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.setBadgeNumber<sup>10+</sup>

setBadgeNumber(badgeNumber: number, callback: AsyncCallback\<void\>): void

设定角标个数，在应用的桌面图标上呈现。使用callback异步回调。

当角标设定个数取值小于或等于0时，表示清除角标。取值大于99时，通知角标将显示99+。

该接口不支持wearable设备。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名      | 类型                  | 必填 | 说明               |
| ----------- | --------------------- | ---- | ------------------ |
| badgeNumber | number                | 是   | 角标个数。         |
| callback    | AsyncCallback\<void\> | 是   | 设定角标回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 801 | Capability not supported. |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600012  | No memory space.                          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let setBadgeNumberCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to set badge number. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in setting badge number.`);
  }
}
let badgeNumber: number = 10;
notificationManager.setBadgeNumber(badgeNumber, setBadgeNumberCallback);
```

## notificationManager.getActiveNotificationCount

getActiveNotificationCount(callback: AsyncCallback\<number\>): void

获取当前应用未删除的通知数。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                   | 必填 | 说明                   |
| -------- | ---------------------- | ---- | ---------------------- |
| callback | AsyncCallback\<number\> | 是   | 获取未删除通知数回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let getActiveNotificationCountCallback = (err: BusinessError, data: number): void => {
  if (err) {
    console.error(`Failed to get active notification count. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting active notification count, data is ${JSON.stringify(data)}`);
  }
}

notificationManager.getActiveNotificationCount(getActiveNotificationCountCallback);
```

## notificationManager.getActiveNotificationCount

getActiveNotificationCount(): Promise\<number\>

获取当前应用未删除的通知数。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型              | 说明                                        |
| ----------------- | ------------------------------------------- |
| Promise\<number\> | 以Promise形式返回获取当前应用未删除通知数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getActiveNotificationCount().then((data: number) => {
  console.info(`Succeeded in getting active notification count, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get active notification count. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.getActiveNotifications

getActiveNotifications(callback: AsyncCallback\<Array\<NotificationRequest>>): void

获取当前应用未删除的通知列表。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                           |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | AsyncCallback\<Array\<[NotificationRequest](js-apis-inner-notification-notificationRequest.md#notificationrequest-1)>> | 是   | 获取当前应用通知列表回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let getActiveNotificationsCallback = (err: BusinessError, data: Array<notificationManager.NotificationRequest>): void => {
  if (err) {
    console.error(`Failed to get active notifications. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting active notifications, data is ${JSON.stringify(data)}`);
  }
}
notificationManager.getActiveNotifications(getActiveNotificationsCallback);
```

## notificationManager.getActiveNotifications

getActiveNotifications(): Promise\<Array\<NotificationRequest\>\>

获取当前应用未删除的通知列表。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型                                                         | 说明                                    |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise\<Array\<[NotificationRequest](js-apis-inner-notification-notificationRequest.md#notificationrequest-1)\>\> | 以Promise形式返回获取当前应用通知列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getActiveNotifications().then((data: Array<notificationManager.NotificationRequest>) => {
  console.info(`Succeeded in getting active notifications, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get active notifications. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.cancelGroup

cancelGroup(groupName: string, callback: AsyncCallback\<void\>): void

取消本应用指定组下的通知。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名      | 类型                  | 必填 | 说明                         |
| --------- | --------------------- | ---- | ---------------------------- |
| groupName | string                | 是   | 通知组名称，此名称需要在发布通知时通过[NotificationRequest](js-apis-inner-notification-notificationRequest.md#notificationrequest-1)对象指定。 |
| callback  | AsyncCallback\<void\> | 是   | 取消本应用指定组下通知的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let cancelGroupCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel group. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling group.`);
  }
}
let groupName: string = "GroupName";
notificationManager.cancelGroup(groupName, cancelGroupCallback);
```

## notificationManager.cancelGroup

cancelGroup(groupName: string): Promise\<void\>

取消本应用指定组下的通知。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名      | 类型   | 必填 | 说明           |
| --------- | ------ | ---- | -------------- |
| groupName | string | 是   | 通知组名称，此名称需要在发布通知时通过[NotificationRequest](js-apis-inner-notification-notificationRequest.md#notificationrequest-1)对象指定。 |

**返回值：**

| 类型      | 说明        | 
|---------|-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let groupName: string = "GroupName";
notificationManager.cancelGroup(groupName).then(() => {
  console.info(`Succeeded in canceling group.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to cancel group. Code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.isSupportTemplate

isSupportTemplate(templateName: string, callback: AsyncCallback\<boolean\>): void

在使用[通知模板](js-apis-inner-notification-notificationTemplate.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名       | 类型                     | 必填 | 说明                       |
| ------------ | ------------------------ | ---- | -------------------------- |
| templateName | string                   | 是   | 模板名称。当前仅支持'downloadTemplate'。                   |
| callback     | AsyncCallback\<boolean\> | 是   | 回调函数。返回true表示支持该模板；返回false表示不支持该模板；调用失败返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let templateName: string = 'downloadTemplate';
let isSupportTemplateCallback = (err: BusinessError, data: boolean): void => {
  if (err) {
    console.error(`isSupportTemplate failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`isSupportTemplate success, data: ${JSON.stringify(data)}`);
  }
}
notificationManager.isSupportTemplate(templateName, isSupportTemplateCallback);
```

## notificationManager.isSupportTemplate

isSupportTemplate(templateName: string): Promise\<boolean\>

查询模板是否存在。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名       | 类型   | 必填 | 说明     |
| ------------ | ------ | ---- | -------- |
| templateName | string | 是   | 模板名称。当前仅支持'downloadTemplate'。 |

**返回值：**

| 类型               | 说明            |
| ------------------ | --------------- |
| Promise\<boolean\> | Promise方式返回模板是否存在的结果（true：存在，false：不存在）。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let templateName: string = 'downloadTemplate';
notificationManager.isSupportTemplate(templateName).then((data: boolean) => {
  console.info(`isSupportTemplate success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`isSupportTemplate failed, code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.requestEnableNotification<sup>(deprecated)</sup>

requestEnableNotification(callback: AsyncCallback\<void\>): void

应用请求通知使能。使用callback异步回调。

> **说明：**
>
> 从API version 12开始不再维护，建议使用有context入参的[requestEnableNotification](#notificationmanagerrequestenablenotification10)代替。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名   | 类型                     | 必填 | 说明                       |
| -------- | ------------------------ | ---- | -------------------------- |
| callback | AsyncCallback\<void\> | 是   | 应用请求通知使能的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600004  | Notification disabled.          |
| 1600013  | A notification dialog box is already displayed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let requestEnableNotificationCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("requestEnableNotification success");
  }
};
notificationManager.requestEnableNotification(requestEnableNotificationCallback);
```

## notificationManager.requestEnableNotification<sup>(deprecated)</sup>

requestEnableNotification(): Promise\<void\>

应用请求通知使能。使用Promise异步回调。

> **说明：**
>
> 从API version 12开始不再维护，建议使用有context入参的[requestEnableNotification](#notificationmanagerrequestenablenotification10-1)代替。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型      | 说明        | 
|---------|-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600004  | Notification disabled.          |
| 1600013  | A notification dialog box is already displayed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.requestEnableNotification().then(() => {
  console.info("requestEnableNotification success");
}).catch((err: BusinessError) => {
  console.error(`requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.requestEnableNotification<sup>10+</sup>

requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback\<void\>): void

应用请求通知使能模态弹窗。使用callback异步回调。

仅当应用界面加载完成后（即调用[loadContent](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#loadcontent)成功），方可使用该接口。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名   | 类型                     | 必填 | 说明                 |
| -------- | ------------------------ | ---- |--------------------|
| context | [UIAbilityContext](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 是   | 通知弹窗绑定Ability的上下文。 |
| callback | AsyncCallback\<void\> | 是   | 应用请求通知使能的回调函数。     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600004  | Notification disabled.          |
| 1600013  | A notification dialog box is already displayed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause: ${JSON.stringify(err) ?? ''}`);
        return;
      }
      hilog.info(0x0000, 'testTag', `Succeeded in loading the content. Data: ${JSON.stringify(data) ?? ''}`);
      let requestEnableNotificationCallback = (err: BusinessError): void => {
        if (err) {
          hilog.error(0x0000, 'testTag', `[ANS] requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
        } else {
          hilog.info(0x0000, 'testTag', `[ANS] requestEnableNotification success`);
        }
      };
      notificationManager.requestEnableNotification(this.context, requestEnableNotificationCallback);
    });
  }
}
```

## notificationManager.requestEnableNotification<sup>10+</sup>

requestEnableNotification(context: UIAbilityContext): Promise\<void\>

应用请求通知使能模态弹窗。使用Promise异步回调。

仅当应用界面加载完成后（即调用[loadContent](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#loadcontent)成功），方可使用该接口。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名   | 类型                     | 必填 | 说明                 |
| -------- | ------------------------ | ---- |--------------------|
| context | [UIAbilityContext](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 是   | 通知弹窗绑定Ability的上下文。 |

**返回值：**

| 类型      | 说明        | 
|---------|-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600004  | Notification disabled.          |
| 1600013  | A notification dialog box is already displayed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause: ${JSON.stringify(err) ?? ''}`);
        return;
      }
      hilog.info(0x0000, 'testTag', `Succeeded in loading the content. Data: ${JSON.stringify(data) ?? ''}`);
      notificationManager.requestEnableNotification(this.context).then(() => {
        hilog.info(0x0000, 'testTag', `[ANS] requestEnableNotification success`);
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', `[ANS] requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
      });
    });
  }
}
```

## notificationManager.isDistributedEnabled   

isDistributedEnabled(callback: AsyncCallback\<boolean>): void

查询设备是否支持跨设备协同通知。使用callback异步回调。

**系统能力**：SystemCapability.Notification.Notification

**参数：**

| 参数名   | 类型                     | 必填 | 说明                       |
| -------- | ------------------------ | ---- | -------------------------- |
| callback | AsyncCallback\<boolean\> | 是   | 回调函数。返回true表示支持跨设备协同通知；返回false表示不支持跨设备协同通知；调用失败返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      | 
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600010  | Distributed operation failed.       |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let isDistributedEnabledCallback = (err: BusinessError, data: boolean): void => {
  if (err) {
    console.error(`isDistributedEnabled failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`isDistributedEnabled success ${JSON.stringify(data)}`);
  }
};
notificationManager.isDistributedEnabled(isDistributedEnabledCallback);
```

## notificationManager.isDistributedEnabled

isDistributedEnabled(): Promise\<boolean>

查询设备是否支持跨设备协同通知。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**返回值：**

| 类型               | 说明                                          |
| ------------------ | --------------------------------------------- |
| Promise\<boolean\> | Promise对象。返回true表示支持跨设备协同通知；返回false表示不支持跨设备协同通知。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 1600001  | Internal error.                     |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.          |
| 1600010  | Distributed operation failed.       |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.isDistributedEnabled().then((data: boolean) => {
  console.info(`isDistributedEnabled success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`isDistributedEnabled failed, code is ${err.code}, message is ${err.message}`);
});
```

## notificationManager.openNotificationSettings<sup>13+</sup>

openNotificationSettings(context: UIAbilityContext): Promise\<void\>

拉起应用的通知设置界面，该页面以半模态形式呈现，可用于设置通知开关、通知提醒方式等。使用Promise异步回调。

该接口不支持wearable设备。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Notification.NotificationSettings

**参数：**

| 参数名   | 类型                     | 必填 | 说明                 |
| -------- | ------------------------ | ---- |--------------------|
| context | [UIAbilityContext](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 是   | 通知设置页面绑定Ability的上下文。 |

**返回值：**

| 类型      | 说明        | 
|---------|-----------|
| Promise\<void\> | 无返回结果的Promise对象。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 801 | Capability not supported. |
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600018  | the notification settings window is already displayed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause: ${JSON.stringify(err) ?? ''}`);
        return;
      }
      hilog.info(0x0000, 'testTag', `Succeeded in loading the content. Data: ${JSON.stringify(data) ?? ''}`);
      notificationManager.openNotificationSettings(this.context).then(() => {
        hilog.info(0x0000, 'testTag', `[ANS] openNotificationSettings success`);
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', `[ANS] openNotificationSettings failed, code is ${err.code}, message is ${err.message}`);
      });
    });
  }
}
```

## ContentType

通知内容类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Notification.Notification

| 名称                              | 值          | 说明               |
| --------------------------------- | ----------- |------------------|
| NOTIFICATION_CONTENT_BASIC_TEXT   | 0          | 普通类型通知。          |
| NOTIFICATION_CONTENT_LONG_TEXT    | 1          | 长文本类型通知。         |
| NOTIFICATION_CONTENT_PICTURE      | 2          | 图片类型通知。          |
| NOTIFICATION_CONTENT_CONVERSATION | 3          | 社交类型通知。预留能力，暂未支持。|
| NOTIFICATION_CONTENT_MULTILINE    | 4          | 多行文本类型通知。        |
| NOTIFICATION_CONTENT_SYSTEM_LIVE_VIEW<sup>11+</sup>    | 5 | 实况窗类型通知。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。|
| NOTIFICATION_CONTENT_LIVE_VIEW<sup>11+</sup>    | 6 | 普通实况窗类型通知。只支持系统应用。  |

## SlotLevel

通知级别。

**系统能力**：SystemCapability.Notification.Notification

| 名称                              | 值          | 说明               |
| --------------------------------- | ----------- | ------------------ |
| LEVEL_NONE                        | 0           | 表示关闭通知功能。     |
| LEVEL_MIN                         | 1           | 表示通知功能已启用，但状态栏中不显示通知图标，且没有横幅和提示音。 |
| LEVEL_LOW                         | 2           | 表示通知功能已启用，且状态栏中显示通知图标，但没有横幅和提示音。 |
| LEVEL_DEFAULT                     | 3           | 表示通知功能已启用，状态栏中显示通知图标，没有横幅但有提示音。 |
| LEVEL_HIGH                        | 4           | 表示通知功能已启用，状态栏中显示通知图标，有横幅和提示音。 |


## SlotType

通知渠道类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Notification.Notification

| 名称                 | 值       | 说明       |
| -------------------- | -------- | ---------- |
| UNKNOWN_TYPE         | 0 | 未知类型。该类型对应[SlotLevel](#slotlevel)为LEVEL_MIN。 |
| SOCIAL_COMMUNICATION | 1 | 社交通信。该类型对应[SlotLevel](#slotlevel)为LEVEL_HIGH。 |
| SERVICE_INFORMATION  | 2 | 服务提醒。该类型对应[SlotLevel](#slotlevel)为LEVEL_HIGH。|
| CONTENT_INFORMATION  | 3 | 内容资讯。该类型对应[SlotLevel](#slotlevel)为LEVEL_MIN。 |
| LIVE_VIEW<sup>11+</sup>            | 4 | 实况窗。不支持三方应用直接创建该渠道类型通知，可以由系统代理创建后，三方应用发布同ID的通知来更新指定内容。该类型对应[SlotLevel](#slotlevel)为LEVEL_DEFAULT。 |
| CUSTOMER_SERVICE<sup>11+</sup>     | 5 | 客服消息。该类型用于用户与商家之间的客服消息，需由用户主动发起。该类型对应[SlotLevel](#slotlevel)为LEVEL_DEFAULT。  |
| OTHER_TYPES          | 0xFFFF | 其他。该类型对应[SlotLevel](#slotlevel)为LEVEL_MIN。 |

## BundleOption

type BundleOption = _BundleOption

描述BundleOption信息，即指定应用的包信息。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_BundleOption](js-apis-inner-notification-notificationCommonDef.md#bundleoption) | 描述BundleOption信息，即指定应用的包信息。 |

## NotificationActionButton

type NotificationActionButton = _NotificationActionButton

描述通知中显示的操作按钮。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationActionButton](js-apis-inner-notification-notificationActionButton.md) | 描述通知中显示的操作按钮。 |

## NotificationBasicContent

type NotificationBasicContent = _NotificationBasicContent

描述普通文本通知。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationBasicContent](js-apis-inner-notification-notificationContent.md#notificationbasiccontent) | 描述普通文本通知。 |

## NotificationContent

type NotificationContent = _NotificationContent

描述通知内容。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationContent](js-apis-inner-notification-notificationContent.md#notificationcontent-1) | 描述通知内容。 |

## NotificationLongTextContent

type NotificationLongTextContent = _NotificationLongTextContent

描述长文本通知。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationLongTextContent](js-apis-inner-notification-notificationContent.md#notificationlongtextcontent) | 描述长文本通知。 |

## NotificationMultiLineContent

type NotificationMultiLineContent = _NotificationMultiLineContent

描述多行文本通知。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationMultiLineContent](js-apis-inner-notification-notificationContent.md#notificationmultilinecontent) | 描述多行文本通知。 |

## NotificationPictureContent

type NotificationPictureContent = _NotificationPictureContent

描述附有图片的通知。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationPictureContent](js-apis-inner-notification-notificationContent.md#notificationpicturecontent) | 描述附有图片的通知。 |

## NotificationSystemLiveViewContent<sup>11+</sup>

type NotificationSystemLiveViewContent = _NotificationSystemLiveViewContent

描述系统实况窗通知内容。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationSystemLiveViewContent](js-apis-inner-notification-notificationContent.md#notificationsystemliveviewcontent) | 描述系统实况窗通知内容。 |

## NotificationRequest

type NotificationRequest = _NotificationRequest

描述通知的请求。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationRequest](js-apis-inner-notification-notificationRequest.md#notificationrequest-1) | 描述通知的请求。 |

## DistributedOptions

type DistributedOptions = _DistributedOptions

描述分布式选项。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_DistributedOptions](js-apis-inner-notification-notificationRequest.md#distributedoptions8) | 描述分布式选项。 |

## NotificationSlot

type NotificationSlot = _NotificationSlot

描述通知槽。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationSlot](js-apis-inner-notification-notificationSlot.md) | 描述通知槽。 |

## NotificationTemplate

type NotificationTemplate = _NotificationTemplate

通知模板。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationTemplate](js-apis-inner-notification-notificationTemplate.md) | 通知模板。 |

## NotificationUserInput

type NotificationUserInput = _NotificationUserInput

保存用户输入的通知消息。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationUserInput](js-apis-inner-notification-notificationUserInput.md) | 保存用户输入的通知消息。 |

## NotificationCapsule<sup>11+</sup>

type NotificationCapsule = _NotificationCapsule

描述通知胶囊。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationCapsule](js-apis-inner-notification-notificationContent.md#notificationcapsule11) | 描述通知胶囊。 |

## NotificationButton<sup>11+</sup>

type NotificationButton = _NotificationButton

描述通知按钮。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationButton](js-apis-inner-notification-notificationContent.md#notificationbutton11) | 描述通知按钮。 |

## NotificationTime<sup>11+</sup>

type NotificationTime = _NotificationTime

描述通知计时信息。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationTime](js-apis-inner-notification-notificationContent.md#notificationtime11) | 描述通知计时信息。 |

## NotificationProgress<sup>11+</sup>

type NotificationProgress = _NotificationProgress

描述通知进度。

**系统能力：** SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationProgress](js-apis-inner-notification-notificationContent.md#notificationprogress11) | 描述通知进度。 |
