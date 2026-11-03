# closeScanner

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## closeScanner

```TypeScript
function closeScanner(scannerId: string): Promise<void>
```

关闭扫描仪。使用Promise异步回调。扫描仪关闭后，将不能再对该扫描仪执行参数获取、设置、扫描等操作。如需再次使用需重新调用openScanner()。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function closeScanner(scannerId: string): Promise<void>--><!--Device-scan-function closeScanner(scannerId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 要关闭的扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，关闭扫描仪成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.closeScanner(scannerId).then(() => {
    console.info('close scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to close scanner. Code: ${error.code}, message: ${error.message}`);
});
```
