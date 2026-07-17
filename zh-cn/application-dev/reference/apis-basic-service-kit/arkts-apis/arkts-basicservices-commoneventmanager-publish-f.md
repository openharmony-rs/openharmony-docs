# publish

## 导入模块

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## publish

```TypeScript
function publish(event: string, callback: AsyncCallback<void>): void
```

发布公共事件。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-commonEventManager-function publish(event: string, callback: AsyncCallback<void>): void--><!--Device-commonEventManager-function publish(event: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发送的公共事件。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当公共事件发布成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1500003](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500003-公共事件发送频率过高) | The common event sending frequency too high.<br>**适用版本：** 20+ |
| [1500007](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500007-ipc请求发送失败) | Failed to send the message to the common event service. |
| [1500008](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500008-公共事件服务端初始化失败) | Failed to initialize the common event service. |
| [1500009](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500009-获取系统参数失败) | Failed to obtain system parameters. |

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

<!--Device-commonEventManager-function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback<void>): void--><!--Device-commonEventManager-function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发布的公共事件。 |
| options | [CommonEventPublishData](arkts-basicservices-commoneventpublishdata-commoneventpublishdata-i.md) | 是 | 表示发布公共事件的属性。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当公共事件发布成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1500003](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500003-公共事件发送频率过高) | The common event sending frequency too high.<br>**适用版本：** 20+ |
| [1500007](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500007-ipc请求发送失败) | Failed to send the message to the common event service. |
| [1500008](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500008-公共事件服务端初始化失败) | Failed to initialize the common event service. |
| [1500009](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500009-获取系统参数失败) | Failed to obtain system parameters. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 公共事件相关信息，以发布有序公共事件为例
let options: commonEventManager.CommonEventPublishData = {
  code: 0,
  data: 'initial data',
  isOrdered: true // 有序公共事件
};

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

