# onJobStateChange（系统接口）

## onJobStateChange

```TypeScript
function onJobStateChange(callback: PrintJobStateChangeCallback): void
```

Register event callback for the state change of print job.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function onJobStateChange(callback: PrintJobStateChangeCallback): void--><!--Device-print-function onJobStateChange(callback: PrintJobStateChangeCallback): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PrintJobStateChangeCallback](arkts-basicservices-print-printjobstatechangecallback-t-sys.md) | 是 | The callback function for state change of printer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

