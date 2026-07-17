# updatePrinterInformation（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## updatePrinterInformation

```TypeScript
function updatePrinterInformation(printerInformation: PrinterInformation): Promise<void>
```

更新系统中打印机的部分信息，使用Promise异步回调。当前仅允许更新[PrinterInformation](arkts-basicservices-print-printerinformation-i.md)的alias和options字段。

**起始版本：** 24

**需要权限：** 
- API版本24+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT
- API版本18 - 23：ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function updatePrinterInformation(printerInformation: PrinterInformation): Promise<void>--><!--Device-print-function updatePrinterInformation(printerInformation: PrinterInformation): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerInformation | [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | 是 | 表示待更新信息的打印机。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 18 - 23 |
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
print.updatePrinterInformation(printerInformation).then(() => {
    console.info('updatePrinterInformation success');
}).catch((error: BusinessError) => {
    console.error('updatePrinterInformation error : ' + JSON.stringify(error));
})

```

