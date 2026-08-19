# unsubscribe

## 导入模块

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## unsubscribe

```TypeScript
function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback<void>): void
```

取消订阅公共事件。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-commonEventManager-function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback<void>): void--><!--Device-commonEventManager-function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | CommonEventSubscriber | 是 | 表示订阅者对象。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 否 | 回调函数。当取消公共事件订阅成功时，err为undefined；取消失败时， err为错误对象。不传该参数时，默认取消订阅且不返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1500007](../errorcode-CommonEventService.md#1500007-ipc请求发送失败) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-公共事件服务端初始化失败) | Failed to initialize the common event service. |

**示例**

ArkTS-Dyn示例：

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
  commonEventManager.createSubscriber(subscribeInfo,
    (err: BusinessError, commonEventSubscriber: commonEventManager.CommonEventSubscriber) => {
      if(!err) {
        console.info(`Succeeded in creating subscriber.`);
        subscriber = commonEventSubscriber;
        // 订阅公共事件
        try {
          commonEventManager.subscribe(subscriber, (err: BusinessError, data: commonEventManager.CommonEventData) => {
            if (err) {
              console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
              return;
            }
            console.info(`Succeeded in subscribing, data is ${JSON.stringify(data)}`);
          });
        } catch (error) {
          let err: BusinessError = error as BusinessError;
          console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
        }
        return;
      }
      console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}

// 取消订阅公共事件
// 等待异步接口subscribe执行完毕，开发者根据实际业务选择是否需要添加setTimeout
setTimeout(() => {
  try {
    commonEventManager.unsubscribe(subscriber, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to unsubscribe. Code is ${err.code}, message is ${err.message}`);
        return;
      }
      // subscriber不再使用时需要将其置为null，避免内存泄露
      subscriber = null;
      console.info(`Succeeded in unsubscribing.`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to unsubscribe. Code is ${err.code}, message is ${err.message}`);
  }
}, 500);
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 定义订阅者，允许为 null 或 undefined
let subscriber: commonEventManager.CommonEventSubscriber | null | undefined = null;

// 订阅者信息
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
  events: ['event']
};

    // 创建订阅者
try {
  commonEventManager.createSubscriber(
    subscribeInfo,
    (err: BusinessError | null,
      commonEventSubscriber: commonEventManager.CommonEventSubscriber | undefined | null) => {
      if (!err && commonEventSubscriber) {
        console.info(`Succeeded in creating subscriber.`);
        subscriber = commonEventSubscriber as commonEventManager.CommonEventSubscriber;
        // 订阅公共事件 - 使用确定的非空对象
        try {
          commonEventManager.subscribe(
            commonEventSubscriber, // 直接使用回调参数，确保非空
            (err: BusinessError | null, data: commonEventManager.CommonEventData | undefined | null) => {
              if (err) {
                console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
                return;
              }
              console.info(`Succeeded in subscribing, data is ${JSON.stringify(data)}`);
            }
          );
        } catch (error) {
          const err = error as BusinessError;
          console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
        }
        return;
      }

      if (err) {
         console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
      } else {
        console.error(`Failed to create subscriber: commonEventSubscriber is null or undefined`);
      }
    }
  );
} catch (error) {
  const err = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}

// 取消订阅公共事件
setTimeout(() => {
  if (subscriber) {
    const currentSubscriber = subscriber as commonEventManager.CommonEventSubscriber;
    try {
      commonEventManager.unsubscribe(
        currentSubscriber,
        (err: BusinessError | null) => {
          if (err) {
            console.error(`Failed to unsubscribe. Code is ${err.code}, message is ${err.message}`);
            return;
          }
          subscriber = undefined;
          console.info(`Succeeded in unsubscribing.`);
        }
      );
    } catch (error) {
      const err = error as BusinessError;
      console.error(`Failed to unsubscribe. Code is ${err.code}, message is ${err.message}`);
    }
  } else {
    console.warn("Cannot unsubscribe: subscriber is null or undefined");
  }
}, 500);
```

