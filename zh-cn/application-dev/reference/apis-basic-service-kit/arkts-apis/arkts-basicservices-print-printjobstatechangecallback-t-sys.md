# PrintJobStateChangeCallback（系统接口）

```TypeScript
type PrintJobStateChangeCallback = (state: PrintJobState, job: PrintJob) => void
```

Defines the callback type used in registering to listen for PrintJobState. The value of state indicates the state of print job. The value of job indicates the latest print job info.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-print-type PrintJobStateChangeCallback = (state: PrintJobState, job: PrintJob) => void--><!--Device-print-type PrintJobStateChangeCallback = (state: PrintJobState, job: PrintJob) => void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the state of print job  |
| job | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the information of the print job  |

