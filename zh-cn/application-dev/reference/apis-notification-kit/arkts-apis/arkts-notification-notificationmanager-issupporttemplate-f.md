# isSupportTemplate

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isSupportTemplate

```TypeScript
function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void
```

在使用[通知模板](arkts-notification-notificationtemplate-notificationtemplate-i.md#NotificationTemplate)发布通知前， 可以通过该接口查询是否支持对应的通知模板。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-notificationManager-function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void--><!--Device-notificationManager-function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateName | string | 是 | 模板名称。当前仅支持'downloadTemplate'。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示支持该模板；返回false表示不支持该模板；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let templateName: string = 'downloadTemplate';
let isSupportTemplateCallback = (err: BusinessError, data: boolean): void => {
  if (err) {
    console.error(`isSupportTemplate failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`isSupportTemplate success, data: ${JSON.stringify(data)}`);
  }
}
notificationManager.isSupportTemplate(templateName, isSupportTemplateCallback);
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let templateName: string = 'downloadTemplate';
let isSupportTemplateCallback = (err: BusinessError | null , data: boolean | undefined | null): void => {
  if (err) {
    console.error(`isSupportTemplate failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`isSupportTemplate success, data: ${JSON.stringify(data)}`);
  }
}
notificationManager.isSupportTemplate(templateName, isSupportTemplateCallback);
```


## isSupportTemplate

```TypeScript
function isSupportTemplate(templateName: string): Promise<boolean>
```

在使用[通知模板](arkts-notification-notificationtemplate-notificationtemplate-i.md#NotificationTemplate)发布通知前， 可以通过该接口查询是否支持对应的通知模板。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-notificationManager-function isSupportTemplate(templateName: string): Promise<boolean>--><!--Device-notificationManager-function isSupportTemplate(templateName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateName | string | 是 | 模板名称。当前仅支持'downloadTemplate'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示支持该模板；返回false表示不支持该模板。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let templateName: string = 'downloadTemplate';
notificationManager.isSupportTemplate(templateName).then((data: boolean) => {
  console.info(`isSupportTemplate success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`isSupportTemplate failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let templateName: string = 'downloadTemplate';
notificationManager.isSupportTemplate(templateName).then((data: boolean) => {
  console.info(`isSupportTemplate success, data: ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`isSupportTemplate failed, code is ${error.code}, message is ${error.message}`);
});
```

