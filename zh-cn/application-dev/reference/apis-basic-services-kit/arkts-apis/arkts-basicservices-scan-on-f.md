# on

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## on('scanDeviceFound')

```TypeScript
function on(type: 'scanDeviceFound', callback: Callback<ScannerDevice>): void
```

注册扫描仪设备发现事件回调，当调用startScannerDiscovery发现新的扫描仪设备时会触发此事件。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function on(type: 'scanDeviceFound', callback: Callback<ScannerDevice>): void--><!--Device-scan-function on(type: 'scanDeviceFound', callback: Callback<ScannerDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scanDeviceFound' | 是 | 事件类型。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md)&gt; | 是 | 回调函数，返回扫描仪设备发现信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceFound', (device: scan.ScannerDevice) => {
    console.info('scan device found: ' + JSON.stringify(device));
});
```


## on('scanDeviceSync')

```TypeScript
function on(type: 'scanDeviceSync', callback: Callback<ScannerSyncDevice>): void
```

注册扫描仪设备同步事件回调，当扫描仪设备状态发生变化（如扫描仪设备ID变更或掉线）时会触发此事件，通知应用同步维护扫描仪列表。使用callback异步回调。适用于应用需要持续跟踪扫描仪设备状态变化的场景，如扫描仪重新连接时更新本地设备信息。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function on(type: 'scanDeviceSync', callback: Callback<ScannerSyncDevice>): void--><!--Device-scan-function on(type: 'scanDeviceSync', callback: Callback<ScannerSyncDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scanDeviceSync' | 是 | 事件类型。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ScannerSyncDevice](arkts-basicservices-scan-scannersyncdevice-i.md)&gt; | 是 | 回调函数，返回扫描仪设备同步信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceSync', (device: scan.ScannerSyncDevice) => {
    console.info('scan device sync: ' + JSON.stringify(device));
});
```
