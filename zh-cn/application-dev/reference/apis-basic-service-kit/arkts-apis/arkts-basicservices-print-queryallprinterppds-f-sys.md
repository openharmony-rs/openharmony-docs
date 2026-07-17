# queryAllPrinterPpds（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryAllPrinterPpds

```TypeScript
function queryAllPrinterPpds(): Promise<PpdInfo[]>
```

查询所有打印机ppd。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function queryAllPrinterPpds(): Promise<PpdInfo[]>--><!--Device-print-function queryAllPrinterPpds(): Promise<PpdInfo[]>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PpdInfo[]> | - Promise that resolves with all printer ppd info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |

