# cancelScan

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## cancelScan

```TypeScript
function cancelScan(scannerId: string): Promise<void>
```

取消扫描。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function cancelScan(scannerId: string): Promise<void>--><!--Device-scan-function cancelScan(scannerId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 扫描仪的ID。 |

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
scan.cancelScan(scannerId).then(() => {
    console.info('cancel scan success');
}).catch((error: BusinessError) => {
    console.error('cancel scan failed: ' + JSON.stringify(error));
})

```

