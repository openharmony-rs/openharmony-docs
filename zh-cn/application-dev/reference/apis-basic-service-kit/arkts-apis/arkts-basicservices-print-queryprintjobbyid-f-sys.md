# queryPrintJobById（系统接口）

## queryPrintJobById

```TypeScript
function queryPrintJobById(jobId: string, callback: AsyncCallback<PrintJob>): void
```

按打印任务ID查询打印任务，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function queryPrintJobById(jobId: string, callback: AsyncCallback<PrintJob>): void--><!--Device-print-function queryPrintJobById(jobId: string, callback: AsyncCallback<PrintJob>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;[PrintJob](arkts-basicservices-print-printjob-i-sys.md)&gt; | 是 | 异步按打印任务ID查询打印任务之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';

let jobId : string = '1';
print.queryPrintJobById(jobId, (err: BusinessError, printJob : print.PrintJob) => {
    if (err) {
        console.error('queryPrintJobById failed, because : ' + JSON.stringify(err));
    } else {
        console.info('queryPrintJobById success, data : ' + JSON.stringify(printJob));
    }
})
```


## queryPrintJobById

```TypeScript
function queryPrintJobById(jobId: string): Promise<PrintJob>
```

按打印任务ID查询打印任务，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function queryPrintJobById(jobId: string): Promise<PrintJob>--><!--Device-print-function queryPrintJobById(jobId: string): Promise<PrintJob>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PrintJob](arkts-basicservices-print-printjob-i-sys.md)&gt; | Promise对象，返回查询到的打印任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';

let jobId : string = '1';
print.queryPrintJobById(jobId).then((printJob : print.PrintJob) => {
    console.info('queryPrintJobById data : ' + JSON.stringify(printJob));
}).catch((error: BusinessError) => {
    console.error('queryPrintJobById error : ' + JSON.stringify(error));
})
```

