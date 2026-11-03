# getScannerCurrentSetting

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## getScannerCurrentSetting

```TypeScript
function getScannerCurrentSetting(scannerId: string, optionIndex: number): Promise<ScannerOptionValue>
```

获取当前扫描仪设置。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function getScannerCurrentSetting(scannerId: string, optionIndex: int): Promise<ScannerOptionValue>--><!--Device-scan-function getScannerCurrentSetting(scannerId: string, optionIndex: int): Promise<ScannerOptionValue>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 要获取当前设置的扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |
| optionIndex | number | 是 | 要获取的选项的索引，可通过getScannerParameter()获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ScannerOptionValue](arkts-basicservices-scan-scanneroptionvalue-i.md)&gt; | Promise对象，获取当前扫描仪设置成功时resolve并返回扫描仪选项值，失败时reject。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
scan.getScannerCurrentSetting(scannerId, optionIndex).then((value: scan.ScannerOptionValue) => {
    console.info('get scanner current setting success: ' + JSON.stringify(value));
}).catch((error: BusinessError) => {
    console.error(`Failed to get scanner current setting. Code: ${error.code}, message: ${error.message}`);
});
```
