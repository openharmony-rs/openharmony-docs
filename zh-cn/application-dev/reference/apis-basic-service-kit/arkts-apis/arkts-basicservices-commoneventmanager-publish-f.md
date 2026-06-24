# publish

## publish

```TypeScript
function publish(event: string, callback: AsyncCallback<void>): void
```

发布公共事件。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发送的公共事件。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当公共事件发布成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1500003](../../errorcode-universal.md#1500003-The) | The common event sending frequency too high.&lt;br&gt;**适用版本：** 20+ |
| [1500007](../../errorcode-universal.md#1500007-Failed) | Failed to send the message to the common event service. |
| [1500008](../../errorcode-universal.md#1500008-Failed) | Failed to initialize the common event service. |
| [1500009](../../errorcode-universal.md#1500009-Failed) | Failed to obtain system parameters. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 发布公共事件
try {
  commonEventManager.publish('event', (err: BusinessError) => {
    if (err) {
      console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Succeeded in publishing common event.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
}

```


## publish

```TypeScript
function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback<void>): void
```

发布公共事件。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发布的公共事件。 |
| options | CommonEventPublishData | 是 | 表示发布公共事件的属性。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当公共事件发布成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1500003](../../errorcode-universal.md#1500003-The) | The common event sending frequency too high.&lt;br&gt;**适用版本：** 20+ |
| [1500007](../../errorcode-universal.md#1500007-Failed) | Failed to send the message to the common event service. |
| [1500008](../../errorcode-universal.md#1500008-Failed) | Failed to initialize the common event service. |
| [1500009](../../errorcode-universal.md#1500009-Failed) | Failed to obtain system parameters. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 公共事件相关信息，以发布有序公共事件为例
let options: commonEventManager.CommonEventPublishData = {
  code: 0,
  data: 'initial data',
  isOrdered: true // 有序公共事件
}

// 发布公共事件
try {
  commonEventManager.publish('event', options, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Succeeded in publishing common event.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
}

```

