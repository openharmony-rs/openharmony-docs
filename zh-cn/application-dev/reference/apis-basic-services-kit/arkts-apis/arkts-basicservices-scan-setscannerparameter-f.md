# setScannerParameter

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## setScannerParameter

```TypeScript
function setScannerParameter(scannerId: string, optionIndex: number, value: ScannerOptionValue): Promise<void>
```

设置扫描仪参数。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function setScannerParameter(scannerId: string, optionIndex: int, value: ScannerOptionValue): Promise<void>--><!--Device-scan-function setScannerParameter(scannerId: string, optionIndex: int, value: ScannerOptionValue): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 要设置参数的扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |
| optionIndex | number | 是 | 要设置的选项的索引，可通过getScannerParameter()获取。 |
| value | [ScannerOptionValue](arkts-basicservices-scan-scanneroptionvalue-i.md) | 是 | 要设置的扫描仪选项值，包含值类型（valueType）及对应的数值（numValue）、字符串值（strValue）或布尔值（boolValue）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，设置扫描仪参数成功时resolve，失败时reject。 |

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
let value: scan.ScannerOptionValue = {
    valueType: scan.OptionValueType.SCAN_TYPE_INT,
    numValue: 100
};
scan.setScannerParameter(scannerId, optionIndex, value).then(() => {
    console.info('set scanner parameter success');
}).catch((error: BusinessError) => {
    console.error(`Failed to set scanner parameter. Code: ${error.code}, message: ${error.message}`);
});
```
