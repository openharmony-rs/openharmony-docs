# deletePrinterFromCups（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## deletePrinterFromCups

```TypeScript
function deletePrinterFromCups(printerName: string): Promise<void>
```

从cups中删除打印机，使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function deletePrinterFromCups(printerName: string): Promise<void>--><!--Device-print-function deletePrinterFromCups(printerName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerName | string | 是 | 表示打印机名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerName : string = "testPrinterName";

print.deletePrinterFromCups(printerName).then(() => {
    console.info('deletePrinterFromCups success');
}).catch((error: BusinessError) => {
    console.error('deletePrinterFromCups error : ' + JSON.stringify(error));
})

```

