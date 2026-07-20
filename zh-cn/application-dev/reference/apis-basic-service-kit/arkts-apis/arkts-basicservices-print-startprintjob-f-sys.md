# startPrintJob（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="startprintjob"></a>
## startPrintJob

```TypeScript
function startPrintJob(jobInfo: PrintJob, callback: AsyncCallback<void>): void
```

开始打印任务，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function startPrintJob(jobInfo: PrintJob, callback: AsyncCallback<void>): void--><!--Device-print-function startPrintJob(jobInfo: PrintJob, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobInfo | [PrintJob](arkts-basicservices-print-printjob-i-sys.md) | 是 | 打印任务信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步开始打印任务之后的回调。 |

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

let jobInfo : print.PrintJob = {
    fdList : [44,45],
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : print.PrintJobState.PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : print.PrintColorMode.COLOR_MODE_COLOR,
    duplexMode : print.PrintDuplexMode.DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.startPrintJob(jobInfo, (err: BusinessError) => {
    if (err) {
        console.error('failed to start Print Job because : ' + JSON.stringify(err));
    } else {
        console.info('start Print Job success');
    }
})

```


<a id="startprintjob-1"></a>
## startPrintJob

```TypeScript
function startPrintJob(jobInfo: PrintJob): Promise<void>
```

开始打印任务，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function startPrintJob(jobInfo: PrintJob): Promise<void>--><!--Device-print-function startPrintJob(jobInfo: PrintJob): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobInfo | [PrintJob](arkts-basicservices-print-printjob-i-sys.md) | 是 | 打印任务信息。 |

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

let jobInfo : print.PrintJob = {
    fdList : [44,45],
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : print.PrintJobState.PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : print.PrintColorMode.COLOR_MODE_COLOR,
    duplexMode : print.PrintDuplexMode.DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.startPrintJob(jobInfo).then(() => {
    console.info('start Print success');
}).catch((error: BusinessError) => {
    console.error('failed to start Print because : ' + JSON.stringify(error));
})

```

