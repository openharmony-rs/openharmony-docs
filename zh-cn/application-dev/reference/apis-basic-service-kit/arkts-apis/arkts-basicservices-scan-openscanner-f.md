# openScanner

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

<a id="openscanner"></a>
## openScanner

```TypeScript
function openScanner(scannerId: string): Promise<void>
```

打开扫描仪。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function openScanner(scannerId: string): Promise<void>--><!--Device-scan-function openScanner(scannerId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 要打开的扫描仪的ID。 |

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
scan.openScanner(scannerId).then(() => {
    console.info('open scanner success');
}).catch((error: BusinessError) => {
    console.error('open scanner failed: ' + JSON.stringify(error));
})

```

