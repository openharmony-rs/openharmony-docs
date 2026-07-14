# publishAsUser（系统接口）

## publishAsUser

```TypeScript
function publishAsUser(event: string, userId: number, callback: AsyncCallback<void>): void
```

以回调的形式向指定用户发布公共事件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** publishAsUser(event:

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发送的公共事件。 |
| userId | number | 是 | 表示指定向该用户ID发送此公共事件。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 表示被指定的回调方法。 |

**示例：**

```TypeScript
import Base from '@ohos.base';

// 发布公共事件回调
function publishCB(err:Base.BusinessError) {
    if (err.code) {
        console.error(`publishAsUser failed, code is ${err.code}`);
    } else {
        console.info("publishAsUser");
    }
}

// 指定发送的用户
let userId = 100;

// 发布公共事件
commonEvent.publishAsUser("event", userId, publishCB);

```


## publishAsUser

```TypeScript
function publishAsUser(
    event: string,
    userId: number,
    options: CommonEventPublishData,
    callback: AsyncCallback<void>
  ): void
```

以回调形式向指定用户发布公共事件并指定发布信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** publishAsUser(

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发布的公共事件。 |
| userId | number | 是 | 表示指定向该用户ID发送此公共事件。 |
| options | CommonEventPublishData | 是 | 表示发布公共事件的属性。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 表示被指定的回调方法。 |

**示例：**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

// 公共事件相关信息
let options:CommonEventManager.CommonEventPublishData = {
    code: 0,             // 公共事件的初始代码
    data: "initial data",// 公共事件的初始数据
}

// 发布公共事件回调
function publishCB(err:Base.BusinessError) {
    if (err.code) {
        console.error(`publishAsUser failed, code is ${err.code}`);
    } else {
        console.info("publishAsUser");
    }
}

// 指定发送的用户
let userId = 100;

// 发布公共事件
commonEvent.publishAsUser("event", userId, options, publishCB);

```

