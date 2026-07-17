# restartPrintJob（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## restartPrintJob

```TypeScript
function restartPrintJob(jobId: string): Promise<void>
```

重新打印之前打印过的打印任务，使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function restartPrintJob(jobId: string): Promise<void>--><!--Device-print-function restartPrintJob(jobId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 之前打印过的打印任务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '121212';
print.restartPrintJob(jobId).then(() => {
    console.info('restartPrintJob success');
}).catch((error: BusinessError) => {
    console.error('restartPrintJob failed, because : ' + JSON.stringify(error));
})

```

