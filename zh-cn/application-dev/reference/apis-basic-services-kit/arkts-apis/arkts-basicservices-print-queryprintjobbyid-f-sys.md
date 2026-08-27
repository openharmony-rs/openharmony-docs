# queryPrintJobById（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryPrintJobById

```TypeScript
function queryPrintJobById(jobId: string, callback: AsyncCallback<PrintJob>): void
```

按打印任务ID查询打印任务，使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[PrintJob](arkts-basicservices-print-printjob-i.md)&gt; | 是 | 异步按打印任务ID查询打印任务之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.queryPrintJobById(jobId, (error: BusinessError, printJob : print.PrintJob) => {
    if (error) {
        console.error(`Failed to query print job by id. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('queryPrintJobById success, data : ' + JSON.stringify(printJob));
    }
});
```


## queryPrintJobById

```TypeScript
function queryPrintJobById(jobId: string): Promise<PrintJob>
```

按打印任务ID查询打印任务，使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PrintJob](arkts-basicservices-print-printjob-i.md)&gt; | Promise对象，返回查询到的打印任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.queryPrintJobById(jobId).then((printJob : print.PrintJob) => {
    console.info('queryPrintJobById data : ' + JSON.stringify(printJob));
}).catch((error: BusinessError) => {
    console.error(`Failed to query print job by id. Code: ${error.code}, message: ${error.message}`);
});
```
