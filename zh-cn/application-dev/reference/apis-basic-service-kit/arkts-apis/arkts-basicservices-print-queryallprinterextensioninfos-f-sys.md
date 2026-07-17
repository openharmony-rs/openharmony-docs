# queryAllPrinterExtensionInfos（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryAllPrinterExtensionInfos

```TypeScript
function queryAllPrinterExtensionInfos(callback: AsyncCallback<Array<PrinterExtensionInfo>>): void
```

查询所有已安装的打印机扩展服务，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function queryAllPrinterExtensionInfos(callback: AsyncCallback<Array<PrinterExtensionInfo>>): void--><!--Device-print-function queryAllPrinterExtensionInfos(callback: AsyncCallback<Array<PrinterExtensionInfo>>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<Array<PrinterExtensionInfo>> | 是 | 异步查询所有已安装的打印机扩展服务之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrinterExtensionInfos((err: BusinessError, extensionInfos: print.PrinterExtensionInfo[]) => {
    if (err) {
        console.error('queryAllPrinterExtensionInfos err ' + JSON.stringify(err));
    } else {
        console.info('queryAllPrinterExtensionInfos success ' + JSON.stringify(extensionInfos));
    }
})

```


## queryAllPrinterExtensionInfos

```TypeScript
function queryAllPrinterExtensionInfos(): Promise<Array<PrinterExtensionInfo>>
```

查询所有已安装的打印机扩展服务，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function queryAllPrinterExtensionInfos(): Promise<Array<PrinterExtensionInfo>>--><!--Device-print-function queryAllPrinterExtensionInfos(): Promise<Array<PrinterExtensionInfo>>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<PrinterExtensionInfo>> | Promise对象，返回包含所有已安装的打印机扩展服务信息的列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrinterExtensionInfos().then((extensionInfos: print.PrinterExtensionInfo[]) => {
    console.info('queryAllPrinterExtensionInfos success ' + JSON.stringify(extensionInfos));
    // ...
}).catch((error: BusinessError) => {
    console.error('failed to get AllPrinterExtension because ' + JSON.stringify(error));
})

```

