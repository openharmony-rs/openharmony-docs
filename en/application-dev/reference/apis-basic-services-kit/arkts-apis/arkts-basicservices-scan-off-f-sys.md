# off (System API)

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## off('scanDeviceAdd')

```TypeScript
function off(type: 'scanDeviceAdd', callback?: Callback<ScannerDevice>): void
```

Unregisters the callback used to listen for the scanner addition event. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'scanDeviceAdd' | Yes | Event type. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md)&gt; | No | Callback used to return the added scanner. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device add: ' + JSON.stringify(device));
};
scan.on('scanDeviceAdd', callback);
// Unregister the callback.
scan.off('scanDeviceAdd', callback);
```


## off('scanDeviceDel')

```TypeScript
function off(type: 'scanDeviceDel', callback?: Callback<ScannerDevice>): void
```

Unregisters the callback used to listen for the scanner deletion event. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'scanDeviceDel' | Yes | Event type. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md)&gt; | No | Callback used to return the deleted scanner. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { scan } from '@kit.BasicServicesKit';

let callback = (device: scan.ScannerDevice) => {
    console.info('scan device delete: ' + JSON.stringify(device));
};
scan.on('scanDeviceDel', callback);
// Unregister the callback.
scan.off('scanDeviceDel', callback);
```
