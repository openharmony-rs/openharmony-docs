# getAddedPrinters

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## getAddedPrinters

```TypeScript
function getAddedPrinters(): Promise<Array<string>>
```

获取系统中已添加的打印机列表，使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT

<!--Device-print-function getAddedPrinters(): Promise<Array<string>>--><!--Device-print-function getAddedPrinters(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回包含所有已添加打印机的打印机ID的列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.getAddedPrinters().then((printers: string[]) => {
    console.info('getAddedPrinters success ' + JSON.stringify(printers));
    // ...
}).catch((error: BusinessError) => {
    console.error('failed to getAddedPrinters because ' + JSON.stringify(error));
})

```

