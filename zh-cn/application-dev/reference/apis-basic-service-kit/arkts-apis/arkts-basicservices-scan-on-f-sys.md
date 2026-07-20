# on（系统接口）

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

<a id="on"></a>
## on('scanDeviceAdd')

```TypeScript
function on(type: 'scanDeviceAdd', callback: Callback<ScannerDevice>): void
```

注册扫描仪设备添加事件回调（系统API）。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function on(type: 'scanDeviceAdd', callback: Callback<ScannerDevice>): void--><!--Device-scan-function on(type: 'scanDeviceAdd', callback: Callback<ScannerDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scanDeviceAdd' | 是 | 事件类型。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ScannerDevice&gt; | 是 | 回调函数，返回扫描仪设备添加信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceAdd', (device: scan.ScannerDevice) => {
    console.info('scan device add: ' + JSON.stringify(device));
})

```


<a id="on-1"></a>
## on('scanDeviceDel')

```TypeScript
function on(type: 'scanDeviceDel', callback: Callback<ScannerDevice>): void
```

注册扫描仪设备删除事件回调（系统API）。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function on(type: 'scanDeviceDel', callback: Callback<ScannerDevice>): void--><!--Device-scan-function on(type: 'scanDeviceDel', callback: Callback<ScannerDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scanDeviceDel' | 是 | 事件类型。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ScannerDevice&gt; | 是 | 回调函数，返回扫描仪设备删除信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceDel', (device: scan.ScannerDevice) => {
    console.info('scan device delete: ' + JSON.stringify(device));
})

```

