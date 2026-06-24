# subscribe

## subscribe

```TypeScript
function subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback<CommonEventData>): void
```

订阅公共事件。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | CommonEventSubscriber | 是 | 表示订阅者对象。 |
| callback | AsyncCallback&lt;CommonEventData&gt; | 是 | 回调函数。当公共事件订阅成功后，事件触发时执行的回调函数；否则订阅失败时，err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-capability) | capability not supported |
| [1500007](../../errorcode-universal.md#1500007-Failed) | Failed to send the message to the common event service. |
| [1500008](../../errorcode-universal.md#1500008-Failed) | Failed to initialize the common event service. |
| [1500010](../../errorcode-universal.md#1500010-The) | The count of subscriber exceed system specification.&lt;br&gt;**适用版本：** 20+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 定义订阅者，用于保存创建成功的订阅者对象，后续使用其完成订阅及退订的动作
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

```

