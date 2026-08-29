# updatePrintJobState

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## updatePrintJobState

```TypeScript
function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState,
    callback: AsyncCallback<void>): void
```

更新打印任务状态，使用callback异步回调。

**起始版本：** 24

**需要权限：** 
- API版本24+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT
- API版本10 - 23：ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| state | [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | 是 | 表示打印任务状态。 |
| subState | [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | 是 | 表示打印任务子状态。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步更新打印任务状态之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 23 |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// jobId可通过打印扩展能力PrintExtensionAbility的onStartPrintJob回调获得
let jobId : string = 'jobId';
let state : print.PrintJobState = print.PrintJobState.PRINT_JOB_PREPARE;
let subState : print.PrintJobSubState = print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS;
print.updatePrintJobState(jobId, state, subState, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to updatePrintJobState. Code: ${error.code}, message: ${error.message}`);
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

**需要权限：** 
- API版本24+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT
- API版本10 - 23：ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| state | [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | 是 | 表示打印任务状态。 |
| subState | [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | 是 | 表示打印任务子状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 23 |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// jobId可通过打印扩展能力PrintExtensionAbility的onStartPrintJob回调获得
let jobId : string = 'jobId';
let state : print.PrintJobState = print.PrintJobState.PRINT_JOB_PREPARE;
let subState : print.PrintJobSubState = print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS;
print.updatePrintJobState(jobId, state, subState).then(() => {
    console.info('update print job state success');
}).catch((error: BusinessError) => {
    console.error(`Failed to updatePrintJobState. Code: ${error.code}, message: ${error.message}`);
})
```
