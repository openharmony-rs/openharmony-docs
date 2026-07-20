# queryAllActivePrintJobs（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="queryallactiveprintjobs"></a>
## queryAllActivePrintJobs

```TypeScript
function queryAllActivePrintJobs(): Promise<PrintJob[]>
```

查询所有活跃中的打印任务，使用Promise进行异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function queryAllActivePrintJobs(): Promise<PrintJob[]>--><!--Device-print-function queryAllActivePrintJobs(): Promise<PrintJob[]>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PrintJob[]&gt; | Promise used to return a list of all active print jobs. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

