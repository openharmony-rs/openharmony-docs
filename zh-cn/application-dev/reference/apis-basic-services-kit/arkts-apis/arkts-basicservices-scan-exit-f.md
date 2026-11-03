# exit

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## exit

```TypeScript
function exit(): Promise<void>
```

退出扫描服务。使用Promise异步回调。扫描服务退出后，其它扫描方法将不可用，如需再次使用需重新调用init()。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function exit(): Promise<void>--><!--Device-scan-function exit(): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，退出扫描服务成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.exit().then(() => {
    console.info('scan exit success');
}).catch((error: BusinessError) => {
    console.error(`Failed to exit scan. Code: ${error.code}, message: ${error.message}`);
});
```
