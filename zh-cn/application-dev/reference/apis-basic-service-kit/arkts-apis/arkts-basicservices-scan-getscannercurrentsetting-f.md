# getScannerCurrentSetting

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## getScannerCurrentSetting

```TypeScript
function getScannerCurrentSetting(scannerId: string, optionIndex: number): Promise<ScannerOptionValue>
```

获取当前扫描仪设置。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function getScannerCurrentSetting(scannerId: string, optionIndex: int): Promise<ScannerOptionValue>--><!--Device-scan-function getScannerCurrentSetting(scannerId: string, optionIndex: int): Promise<ScannerOptionValue>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 扫描仪的ID。 |
| optionIndex | number | 是 | 要获取的选项的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ScannerOptionValue> | Promise对象，返回扫描仪选项值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
scan.getScannerCurrentSetting(scannerId, optionIndex).then((value: scan.ScannerOptionValue) => {
    console.info('get scanner current setting success: ' + JSON.stringify(value));
}).catch((error: BusinessError) => {
    console.error('get scanner current setting failed: ' + JSON.stringify(error));
})

```

