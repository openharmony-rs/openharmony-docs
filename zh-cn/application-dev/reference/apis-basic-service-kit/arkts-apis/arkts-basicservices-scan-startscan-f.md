# startScan

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## startScan

```TypeScript
function startScan(scannerId: string, batchMode: boolean): Promise<void>
```

开始扫描。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function startScan(scannerId: string, batchMode: boolean): Promise<void>--><!--Device-scan-function startScan(scannerId: string, batchMode: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 扫描仪的ID。 |
| batchMode | boolean | 是 | 是否使用批处理模式。true表示使用批处理模式，false表示不使用批处理模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
let batchMode: boolean = true;
scan.startScan(scannerId, batchMode).then(() => {
    console.info('start scan success');
}).catch((error: BusinessError) => {
    console.error('start scan failed: ' + JSON.stringify(error));
})

```

