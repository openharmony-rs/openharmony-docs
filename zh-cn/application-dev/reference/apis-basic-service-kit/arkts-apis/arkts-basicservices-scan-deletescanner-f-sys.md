# deleteScanner（系统接口）

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

<a id="deletescanner"></a>
## deleteScanner

```TypeScript
function deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise<void>
```

删除扫描仪（系统API）。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise<void>--><!--Device-scan-function deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | string | 是 | 扫描仪的唯一ID。 |
| discoveryMode | [ScannerDiscoveryMode](arkts-basicservices-scan-scannerdiscoverymode-e.md) | 是 | 发现模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uniqueId: string = 'unique_scanner_001';
let discoveryMode: scan.ScannerDiscoveryMode = scan.ScannerDiscoveryMode.TCP_STR;
scan.deleteScanner(uniqueId, discoveryMode).then(() => {
    console.info('delete scanner success');
}).catch((error: BusinessError) => {
    console.error('delete scanner failed: ' + JSON.stringify(error));
})

```

