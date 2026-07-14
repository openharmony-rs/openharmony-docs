# publish

## publish

```TypeScript
function publish(event: string, callback: AsyncCallback<void>): void
```

发布公共事件（回调形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** publish(event:

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发送的公共事件。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 表示指定的回调方法。 |

**示例：**

```TypeScript
import Base from '@ohos.base';

// 发布公共事件回调
function publishCB(err:Base.BusinessError) {
    if (err.code) {
        console.error(`publish failed, code is ${err.code}`);
    } else {
        console.info("publish");
    }
}

// 发布公共事件
commonEvent.publish("event", publishCB);

```


## publish

```TypeScript
function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback<void>): void
```

以回调的形式发布公共事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** publish(event:

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发布的公共事件。 |
| options | CommonEventPublishData | 是 | 表示发布公共事件的属性。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 表示指定的回调方法。 |

**示例：**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

// 公共事件相关信息
let options:CommonEventManager.CommonEventPublishData = {
    code: 0,             // 公共事件的初始代码
    data: "initial data", // 公共事件的初始数据
    isOrdered: true  // 有序公共事件
}

// 发布公共事件回调
function publishCB(err:Base.BusinessError) {
    if (err.code) {
        console.error(`publish failed, code is ${err.code}`);
    } else {
        console.info("publish");
    }
}

// 发布公共事件
commonEvent.publish("event", options, publishCB);

```

