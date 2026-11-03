# getAddedScanners（系统接口）

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## getAddedScanners

```TypeScript
function getAddedScanners(): Promise<ScannerDevice[]>
```

获取已添加的扫描仪（系统接口）。适用于需要查询当前可用扫描仪列表以供用户选择设备的场景。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function getAddedScanners(): Promise<ScannerDevice[]>--><!--Device-scan-function getAddedScanners(): Promise<ScannerDevice[]>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md)[]&gt; | Promise对象。resolve返回已添加的扫描仪设备数组，reject表示获取扫描仪设备失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application. |

<!--Del-->
**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.getAddedScanners().then((scanners: scan.ScannerDevice[]) => {
    console.info('get added scanners success: ' + JSON.stringify(scanners));
}).catch((error: BusinessError) => {
    console.error(`Failed to get added scanners. Code: ${error.code}, message: ${error.message}`);
});
```

<!--DelEnd-->
