# @ohos.scan (扫描)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester:@baozewei-->
<!--Adviser: @fang-jinxu-->

该模块为扫描框架的 js-api 接口文档，提供发现、添加、删除扫描仪以及获取已添加扫描仪列表的能力，同时支持监听扫描仪设备的添加和删除事件，适用于需要在应用内集成扫描仪设备管理并实时感知设备状态变化的场景。扫描框架通过发现模式发现扫描仪设备，添加设备后可通过事件监听设备的添加和删除状态，完成扫描任务后可删除设备，帮助开发者便捷地完成扫描仪的接入与生命周期管理。

> **说明：**  
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 当前界面仅包含本模块的系统接口，其他公开接口参见[@ohos.scan (扫描)](./js-apis-scan.md)。

## 导入模块

```ts
import { scan } from '@kit.BasicServicesKit';
```
## scan.addScanner

addScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise&lt;void&gt;

添加扫描仪（系统接口）。根据指定的发现模式发现并添加扫描仪设备，添加成功后将触发scanDeviceAdd事件通知。使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| uniqueId | string | 是 | 扫描仪的唯一ID，可通过getAddedScanners()获取或从scan.on('scanDeviceAdd')事件回调中获得。 |
| discoveryMode | [ScannerDiscoveryMode](./js-apis-scan.md#scannerdiscoverymode) | 是 | 扫描仪的发现模式，不同模式适用于不同的扫描仪发现场景。 |

**返回值：**

| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象。resolve表示接口调用成功，reject表示接口调用失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// uniqueId可通过getAddedScanners()获取已添加扫描仪的唯一ID，或从scan.on('scanDeviceAdd')事件回调中获得
let uniqueId: string = 'unique_scanner_001';
let discoveryMode: scan.ScannerDiscoveryMode = scan.ScannerDiscoveryMode.TCP_STR;
scan.addScanner(uniqueId, discoveryMode).then(() => {
    console.info('add scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to add scanner. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.deleteScanner

deleteScanner(uniqueId: string, discoveryMode: ScannerDiscoveryMode): Promise&lt;void&gt;

删除扫描仪（系统接口）。适用于扫描仪设备离线或不再需要时移除设备的场景，删除成功后将触发scanDeviceDel事件通知，可通过on('scanDeviceDel')监听设备删除事件。使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| uniqueId | string | 是 | 扫描仪的唯一ID，可通过getAddedScanners()获取或从scan.on('scanDeviceAdd')事件回调中获得。 |
| discoveryMode | [ScannerDiscoveryMode](./js-apis-scan.md#scannerdiscoverymode) | 是 | 扫描仪的发现模式，需与添加该扫描仪时使用的发现模式保持一致。 |

**返回值：**

| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象。resolve表示接口调用成功，reject表示接口调用失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// uniqueId可通过getAddedScanners()获取已添加扫描仪的唯一ID，或从scan.on('scanDeviceAdd')事件回调中获得
let uniqueId: string = 'unique_scanner_001';
let discoveryMode: scan.ScannerDiscoveryMode = scan.ScannerDiscoveryMode.TCP_STR;
scan.deleteScanner(uniqueId, discoveryMode).then(() => {
    console.info('delete scanner success');
}).catch((error: BusinessError) => {
    console.error(`Failed to delete scanner. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.getAddedScanners

getAddedScanners(): Promise&lt;ScannerDevice[]&gt;

获取已添加的扫描仪（系统接口）。适用于需要查询当前可用扫描仪列表以供用户选择设备的场景。使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| **类型** | **说明** |
| -------- | -------- |
| Promise&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)[]&gt; | Promise对象。resolve返回已添加的扫描仪设备数组，reject表示获取扫描仪设备失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

scan.getAddedScanners().then((scanners: scan.ScannerDevice[]) => {
    console.info('get added scanners success: ' + JSON.stringify(scanners));
}).catch((error: BusinessError) => {
    console.error(`Failed to get added scanners. Code: ${error.code}, message: ${error.message}`);
});
```

## scan.on

on(type: 'scanDeviceAdd', callback: Callback&lt;ScannerDevice&gt;): void

注册扫描仪设备添加事件回调（系统接口）。当扫描仪设备被成功添加时触发此回调，返回添加的设备信息。使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceAdd' | 是 | 事件类型。 |
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | 是 | 扫描仪设备添加事件的回调函数，当有扫描仪设备添加时触发，返回添加的扫描仪设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceAdd', (device: scan.ScannerDevice) => {
    console.info('scan device add: ' + JSON.stringify(device));
});
```

## scan.off

off(type: 'scanDeviceAdd', callback?: Callback&lt;ScannerDevice&gt;): void

取消注册扫描仪设备添加事件回调（系统接口）。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceAdd' | 是 | 事件类型。 |
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | 否 | 需要取消注册的回调函数。若不传入，则取消调用方所有已注册的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device add: ' + JSON.stringify(device));
};
scan.on('scanDeviceAdd', callback);
// 取消注册
scan.off('scanDeviceAdd', callback);
```

## scan.on

on(type: 'scanDeviceDel', callback: Callback&lt;ScannerDevice&gt;): void

注册扫描仪设备删除事件回调（系统接口）。当扫描仪设备被删除时触发此回调，返回删除的设备信息。使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceDel' | 是 | 事件类型。 |
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | 是 | 扫描仪设备删除事件的回调函数，当有扫描仪设备删除时触发，返回删除的扫描仪设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';

scan.on('scanDeviceDel', (device: scan.ScannerDevice) => {
    console.info('scan device delete: ' + JSON.stringify(device));
});
```

## scan.off

off(type: 'scanDeviceDel', callback?: Callback&lt;ScannerDevice&gt;): void

取消注册扫描仪设备删除事件回调（系统接口）。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| type | 'scanDeviceDel' | 是 | 事件类型。 |
| callback | Callback&lt;[ScannerDevice](./js-apis-scan.md#scannerdevice)&gt; | 否 | 需要取消注册的回调函数。若不传入，则取消调用方所有已注册的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**示例：**

```ts
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device delete: ' + JSON.stringify(device));
};
scan.on('scanDeviceDel', callback);
// 取消注册
scan.off('scanDeviceDel', callback);
```