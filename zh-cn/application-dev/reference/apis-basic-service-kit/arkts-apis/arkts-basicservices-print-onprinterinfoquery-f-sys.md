# onPrinterInfoQuery（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="onprinterinfoquery"></a>
## onPrinterInfoQuery

```TypeScript
function onPrinterInfoQuery(callback: PrinterInfoQueryCallback): void
```

为查询到的打印机信息注册事件回调。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function onPrinterInfoQuery(callback: PrinterInfoQueryCallback): void--><!--Device-print-function onPrinterInfoQuery(callback: PrinterInfoQueryCallback): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PrinterInfoQueryCallback](arkts-basicservices-print-printerinfoquerycallback-t-sys.md) | 是 | 查询到的打印机信息的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |

