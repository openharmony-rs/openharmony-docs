# updatePrintJobState（系统接口）

## updatePrintJobState

```TypeScript
function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState,
    callback: AsyncCallback<void>): void
```

更新打印任务状态，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本24+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT
- API版本10 - 23：ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState,    callback: AsyncCallback<void>): void--><!--Device-print-function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState,    callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| state | [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | 是 | 表示打印任务状态。 |
| subState | [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | 是 | 表示打印任务子状态。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 异步更新打印任务状态之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 23 |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';

let jobId : string = 'jobId';
let state : print.PrintJobState = print.PrintJobState.PRINT_JOB_PREPARE;
let subState : print.PrintJobSubState = print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS;
print.updatePrintJobState(jobId, state, subState, (err: BusinessError) => {
    if (err) {
        console.error('updataPrintJobState failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updatePrintJobState success');
    }
})
```


## updatePrintJobState

```TypeScript
function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState): Promise<void>
```

更新打印任务状态，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本24+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT
- API版本10 - 23：ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState): Promise<void>--><!--Device-print-function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| state | [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | 是 | 表示打印任务状态。 |
| subState | [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | 是 | 表示打印任务子状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 23 |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';

let jobId : string = 'jobId';
let state : print.PrintJobState = print.PrintJobState.PRINT_JOB_PREPARE;
let subState : print.PrintJobSubState = print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS;
print.updatePrintJobState(jobId, state, subState).then(() => {
    console.info('update print job state success');
}).catch((error: BusinessError) => {
    console.error('update print job state error : ' + JSON.stringify(error));
})
```

