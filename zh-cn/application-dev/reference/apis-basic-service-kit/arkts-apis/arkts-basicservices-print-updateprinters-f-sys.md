# updatePrinters（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="updateprinters"></a>
## updatePrinters

```TypeScript
function updatePrinters(printers: Array<PrinterInfo>, callback: AsyncCallback<void>): void
```

更新特定打印机的信息，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function updatePrinters(printers: Array<PrinterInfo>, callback: AsyncCallback<void>): void--><!--Device-print-function updatePrinters(printers: Array<PrinterInfo>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printers | Array&lt;PrinterInfo&gt; | 是 | 表示待更新的打印机列表。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步更新打印机信息之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.updatePrinters([printerInfo], (err: BusinessError) => {
    if (err) {
        console.error('updatePrinters failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updatePrinters success');
    }
})

```


<a id="updateprinters-1"></a>
## updatePrinters

```TypeScript
function updatePrinters(printers: Array<PrinterInfo>): Promise<void>
```

更新特定打印机的信息，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function updatePrinters(printers: Array<PrinterInfo>): Promise<void>--><!--Device-print-function updatePrinters(printers: Array<PrinterInfo>): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printers | Array&lt;PrinterInfo&gt; | 是 | 表示待更新的打印机列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.updatePrinters([printerInfo]).then(() => {
    console.info('update printers success');
}).catch((error: BusinessError) => {
    console.error('update printers error : ' + JSON.stringify(error));
})

```

