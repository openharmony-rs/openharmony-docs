# removeAllSlots

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## removeAllSlots

```TypeScript
function removeAllSlots(callback: AsyncCallback<void>): void
```

删除当前应用所有通知渠道。使用callback异步回调。 删除后，当前应用的所有通知渠道及其配置将被永久移除，后续发布通知时系统将自动创建对应类型的渠道。 已通过这些渠道发布的通知不受影响，仍可在通知中心查看。 适用于需要一次性清除所有渠道配置的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-notificationManager-function removeAllSlots(callback: AsyncCallback<void>): void--><!--Device-notificationManager-function removeAllSlots(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参见：**

addSlot 创建通知频道。

getSlot 获取指定类型的通知渠道。

removeSlot 删除所有通知渠道。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当删除当前应用所有通知渠道成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let removeAllSlotsCallback = (err: BusinessError | null): void => {
  if (err) {
    console.error(`Failed to remove all slots. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in removing all slots.`);
  }
}
notificationManager.removeAllSlots(removeAllSlotsCallback);
```


## removeAllSlots

```TypeScript
function removeAllSlots(): Promise<void>
```

删除当前应用所有通知渠道。使用Promise异步回调。 删除后，当前应用的所有通知渠道及其配置将被永久移除，后续发布通知时系统将自动创建对应类型的渠道。 已通过这些渠道发布的通知不受影响，仍可在通知中心查看。 适用于需要一次性清除所有渠道配置的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-notificationManager-function removeAllSlots(): Promise<void>--><!--Device-notificationManager-function removeAllSlots(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参见：**

addSlot 创建通知频道。

getSlot 获取指定类型的通知渠道。

removeSlot 删除指定类型的通知渠道。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.removeAllSlots().then(() => {
  console.info(`Succeeded in removing all slots.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to remove all slots. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.removeAllSlots().then(() => {
  console.info(`Succeeded in removing all slots.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to remove all slots. Code is ${error.code}, message is ${error.message}`);
});
```

