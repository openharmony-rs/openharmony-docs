# startScannerDiscovery

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## startScannerDiscovery

```TypeScript
function startScannerDiscovery(): Promise<void>
```

开始发现扫描仪。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function startScannerDiscovery(): Promise<void>--><!--Device-scan-function startScannerDiscovery(): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.startScannerDiscovery().then(() => {
    console.info('start scanner discovery success');
}).catch((error: BusinessError) => {
    console.error('start scanner discovery failed: ' + JSON.stringify(error));
})

```

