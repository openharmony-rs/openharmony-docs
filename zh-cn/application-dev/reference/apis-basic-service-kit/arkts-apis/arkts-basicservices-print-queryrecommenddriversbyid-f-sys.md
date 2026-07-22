# queryRecommendDriversById（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryRecommendDriversById

```TypeScript
function queryRecommendDriversById(printerId: string): Promise<PpdInfo[]>
```

根据打印机ID查询推荐的打印机驱动程序。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function queryRecommendDriversById(printerId: string): Promise<PpdInfo[]>--><!--Device-print-function queryRecommendDriversById(printerId: string): Promise<PpdInfo[]>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | string | 是 | 打印机ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PpdInfo[]&gt; | - Promise that resolves with all ppd info of the printer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [13100005](../../apis-basic-services-kit/errorcode-print.md#13100005-无效的打印机) | Can not find the printer in system. |

