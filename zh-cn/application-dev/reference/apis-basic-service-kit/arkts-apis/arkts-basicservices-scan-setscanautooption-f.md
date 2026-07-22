# setScanAutoOption

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## setScanAutoOption

```TypeScript
function setScanAutoOption(scannerId: string, optionIndex: number): Promise<void>
```

设置扫描选项为自动模式。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function setScanAutoOption(scannerId: string, optionIndex: int): Promise<void>--><!--Device-scan-function setScanAutoOption(scannerId: string, optionIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 扫描仪的ID。 |
| optionIndex | number | 是 | 要设置为自动的选项的索引。 |

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

let scannerId: string = 'scanner_001';
let optionIndex: number = 1;
scan.setScanAutoOption(scannerId, optionIndex).then(() => {
    console.info('set scan auto option success');
}).catch((error: BusinessError) => {
    console.error('set scan auto option failed: ' + JSON.stringify(error));
})

```

