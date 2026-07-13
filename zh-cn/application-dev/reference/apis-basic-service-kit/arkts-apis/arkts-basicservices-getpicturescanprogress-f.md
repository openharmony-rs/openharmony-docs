# getPictureScanProgress

## getPictureScanProgress

```TypeScript
function getPictureScanProgress(scannerId: string): Promise<PictureScanProgress>
```

获取图片扫描进度。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scannerId | string | 是 | 扫描仪的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PictureScanProgress&gt; | Promise对象，返回图片扫描进度信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let scannerId: string = 'scanner_001';
scan.getPictureScanProgress(scannerId).then((progress: scan.PictureScanProgress) => {
    console.info('get picture scan progress success: ' + JSON.stringify(progress));
}).catch((error: BusinessError) => {
    console.error('get picture scan progress failed: ' + JSON.stringify(error));
})

```

