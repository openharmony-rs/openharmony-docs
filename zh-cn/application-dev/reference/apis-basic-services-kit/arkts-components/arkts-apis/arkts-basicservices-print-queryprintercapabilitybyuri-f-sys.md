# queryPrinterCapabilityByUri（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryPrinterCapabilityByUri

```TypeScript
function queryPrinterCapabilityByUri(printerUri: string, printerId: string): Promise<PrinterCapabilities>
```

使用打印机的uri查询打印机能力，使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerUri | string | 是 | 表示打印机uri。 |
| printerId | string | 是 | 表示打印机ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md)&gt; | Promise对象，返回打印机能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [13100005](../errorcode-print.md#13100005-无效的打印机) | Can not find the printer in system. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// printerUri 可通过 discoverUsbPrinters 接口返回的 PrinterInformation 获取
let printerUri : string = 'testPrinterUri';
let printerId : string = 'testPrinterId';
print.queryPrinterCapabilityByUri(printerUri, printerId).then((capabilities: print.PrinterCapabilities) => {
    console.info('queryPrinterCapabilityByUri success' + JSON.stringify(capabilities));
}).catch((error: BusinessError) => {
    console.error(`Failed to query printer capability by uri. Code: ${error.code}, message: ${error.message}`);
});
```
