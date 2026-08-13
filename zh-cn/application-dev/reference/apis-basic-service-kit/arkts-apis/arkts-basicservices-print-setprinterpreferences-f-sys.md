# setPrinterPreferences（系统接口）

## setPrinterPreferences

```TypeScript
function setPrinterPreferences(printerId: string, printerPreferences: PrinterPreferences): Promise<void>
```

设置打印机首选项，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function setPrinterPreferences(printerId: string, printerPreferences: PrinterPreferences): Promise<void>--><!--Device-print-function setPrinterPreferences(printerId: string, printerPreferences: PrinterPreferences): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 表示打印机ID。 |
| printerPreferences | [PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md) | 是 | 表示打印机首选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';

let printerId : string = 'testPrinterId';
let preferences : print.PrinterPreferences = {
    defaultDuplexMode: print.PrintDuplexMode.DUPLEX_MODE_NONE
};
print.setPrinterPreferences(printerId, preferences).then(() => {
    console.info('setPrinterPreferences success');
}).catch((error: BusinessError) => {
    console.error('setPrinterPreferences error : ' + JSON.stringify(error));
})
```

