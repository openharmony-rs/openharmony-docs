# updatePrinterState（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="updateprinterstate"></a>
## updatePrinterState

```TypeScript
function updatePrinterState(printerId: string, state: PrinterState, callback: AsyncCallback<void>): void
```

更新打印机状态，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function updatePrinterState(printerId: string, state: PrinterState, callback: AsyncCallback<void>): void--><!--Device-print-function updatePrinterState(printerId: string, state: PrinterState, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 表示打印机ID。 |
| state | [PrinterState](arkts-basicservices-print-printerstate-e.md) | 是 | 表示打印机状态。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步更新打印机状态之后的回调。 |

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

let printerId : string = '1212';
let state : print.PrinterState = print.PrinterState.PRINTER_CONNECTED;
print.updatePrinterState(printerId, state, (err: BusinessError) => {
    if (err) {
        console.error('updatePrinterState failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updatePrinterState success');
    }
})

```


<a id="updateprinterstate-1"></a>
## updatePrinterState

```TypeScript
function updatePrinterState(printerId: string, state: PrinterState): Promise<void>
```

更新打印机状态，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function updatePrinterState(printerId: string, state: PrinterState): Promise<void>--><!--Device-print-function updatePrinterState(printerId: string, state: PrinterState): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 表示打印机ID。 |
| state | [PrinterState](arkts-basicservices-print-printerstate-e.md) | 是 | 表示打印机状态。 |

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

let printerId : string = '1212';
let state : print.PrinterState = print.PrinterState.PRINTER_CONNECTED;
print.updatePrinterState(printerId, state).then(() => {
    console.info('update printer state success');
}).catch((error: BusinessError) => {
    console.error('update printer state error : ' + JSON.stringify(error));
})

```

