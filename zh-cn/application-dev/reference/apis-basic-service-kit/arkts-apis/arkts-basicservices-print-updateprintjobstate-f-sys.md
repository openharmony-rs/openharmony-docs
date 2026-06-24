# updatePrintJobState（系统接口）

## updatePrintJobState

```TypeScript
function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState,
    callback: AsyncCallback<void>): void
```

更新打印任务状态，使用callback异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB, ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| state | PrintJobState | 是 | 表示打印任务状态。 |
| subState | PrintJobSubState | 是 | 表示打印任务子状态。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步更新打印任务状态之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-not) | not system application&lt;br&gt;**适用版本：** 10 - 23 |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = 'jobId';
let state : print.PrintJobState = print.PrintJobState.PRINT_JOB_PREPARE;
let subState : print.PrintJobSubState = print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS;
print.updatePrintJobState(jobId, state, subState, (err: BusinessError) => {
    if (err) {
        console.error('updatePrintJobState failed, because : ' + JSON.stringify(err));
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

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB, ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| state | PrintJobState | 是 | 表示打印任务状态。 |
| subState | PrintJobSubState | 是 | 表示打印任务子状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-not) | not system application&lt;br&gt;**适用版本：** 10 - 23 |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = 'jobId';
let state : print.PrintJobState = print.PrintJobState.PRINT_JOB_PREPARE;
let subState : print.PrintJobSubState = print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS;
print.updatePrintJobState(jobId, state, subState).then(() => {
    console.info('update print job state success');
}).catch((error: BusinessError) => {
    console.error('update print job state error : ' + JSON.stringify(error));
})

```

