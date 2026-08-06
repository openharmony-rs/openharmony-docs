# subscribeToEvent

## subscribeToEvent

```TypeScript
function subscribeToEvent(subscriber: CommonEventSubscriber, callback: Callback<CommonEventData>): Promise<void>
```

订阅公共事件，并返回订阅成功或失败信息。使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-commonEventManager-function subscribeToEvent(subscriber: CommonEventSubscriber, callback: Callback<CommonEventData>): Promise<void>--><!--Device-commonEventManager-function subscribeToEvent(subscriber: CommonEventSubscriber, callback: Callback<CommonEventData>): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示订阅者对象。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CommonEventData&gt; | 是 | 表示接收公共事件数据的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1500007](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500007-ipc请求发送失败) | Failed to send the message to the common event service. |
| [1500008](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500008-公共事件服务端初始化失败) | Failed to initialize the common event service. |
| [1500010](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500010-订阅者数量超限) | The count of subscriber exceeds system specification. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 定义订阅者，用于保存创建成功的订阅者对象，后续使用其完成订阅及取消订阅的动作
let subscriber: commonEventManager.CommonEventSubscriber | null = null;
// 订阅者信息
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
  events: ["event"]
};

// 创建订阅者
try {
  commonEventManager.createSubscriber(subscribeInfo,
    (err: BusinessError, commonEventSubscriber: commonEventManager.CommonEventSubscriber) => {
      if (err) {
        console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
      } else {
        console.info(`Succeeded in creating subscriber.`);
        subscriber = commonEventSubscriber;
        // 订阅公共事件
        try {
          commonEventManager.subscribeToEvent(subscriber, (data: commonEventManager.CommonEventData) => {
            console.info(`Succeeded to receive common event, data is ` + JSON.stringify(data));
          }).then(() => {
            console.info(`Succeeded to subscribe.`);
          }).catch((err: BusinessError) => {
            console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
          });
        } catch (error) {
          let err: BusinessError = error as BusinessError;
          console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
        }
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 定义订阅者
let subscriber: commonEventManager.CommonEventSubscriber | undefined | null = null;
// 订阅者信息
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
  events: ["event"]
};

// 创建订阅者
try {
  commonEventManager.createSubscriber(
    subscribeInfo,
    (err: BusinessError | null, commonEventSubscriber: commonEventManager.CommonEventSubscriber | undefined) => {
      if (err) {
        console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
        return;
      }

      // 确保订阅者对象有效
      if (!commonEventSubscriber) {
        console.error(`Failed to create subscriber: subscriber is undefined`);
        return;
      }

      console.info(`Succeeded in creating subscriber.`);
      subscriber = commonEventSubscriber;

      // 使用类型断言确保类型正确
      const validSubscriber = commonEventSubscriber as commonEventManager.CommonEventSubscriber;

      // 订阅公共事件
      commonEventManager.subscribeToEvent(
        validSubscriber,
        (data: commonEventManager.CommonEventData) => {
          console.info(`Succeeded to receive common event, data is ${JSON.stringify(data)}`);
        }
      ).then(() => {
        console.info(`Succeeded to subscribe.`);
      }).catch((err: Error) => {
        const businessErr = err as BusinessError;
        console.error(`Failed to subscribe. Code is ${businessErr.code}, message is ${businessErr.message}`);
      });
    }
  );
} catch (error) {
  const err = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}
```

