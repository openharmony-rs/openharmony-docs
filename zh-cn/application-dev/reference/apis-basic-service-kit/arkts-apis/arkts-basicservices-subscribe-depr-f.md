# subscribe

## subscribe

```TypeScript
function subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback<CommonEventData>): void
```

以回调形式订阅公共事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [subscribe](arkts-basicservices-subscribe-f.md#subscribe-1)

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | CommonEventSubscriber | 是 | 表示订阅者对象。 |
| callback | AsyncCallback&lt;CommonEventData&gt; | 是 | 表示接收公共事件数据的回调函数。 |

**示例：**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber;// 用于保存创建成功的订阅者对象，后续使用其完成订阅及退订的动作

// 订阅者信息
let subscribeInfo:CommonEventManager.CommonEventSubscribeInfo = {
    events: ["event"]
};

// 订阅公共事件回调
function subscribeCB(err:Base.BusinessError, data:CommonEventManager.CommonEventData) {
    if (err.code) {
        console.error(`subscribe failed, code is ${err.code}`);
    } else {
        console.info("subscribe " + JSON.stringify(data));
    }
}

// 创建订阅者回调
function createCB(err:Base.BusinessError, commonEventSubscriber:CommonEventManager.CommonEventSubscriber) {
    if (err.code) {
        console.error(`createSubscriber failed, code is ${err.code}`);
    } else {
        console.info("createSubscriber");
        subscriber = commonEventSubscriber;
        // Subscribe to a common event.
        commonEvent.subscribe(subscriber, subscribeCB);
    }
}

// 创建订阅者
commonEvent.createSubscriber(subscribeInfo, createCB);

```

