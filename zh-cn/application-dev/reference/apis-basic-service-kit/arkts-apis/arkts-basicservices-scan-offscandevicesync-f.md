# offScanDeviceSync

## offScanDeviceSync

```TypeScript
function offScanDeviceSync(callback?: Callback<ScannerSyncDevice>): void
```

Unregister event callback for scanner device sync.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function offScanDeviceSync(callback?: Callback<ScannerSyncDevice>): void--><!--Device-scan-function offScanDeviceSync(callback?: Callback<ScannerSyncDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[ScannerSyncDevice](arkts-basicservices-scan-scannersyncdevice-i.md)&gt; | 否 | Optional callback to unregister. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

```TypeScript
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerSyncDevice) => {
    console.info('scan device sync: ' + JSON.stringify(device));
};
scan.onScanDeviceSync(callback);
// 取消注册
scan.offScanDeviceSync(callback);
```

