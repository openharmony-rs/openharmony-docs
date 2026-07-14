# addPrinter

## addPrinter

```TypeScript
function addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise<boolean>
```

添加打印机到系统中，使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINTER_DRIVER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerName | string | 是 | 表示打印机名称。 |
| uri | string | 是 | 表示打印机的URI。 |
| ppdName | string | 否 | 表示打印机的PPD文件名称。 |
| options | string | 否 | JSON对象字符串，表示打印机选项参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回添加打印机成功与否的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [13100003](../../apis-basic-services-kit/errorcode-print.md#13100003-打印服务异常) | Add the printer to system failed. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerName : string = 'printerName';
let uri : string = 'uri';
let ppdName : string = 'ppdName';
print.addPrinter(printerName, uri, ppdName).then(() => {
    console.info('add printer success');
}).catch((error: BusinessError) => {
    console.error('add printer error : ' + JSON.stringify(error));
})

```

