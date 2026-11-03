# openScanner

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## openScanner

```TypeScript
function openScanner(scannerId: string): Promise<void>
```

打开扫描仪。需在调用init()完成初始化后使用。使用Promise异步回调。在使用完毕后，需调用closeScanner()关闭扫描仪，释放资源。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function openScanner(scannerId: string): Promise<void>--><!--Device-scan-function openScanner(scannerId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 要打开的扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，打开扫描仪成功时resolve，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.openScanner(scannerId).then(() => {
    console.info('open scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to open scanner. Code: ${error.code}, message: ${error.message}`);
});
```
