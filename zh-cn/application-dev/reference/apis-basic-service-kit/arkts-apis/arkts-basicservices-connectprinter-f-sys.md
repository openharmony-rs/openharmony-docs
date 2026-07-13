# connectPrinter（系统接口）

## connectPrinter

```TypeScript
function connectPrinter(printerId: string, callback: AsyncCallback<void>): void
```

通过打印机ID连接打印机，使用callback异步回调。

**起始版本：** 20

**需要权限：** 
- API版本20+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT
- API版本10 - 19：ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 打印机ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 通过打印机ID异步连接打印机的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 19 |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.connectPrinter(printerId, (err: BusinessError) => {
    if (err) {
        console.error('failed to connect Printer because : ' + JSON.stringify(err));
    } else {
        console.info('start connect Printer success');
    }
})

```


## connectPrinter

```TypeScript
function connectPrinter(printerId: string): Promise<void>
```

通过打印机ID连接打印机，使用Promise异步回调。

**起始版本：** 20

**需要权限：** 
- API版本20+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT
- API版本10 - 19：ohos.permission.MANAGE_PRINT_JOB

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 打印机ID |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 19 |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.connectPrinter(printerId).then(() => {
    console.info('start connect Printer success');
}).catch((error: BusinessError) => {
    console.error('failed to connect Printer because : ' + JSON.stringify(error));
})

```

