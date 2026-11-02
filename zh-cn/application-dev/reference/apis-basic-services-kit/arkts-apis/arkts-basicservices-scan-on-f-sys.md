# on（系统接口）

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## on('scanDeviceAdd')

```TypeScript
function on(type: 'scanDeviceAdd', callback: Callback<ScannerDevice>): void
```

注册扫描仪设备添加事件回调（系统接口）。当扫描仪设备被成功添加时触发此回调，返回添加的设备信息。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function on(type: 'scanDeviceAdd', callback: Callback<ScannerDevice>): void--><!--Device-scan-function on(type: 'scanDeviceAdd', callback: Callback<ScannerDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scanDeviceAdd' | 是 | 事件类型。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md)&gt; | 是 | 扫描仪设备添加事件的回调函数，当有扫描仪设备添加时触发，返回添加的扫描仪设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application. |

<!--Del-->
**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceAdd', (device: scan.ScannerDevice) => {
    console.info('scan device add: ' + JSON.stringify(device));
});
```

<!--DelEnd-->


## on('scanDeviceDel')

```TypeScript
function on(type: 'scanDeviceDel', callback: Callback<ScannerDevice>): void
```

注册扫描仪设备删除事件回调（系统接口）。当扫描仪设备被删除时触发此回调，返回删除的设备信息。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function on(type: 'scanDeviceDel', callback: Callback<ScannerDevice>): void--><!--Device-scan-function on(type: 'scanDeviceDel', callback: Callback<ScannerDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scanDeviceDel' | 是 | 事件类型。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md)&gt; | 是 | 扫描仪设备删除事件的回调函数，当有扫描仪设备删除时触发，返回删除的扫描仪设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application. |

<!--Del-->
**示例**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceDel', (device: scan.ScannerDevice) => {
    console.info('scan device delete: ' + JSON.stringify(device));
});
```

<!--DelEnd-->
