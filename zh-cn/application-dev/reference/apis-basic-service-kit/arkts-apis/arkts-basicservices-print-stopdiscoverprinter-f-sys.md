# stopDiscoverPrinter（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## stopDiscoverPrinter

```TypeScript
function stopDiscoverPrinter(callback: AsyncCallback<void>): void
```

停止发现打印机，使用callback异步回调。

**起始版本：** 20

**需要权限：** 
- API版本20+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT
- API版本10 - 19：ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function stopDiscoverPrinter(callback: AsyncCallback<void>): void--><!--Device-print-function stopDiscoverPrinter(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 停止发现打印机的异步回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 19 |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.stopDiscoverPrinter((err: BusinessError) => {
    if (err) {
        console.error('failed to stop Discover Printer because : ' + JSON.stringify(err));
    } else {
        console.info('stop Discover Printer success');
    }
})

```


## stopDiscoverPrinter

```TypeScript
function stopDiscoverPrinter(): Promise<void>
```

停止发现打印机，使用Promise异步回调。

**起始版本：** 20

**需要权限：** 
- API版本20+：ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT
- API版本10 - 19：ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function stopDiscoverPrinter(): Promise<void>--><!--Device-print-function stopDiscoverPrinter(): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 19 |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.stopDiscoverPrinter().then(() => {
    console.info('stop Discovery success');
}).catch((error: BusinessError) => {
    console.error('failed to stop Discovery because : ' + JSON.stringify(error));
})

```

