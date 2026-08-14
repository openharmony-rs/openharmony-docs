# publishAsUser（系统接口）

## publishAsUser

```TypeScript
function publishAsUser(event: string, userId: int, callback: AsyncCallback<void>): void
```

向指定用户发布公共事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-commonEventManager-function publishAsUser(event: string, userId: int, callback: AsyncCallback<void>): void--><!--Device-commonEventManager-function publishAsUser(event: string, userId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发布的公共事件。 |
| userId | int | 是 | 表示指定接收此公共事件的用户ID。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当公共事件发布成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1500006](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500006-无效userid) | Invalid userId.<br>**适用版本：** 21+ |
| [1500007](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500007-ipc请求发送失败) | Failed to send the message to the common event service. |
| [1500003](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500003-公共事件发送频率过高) | The common event sending frequency too high.<br>**适用版本：** 20+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1500008](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500008-公共事件服务端初始化失败) | Failed to initialize the common event service. |
| [1500009](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500009-获取系统参数失败) | Failed to obtain system parameters. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 指定发送的用户
let userId = 100;

// 发布公共事件
try {
    commonEventManager.publishAsUser('event', userId, (err: BusinessError) => {
      if (err) {
        console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('publishAsUser');
    });
} catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 指定发送的用户
let userId = 1;

// 发布公共事件
try {
    commonEventManager.publishAsUser('event', userId, (err: BusinessError | null) => {
      if (err) {
        console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('publishAsUser');
    });
} catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```


## publishAsUser

```TypeScript
function publishAsUser(
    event: string,
    userId: int,
    options: CommonEventPublishData,
    callback: AsyncCallback<void>
  ): void
```

向指定用户发布公共事件并指定发布信息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-commonEventManager-function publishAsUser(    event: string,    userId: int,    options: CommonEventPublishData,    callback: AsyncCallback<void>  ): void--><!--Device-commonEventManager-function publishAsUser(    event: string,    userId: int,    options: CommonEventPublishData,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 表示要发布的公共事件。 |
| userId | int | 是 | 表示指定接收此公共事件的用户ID。 |
| options | CommonEventPublishData | 是 | 表示发布公共事件的属性。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当公共事件发布成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1500006](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500006-无效userid) | Invalid userId.<br>**适用版本：** 21+ |
| [1500007](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500007-ipc请求发送失败) | Failed to send the message to the common event service. |
| [1500003](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500003-公共事件发送频率过高) | The common event sending frequency too high.<br>**适用版本：** 20+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1500008](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500008-公共事件服务端初始化失败) | Failed to initialize the common event service. |
| [1500009](../../apis-basic-services-kit/errorcode-CommonEventService.md#1500009-获取系统参数失败) | Failed to obtain system parameters. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 公共事件相关信息
let options: commonEventManager.CommonEventPublishData = {
  code: 0,        // 公共事件的初始代码
  data: 'initial data', // 公共事件的初始数据
}

// 指定发送的用户
let userId = 100;
// 发布公共事件
try {
  commonEventManager.publishAsUser('event', userId, options, (err: BusinessError) => {
    if (err) {
      console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('publishAsUser');
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 公共事件相关信息
let options:commonEventManager.CommonEventPublishData = {
  code: 0,// 公共事件的初始代码
  data: 'initial data',// 公共事件的初始数据
}

// 指定发送的用户
let userId = 1;
// 发布公共事件
try {
  commonEventManager.publishAsUser('event', userId, options, (err: BusinessError | null) => {
    if (err) {
      console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('publishAsUser');
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```

