# notifyPrintServiceEvent（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="notifyprintserviceevent"></a>
## notifyPrintServiceEvent

```TypeScript
function notifyPrintServiceEvent(event: ApplicationEvent): Promise<void>
```

将打印应用相关事件通知打印服务，使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function notifyPrintServiceEvent(event: ApplicationEvent): Promise<void>--><!--Device-print-function notifyPrintServiceEvent(event: ApplicationEvent): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ApplicationEvent](arkts-basicservices-print-applicationevent-e.md) | 是 | 表示打印应用事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let event : print.ApplicationEvent = print.ApplicationEvent.APPLICATION_CREATED;
print.notifyPrintServiceEvent(event).then(() => {
    console.info('notifyPrintServiceEvent success');
}).catch((error: BusinessError) => {
    console.error('notifyPrintServiceEvent error : ' + JSON.stringify(error));
})

```


<a id="notifyprintserviceevent-1"></a>
## notifyPrintServiceEvent

```TypeScript
function notifyPrintServiceEvent(event: ApplicationEvent, jobId: string): Promise<void>
```

将打印应用相关事件通知打印服务，使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function notifyPrintServiceEvent(event: ApplicationEvent, jobId: string): Promise<void>--><!--Device-print-function notifyPrintServiceEvent(event: ApplicationEvent, jobId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ApplicationEvent](arkts-basicservices-print-applicationevent-e.md) | 是 | 表示打印应用事件。 |
| jobId | string | 是 | 表示打印任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let event : print.ApplicationEvent = print.ApplicationEvent.APPLICATION_CREATED;
let jobId : string = '1';
print.notifyPrintServiceEvent(event, jobId).then(() => {
    console.info('notifyPrintServiceEvent success');
}).catch((error: BusinessError) => {
    console.error('notifyPrintServiceEvent error : ' + JSON.stringify(error));
})

```

