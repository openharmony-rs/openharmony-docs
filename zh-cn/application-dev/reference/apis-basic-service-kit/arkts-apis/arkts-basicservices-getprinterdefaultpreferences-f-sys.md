# getPrinterDefaultPreferences（系统接口）

## getPrinterDefaultPreferences

```TypeScript
function getPrinterDefaultPreferences(printerId: string): Promise<PrinterPreferences>
```

按打印机ID获取默认首选项。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 打印机ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PrinterPreferences&gt; | - Promise that resolves with the default preferences of the printer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [13100005](../../apis-basic-services-kit/errorcode-print.md#13100005-无效的打印机) | Can not find the printer or printer's ppd file in system. |

