# queryPrintJobList（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryPrintJobList

```TypeScript
function queryPrintJobList(callback: AsyncCallback<Array<PrintJob>>): void
```

查询所有打印任务，使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function queryPrintJobList(callback: AsyncCallback<Array<PrintJob>>): void--><!--Device-print-function queryPrintJobList(callback: AsyncCallback<Array<PrintJob>>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<Array<PrintJob>> | 是 | 异步查询所有打印任务之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryPrintJobList((err: BusinessError, printJobs : print.PrintJob[]) => {
    if (err) {
        console.error('queryPrintJobList failed, because : ' + JSON.stringify(err));
    } else {
        console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
    }
})

```


## queryPrintJobList

```TypeScript
function queryPrintJobList(): Promise<Array<PrintJob>>
```

查询所有打印任务，使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function queryPrintJobList(): Promise<Array<PrintJob>>--><!--Device-print-function queryPrintJobList(): Promise<Array<PrintJob>>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<PrintJob>> | Promise对象，返回包含所有打印任务的列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryPrintJobList().then((printJobs : print.PrintJob[]) => {
    console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
}).catch((error: BusinessError) => {
    console.error('queryPrintJobList failed, error : ' + JSON.stringify(error));
})

```

