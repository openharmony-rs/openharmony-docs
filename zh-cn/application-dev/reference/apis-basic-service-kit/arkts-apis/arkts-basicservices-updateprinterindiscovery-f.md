# updatePrinterInDiscovery

## updatePrinterInDiscovery

```TypeScript
function updatePrinterInDiscovery(printerInformation: PrinterInformation): Promise<void>
```

更新打印机能力到系统打印机发现列表，使用Promise异步回调。

**起始版本：** 14

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerInformation | PrinterInformation | 是 | 表示待更新能力的打印机。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testPageSize : print.PrintPageSize = {
    id : 'ISO_A4',
    name : 'iso_a4_210x297mm',
    width : 8268,
    height : 11692
};

let testCapability : print.PrinterCapabilities = {
    supportedPageSizes : [testPageSize],
    supportedColorModes : [print.PrintColorMode.COLOR_MODE_MONOCHROME],
    supportedDuplexModes : [print.PrintDuplexMode.DUPLEX_MODE_NONE],
    supportedMediaTypes : ['stationery'],
    supportedQualities : [print.PrintQuality.QUALITY_NORMAL],
    supportedOrientations : [print.PrintOrientationMode.ORIENTATION_MODE_PORTRAIT],
    options : 'testOptions'
};

let printerInformation : print.PrinterInformation = {
    printerId : 'testPrinterId',
    printerName : 'testPrinterName',
    printerStatus : 0,
    description : 'testDesc',
    capability : testCapability,
    uri : 'testUri',
    printerMake : 'testPrinterMake',
    options : 'testOptions'
};
print.updatePrinterInDiscovery(printerInformation).then(() => {
    console.info('updatePrinterInDiscovery success');
}).catch((error: BusinessError) => {
    console.error('updatePrinterInDiscovery error : ' + JSON.stringify(error));
})

```

