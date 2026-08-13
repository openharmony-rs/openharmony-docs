# addPrinterToDiscovery

## addPrinterToDiscovery

```TypeScript
function addPrinterToDiscovery(printerInformation: PrinterInformation): Promise<void>
```

添加打印机到系统打印机发现列表，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-print-function addPrinterToDiscovery(printerInformation: PrinterInformation): Promise<void>--><!--Device-print-function addPrinterToDiscovery(printerInformation: PrinterInformation): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerInformation | [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | 是 | 表示新发现的打印机。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';

let printerInformation : print.PrinterInformation = {
    printerId : 'testPrinterId',
    printerName : 'testPrinterName',
    printerStatus : 0,
    description : 'testDesc',
    uri : 'testUri',
    printerMake : 'testPrinterMake',
    options : 'testOps'
};
print.addPrinterToDiscovery(printerInformation).then(() => {
    console.info('addPrinterToDiscovery success');
}).catch((error: BusinessError) => {
    console.error('addPrinterToDiscovery error : ' + JSON.stringify(error));
})
```

