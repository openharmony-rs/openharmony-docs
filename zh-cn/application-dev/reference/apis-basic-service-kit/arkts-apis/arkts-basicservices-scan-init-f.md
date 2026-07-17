# init

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## init

```TypeScript
function init(): Promise<void>
```

初始化扫描服务。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function init(): Promise<void>--><!--Device-scan-function init(): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.init().then(() => {
    console.info('scan init success');
}).catch((error: BusinessError) => {
    console.error('scan init failed: ' + JSON.stringify(error));
})

```

