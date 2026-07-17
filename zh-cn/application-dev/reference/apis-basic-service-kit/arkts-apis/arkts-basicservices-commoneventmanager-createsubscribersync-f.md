# createSubscriberSync

## 导入模块

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## createSubscriberSync

```TypeScript
function createSubscriberSync(subscribeInfo: CommonEventSubscribeInfo): CommonEventSubscriber
```

createSubscriber的同步接口。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-commonEventManager-function createSubscriberSync(subscribeInfo: CommonEventSubscribeInfo): CommonEventSubscriber--><!--Device-commonEventManager-function createSubscriberSync(subscribeInfo: CommonEventSubscribeInfo): CommonEventSubscriber-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeInfo | [CommonEventSubscribeInfo](arkts-basicservices-commoneventmanager-commoneventsubscribeinfo-t.md) | 是 | 表示订阅信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CommonEventSubscriber](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md) | 返回订阅者对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 定义订阅者，用于保存创建成功的订阅者对象，后续使用其完成订阅及取消订阅的动作
let subscriber: commonEventManager.CommonEventSubscriber | null = null;
// 订阅者信息
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
  events: ['event']
};
// 创建订阅者
try {
  subscriber = commonEventManager.createSubscriberSync(subscribeInfo);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}

```

