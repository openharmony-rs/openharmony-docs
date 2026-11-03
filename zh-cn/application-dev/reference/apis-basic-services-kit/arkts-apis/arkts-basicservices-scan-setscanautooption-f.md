# setScanAutoOption

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## setScanAutoOption

```TypeScript
function setScanAutoOption(scannerId: string, optionIndex: number): Promise<void>
```

设置扫描选项为自动模式，由扫描仪自动确定该选项的取值。使用Promise异步回调。必须在调用openScanner()打开扫描仪之后才能调用此方法。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function setScanAutoOption(scannerId: string, optionIndex: int): Promise<void>--><!--Device-scan-function setScanAutoOption(scannerId: string, optionIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 扫描仪的ID，可以在startScannerDiscovery后通过scanDeviceFound回调获取。 |
| optionIndex | number | 是 | 要设置为自动的选项的索引，可通过getScannerParameter()获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，设置扫描选项为自动模式成功时resolve，失败时reject。 |

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
scan.setScanAutoOption(scannerId, optionIndex).then(() => {
    console.info('set scan auto option success');
}).catch((error: BusinessError) => {
    console.error(`Failed to set scan auto option. Code: ${error.code}, message: ${error.message}`);
});
```
