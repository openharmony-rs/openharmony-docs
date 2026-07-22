# authPrintJob（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## authPrintJob

```TypeScript
function authPrintJob(jobId: string, userName: string, password: string): Promise<boolean>
```

验证打印作业。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function authPrintJob(jobId: string, userName: string, password: string): Promise<boolean>--><!--Device-print-function authPrintJob(jobId: string, userName: string, password: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 打印作业ID。<br>要打印的作业ID。 |
| userName | string | 是 | 用户名。<br>用户名。 |
| password | string | 是 | 用户密码。<br>用户密码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [13100006](../../apis-basic-services-kit/errorcode-print.md#13100006-无效的打印任务) | Can not find the print job. |

