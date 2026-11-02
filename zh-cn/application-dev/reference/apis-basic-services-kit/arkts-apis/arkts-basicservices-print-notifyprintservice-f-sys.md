# notifyPrintService（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## notifyPrintService('spooler_closed_for_cancelled' | 'spooler_closed_for_started')

```TypeScript
function notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started',
    callback: AsyncCallback<void>): void
```

将打印预览界面关闭信息通知打印服务，使用callback异步回调。用于在打印预览界面关闭后，让打印服务进行清理、退出等操作。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started',    callback: AsyncCallback<void>): void--><!--Device-print-function notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started',    callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示已创建的打印任务ID。 |
| type | 'spooler_closed_for_cancelled' &#124; 'spooler_closed_for_started' | 是 | 表示打印预览界面关闭信息的类型。'spooler_closed_for_cancelled'表示因取消当前打印任务而关闭打印预览界面；'spooler_closed_for_started'表示因打印任务成功下发而关闭打印预览界面。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当将打印预览界面关闭信息成功通知打印服务，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Async] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

<!--Del-->
**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started', (error: BusinessError) => {
    if (error) {
        console.error(`Failed to notify print service. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('notifyPrintService success');
    }
});
```

<!--DelEnd-->


## notifyPrintService('spooler_closed_for_cancelled' | 'spooler_closed_for_started')

```TypeScript
function notifyPrintService(jobId: string,
    type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise<void>
```

将打印预览界面关闭信息通知打印服务，使用Promise异步回调。用于在打印预览界面关闭后，让打印服务进行清理、退出等操作。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function notifyPrintService(jobId: string,    type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise<void>--><!--Device-print-function notifyPrintService(jobId: string,    type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示已创建的打印任务ID。 |
| type | 'spooler_closed_for_cancelled' &#124; 'spooler_closed_for_started' | 是 | 表示打印预览界面关闭信息的类型。'spooler_closed_for_cancelled'表示因取消当前打印任务而关闭打印预览界面；'spooler_closed_for_started'表示因打印任务成功下发而关闭打印预览界面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Async] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

<!--Del-->
**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started').then(() => {
    console.info('notifyPrintService success');
}).catch((error: BusinessError) => {
    console.error(`Failed to notify print service. Code: ${error.code}, message: ${error.message}`);
});
```

<!--DelEnd-->
