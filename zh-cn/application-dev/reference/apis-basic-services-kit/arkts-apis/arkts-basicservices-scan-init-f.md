# init

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## init

```TypeScript
function init(): Promise<void>
```

初始化扫描服务，必须在调用其它扫描接口前完成初始化。使用Promise异步回调。使用完毕后需调用exit()退出扫描服务，释放资源。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function init(): Promise<void>--><!--Device-scan-function init(): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，初始化扫描服务成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.init().then(() => {
    console.info('scan init success');
}).catch((error: BusinessError) => {
    console.error(`Failed to init scan. Code: ${error.code}, message: ${error.message}`);
});
```
