# createSubscriber

<a id="createsubscriber"></a>
## createSubscriber

```TypeScript
function createSubscriber(
    subscribeInfo: CommonEventSubscribeInfo,
    callback: AsyncCallback<CommonEventSubscriber>
  ): void
```

以回调形式创建订阅者。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [createSubscriber(](arkts-basicservices-commoneventmanager-createsubscriber-f.md#createsubscriber-1)

<!--Device-commonEvent-function createSubscriber(
    subscribeInfo: CommonEventSubscribeInfo,
    callback: AsyncCallback<CommonEventSubscriber>
  ): void--><!--Device-commonEvent-function createSubscriber(
    subscribeInfo: CommonEventSubscribeInfo,
    callback: AsyncCallback<CommonEventSubscriber>
  ): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeInfo | [CommonEventSubscribeInfo](arkts-basicservices-commoneventmanager-commoneventsubscribeinfo-t.md) | 是 | 表示订阅信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;CommonEventSubscriber&gt; | 是 | 表示创建订阅者的回调方法。 |

**示例：**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber; // 用于保存创建成功的订阅者对象，后续使用其完成订阅及取消订阅的动作

// 订阅者信息
let subscribeInfo:CommonEventManager.CommonEventSubscribeInfo = {
    events: ["event"]
};

// 创建订阅者回调
let createCallBack = (err:Base.BusinessError, commonEventSubscriber:CommonEventManager.CommonEventSubscriber) => {
    if (err.code) {
        console.error(`createSubscriber failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("createSubscriber");
        subscriber = commonEventSubscriber;
    }
}

// 创建订阅者
commonEvent.createSubscriber(subscribeInfo, createCallBack);

```


<a id="createsubscriber-1"></a>
## createSubscriber

```TypeScript
function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise<CommonEventSubscriber>
```

以Promise形式创建订阅者。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [createSubscriber(subscribeInfo:](arkts-basicservices-commoneventmanager-createsubscriber-f.md#createsubscriber-1)

<!--Device-commonEvent-function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise<CommonEventSubscriber>--><!--Device-commonEvent-function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise<CommonEventSubscriber>-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeInfo | [CommonEventSubscribeInfo](arkts-basicservices-commoneventmanager-commoneventsubscribeinfo-t.md) | 是 | 表示订阅信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CommonEventSubscriber&gt; | 返回订阅者对象。 |

**示例：**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber; // 用于保存创建成功的订阅者对象，后续使用其完成订阅及取消订阅的动作

// 订阅者信息
let subscribeInfo:CommonEventManager.CommonEventSubscribeInfo = {
    events: ["event"]
};

// 创建订阅者
commonEvent.createSubscriber(subscribeInfo).then((commonEventSubscriber:CommonEventManager.CommonEventSubscriber) => {
    console.info("createSubscriber");
    subscriber = commonEventSubscriber;
}).catch((err:Base.BusinessError) => {
    console.error(`createSubscriber failed, code is ${err.code}, message is ${err.message}`);
});

```

