# connectPrinterByIdAndPpd（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## connectPrinterByIdAndPpd

```TypeScript
function connectPrinterByIdAndPpd(printerId: string, protocol: string, ppdName: string): Promise<void>
```

根据打印机ID和PPD连接打印机，使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function connectPrinterByIdAndPpd(printerId: string, protocol: string, ppdName: string): Promise<void>--><!--Device-print-function connectPrinterByIdAndPpd(printerId: string, protocol: string, ppdName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 待连接的打印机ID。 |
| protocol | string | 是 | 待连接的打印机的协议类型。 |
| ppdName | string | 是 | 待连接的打印机的PPD名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | not system application. |
| [13100003](../errorcode-print.md#13100003-打印服务异常) | Add the printer to system failed. |
