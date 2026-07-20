# isSupportTemplate

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="issupporttemplate"></a>
## isSupportTemplate

```TypeScript
function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void
```

在使用[通知模板](arkts-notification-notificationtemplate-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用callback异步回调。

**起始版本：** 9

<!--Device-notificationManager-function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void--><!--Device-notificationManager-function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateName | string | 是 | 模板名称。当前仅支持'downloadTemplate'。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示支持该模板；返回false表示不支持该模板；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

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


<a id="issupporttemplate-1"></a>
## isSupportTemplate

```TypeScript
function isSupportTemplate(templateName: string): Promise<boolean>
```

在使用[通知模板](arkts-notification-notificationtemplate-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用Promise异步回调。

**起始版本：** 9

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
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let templateName: string = 'downloadTemplate';
notificationManager.isSupportTemplate(templateName).then((data: boolean) => {
  console.info(`isSupportTemplate success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`isSupportTemplate failed, code is ${err.code}, message is ${err.message}`);
});

```

