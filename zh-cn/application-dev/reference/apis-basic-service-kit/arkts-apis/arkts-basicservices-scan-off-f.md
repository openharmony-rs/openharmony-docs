# off

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## off('scanDeviceFound')

```TypeScript
function off(type: 'scanDeviceFound', callback?: Callback<ScannerDevice>): void
```

取消注册扫描仪设备发现事件回调。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.PRINT

<!--Device-scan-function off(type: 'scanDeviceFound', callback?: Callback<ScannerDevice>): void--><!--Device-scan-function off(type: 'scanDeviceFound', callback?: Callback<ScannerDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scanDeviceFound' | 是 | 事件类型。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ScannerDevice> | 否 | 回调函数，返回扫描仪设备发现信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device found: ' + JSON.stringify(device));
};
scan.on('scanDeviceFound', callback);
// 取消注册
scan.off('scanDeviceFound', callback);

```


## off('scanDeviceSync')

```TypeScript
function off(type: 'scanDeviceSync', callback?: Callback<ScannerSyncDevice>): void
```

取消注册扫描仪设备同步事件回调。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function off(type: 'scanDeviceSync', callback?: Callback<ScannerSyncDevice>): void--><!--Device-scan-function off(type: 'scanDeviceSync', callback?: Callback<ScannerSyncDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scanDeviceSync' | 是 | 事件类型。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ScannerSyncDevice> | 否 | 回调函数，返回扫描仪设备同步信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerSyncDevice) => {
    console.info('scan device sync: ' + JSON.stringify(device));
};
scan.on('scanDeviceSync', callback);
// 取消注册
scan.off('scanDeviceSync', callback);

```

