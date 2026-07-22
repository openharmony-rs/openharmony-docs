# unsubscribe

## unsubscribe

```TypeScript
function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback<void>): void
```

以回调形式取消订阅公共事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [unsubscribe](arkts-basicservices-commoneventmanager-unsubscribe-f.md#unsubscribe)

<!--Device-commonEvent-function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback<void>): void--><!--Device-commonEvent-function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [CommonEventSubscriber](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md) | 是 | 表示订阅者对象。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 否 | 表示取消订阅的回调方法。 |

**示例：**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber;    // 用于保存创建成功的订阅者对象，后续使用其完成订阅及取消订阅的动作

// 订阅者信息
let subscribeInfo:CommonEventManager.CommonEventSubscribeInfo = {
    events: ["event"]
};

// 订阅公共事件回调
let subscribeCallBack = (err:Base.BusinessError, data:CommonEventManager.CommonEventData) => {
    if (err.code) {
        console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("subscribe " + JSON.stringify(data));
    }
}

// 创建订阅者回调
let createCallBack = (err:Base.BusinessError, commonEventSubscriber:CommonEventManager.CommonEventSubscriber) => {
    if (err.code) {
        console.error(`createSubscriber failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("createSubscriber");
        subscriber = commonEventSubscriber;
         // 订阅公共事件
        commonEvent.subscribe(subscriber, subscribeCallBack);
    }
}

// 取消订阅公共事件回调
let unsubscribeCallback = (err: Base.BusinessError) => {
    if (err.code) {
        console.error(`unsubscribe failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("unsubscribe");
    }
}

// 创建订阅者
commonEvent.createSubscriber(subscribeInfo, createCallBack);

// 取消订阅公共事件
// 注意：需在subscriber创建成功后（即createCallBack回调执行后）调用，此处仅展示API用法
commonEvent.unsubscribe(subscriber, unsubscribeCallback);

```

