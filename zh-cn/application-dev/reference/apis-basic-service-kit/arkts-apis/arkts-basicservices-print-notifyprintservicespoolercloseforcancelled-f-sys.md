# notifyPrintServiceSpoolerCloseForCancelled（系统接口）

## notifyPrintServiceSpoolerCloseForCancelled

```TypeScript
function notifyPrintServiceSpoolerCloseForCancelled(jobId: string, callback: AsyncCallback<void>): void
```

Notify print service the information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function notifyPrintServiceSpoolerCloseForCancelled(jobId: string, callback: AsyncCallback<void>): void--><!--Device-print-function notifyPrintServiceSpoolerCloseForCancelled(jobId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | Indicates id of the print job. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | The callback function for indcating the result of API execution. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |


## notifyPrintServiceSpoolerCloseForCancelled

```TypeScript
function notifyPrintServiceSpoolerCloseForCancelled(jobId: string): Promise<void>
```

Notify print service the information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function notifyPrintServiceSpoolerCloseForCancelled(jobId: string): Promise<void>--><!--Device-print-function notifyPrintServiceSpoolerCloseForCancelled(jobId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | Indicates id of the print job. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

