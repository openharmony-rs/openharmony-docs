# addPrinter

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## addPrinter

```TypeScript
function addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise<boolean>
```

添加打印机到系统中，使用Promise异步回调。该接口面向打印驱动、打印管理软件、三方打印管理软件、云打印等需要管理打印机或扫描仪的场景。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINTER_DRIVER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise<boolean>--><!--Device-print-function addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerName | string | 是 | 表示打印机名称。 |
| uri | string | 是 | 表示打印机的URI。 |
| ppdName | string | 否 | 表示打印机PPD驱动文件在文件系统中的名称。该名称由设备安装厂商驱动后生成，命名格式为“包名_模块名_文件名”，具体名称需向驱动厂商获取。当需要指定特定PPD驱动文件时传入此参数，不传入时系统自动匹配。 |
| options | string | 否 | JSON对象字符串，表示打印机选项参数。预留字段，暂未启用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回添加打印机成功与否的结果。true表示添加成功，false表示添加失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | the application does not have permission to call this function. |
| [13100003](../errorcode-print.md#13100003-打印服务异常) | Add the printer to system failed. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerName : string = 'printerName';
let uri : string = 'uri';
let ppdName : string = 'ppdName';
print.addPrinter(printerName, uri, ppdName).then(() => {
    console.info('add printer success');
}).catch((error: BusinessError) => {
    console.error(`Failed to addPrinter. Code: ${error.code}, message: ${error.message}`);
})
```
