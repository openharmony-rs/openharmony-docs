# savePdfFileJob（系统接口）

## savePdfFileJob

```TypeScript
function savePdfFileJob(jobId: string, fd: number): Promise<void>
```

保存打印作业的pdf文件。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 打印作业ID。 |
| fd | number | 是 | 文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [13100006](../../apis-basic-services-kit/errorcode-print.md#13100006-无效的打印任务) | Invalid job ID. |
| 13100007 | Save file failed. |

