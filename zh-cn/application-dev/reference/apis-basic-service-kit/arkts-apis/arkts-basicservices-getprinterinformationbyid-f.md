# getPrinterInformationById

## getPrinterInformationById

```TypeScript
function getPrinterInformationById(printerId: string): Promise<PrinterInformation>
```

根据打印机id获取打印机信息，使用Promise异步回调。

**起始版本：** 14

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 表示待获取信息的打印机id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PrinterInformation&gt; | Promise对象，返回打印机信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = 'testPrinterId';
print.getPrinterInformationById(printerId).then((printerInformation : print.PrinterInformation) => {
    console.info('getPrinterInformationById data : ' + JSON.stringify(printerInformation));
}).catch((error: BusinessError) => {
    console.error('getPrinterInformationById error : ' + JSON.stringify(error));
})

```

