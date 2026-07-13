# unsubscribe

## unsubscribe

```TypeScript
function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback<void>): void
```

以回调形式取消订阅公共事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [unsubscribe](arkts-basicservices-unsubscribe-f.md#unsubscribe-1)

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | CommonEventSubscriber | 是 | 表示订阅者对象。 |
| callback | AsyncCallback&lt;void&gt; | 否 | 表示取消订阅的回调方法。 |

**示例：**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber;    // 用于保存创建成功的订阅者对象，后续使用其完成订阅及退订的动作

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

// 取消订阅公共事件回调
function unsubscribeCB(err:Base.BusinessError) {
    if (err.code) {
        console.error(`unsubscribe failed, code is ${err.code}`);
    } else {
        console.info("unsubscribe");
    }
}

// 创建订阅者
commonEvent.createSubscriber(subscribeInfo, createCB);

// 取消订阅公共事件
commonEvent.unsubscribe(subscriber, unsubscribeCB);

```

