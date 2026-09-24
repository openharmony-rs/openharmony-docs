# BleScanner

```TypeScript
interface BleScanner
```

Manages the ble scanner. Before calling a ble scanner method, you must use [createBleScanner](arkts-connectivity-ble-createblescanner-f.md) to create an BleScanner instance.

**Since:** 15

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## off('BLEDeviceFind')

```TypeScript
off(type: 'BLEDeviceFind', callback?: Callback<ScanReport>): void
```

Unsubscribe BLE scan result.

**Since:** 15

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLEDeviceFind' | Yes | Type of the scan result event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScanReport](arkts-connectivity-ble-scanreport-i.md)&gt; | No | Callback used to listen for the scan result event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { ble } from '@kit.ConnectivityKit';
function onReceiveEvent(scanReport: ble.ScanReport) {
    console.info('bluetooth device find = '+ JSON.stringify(scanReport));
}
let bleScanner: ble.BleScanner = ble.createBleScanner();
try {
    bleScanner.on('BLEDeviceFind', onReceiveEvent);
    bleScanner.off('BLEDeviceFind', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## on('BLEDeviceFind')

```TypeScript
on(type: 'BLEDeviceFind', callback: Callback<ScanReport>): void
```

Subscribe BLE scan result. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual.

**Since:** 15

**Required permissions:** 
- API version 26 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 25: N/A
- API versions 15 to 24: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLEDeviceFind' | Yes | Type of the scan result event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScanReport](arkts-connectivity-ble-scanreport-i.md)&gt; | Yes | Callback used to listen for the scan result event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**Applicable version:** 15 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { ble } from '@kit.ConnectivityKit';
function onReceiveEvent(scanReport: ble.ScanReport) {
    console.info('bluetooth device find = '+ JSON.stringify(scanReport));
}
let bleScanner: ble.BleScanner = ble.createBleScanner();
try {
    bleScanner.on('BLEDeviceFind', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## startScan

```TypeScript
startScan(filters: Array<ScanFilter>, options?: ScanOptions): Promise<void>
```

Starts scanning for specified BLE devices with filters.

**Since:** 15

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filters | Array&lt;[ScanFilter](arkts-connectivity-ble-scanfilter-i.md)&gt; | Yes | Indicates the list of filters used to filter out specified devices. If you do not want to use filter, set this parameter to `null`. |
| options | [ScanOptions](arkts-connectivity-ble-scanoptions-i.md) | No | Indicates the parameters for scanning and if the user does not assign a value, the default value will be used. [interval](arkts-connectivity-ble-scanoptions-i.md#interval) set to 0, and [dutyMode](arkts-connectivity-ble-scanoptions-i.md#dutymode) set to [SCAN_MODE_LOW_POWER](arkts-connectivity-ble-scanduty-e.md#scan_mode_low_power) and [matchMode](arkts-connectivity-ble-scanoptions-i.md#matchmode) set to [MATCH_MODE_AGGRESSIVE](arkts-connectivity-ble-matchmode-e.md#match_mode_aggressive). and [phyType](arkts-connectivity-ble-scanoptions-i.md#phytype) set to [PHY_LE_ALL_SUPPORTED](arkts-connectivity-ble-phytype-e.md#phy_le_all_supported). and [reportMode](arkts-connectivity-ble-scanoptions-i.md#reportmode) set to [NORMAL](arkts-connectivity-ble-scanreportmode-e.md#normal). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900009 | Fails to start scan as it is out of hardware resources. |
| 2900099 | Operation failed. |
| 2902050 | Failed to start scan as Ble scan is already started by the app. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { ble } from '@kit.ConnectivityKit';
let bleScanner: ble.BleScanner = ble.createBleScanner();
function onReceiveEvent(scanReport: ble.ScanReport) {
    console.info('BLE scan device find result = '+ JSON.stringify(scanReport));
}
async function startscan() {
    try {
        bleScanner.on("BLEDeviceFind", onReceiveEvent);
        let scanFilter: ble.ScanFilter = {
            deviceId:"XX:XX:XX:XX:XX:XX",
            name:"test",
            serviceUuid:"00001888-0000-1000-8000-00805f9b34fb"
        };
        let scanOptions: ble.ScanOptions = {
            interval: 500,
            dutyMode: ble.ScanDuty.SCAN_MODE_LOW_POWER,
            matchMode: ble.MatchMode.MATCH_MODE_AGGRESSIVE,
            reportMode: ble.ScanReportMode.FENCE_SENSITIVITY_LOW
        }
        await bleScanner.startScan([scanFilter],scanOptions);
        console.info('startScan success');
    } catch (err) {
        console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    }
}
startscan();
```

## stopScan

```TypeScript
stopScan(): Promise<void>
```

Stops BLE scanning.

**Since:** 15

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { ble } from '@kit.ConnectivityKit';
let bleScanner: ble.BleScanner = ble.createBleScanner();
async function stopScan() {
    try {
        await bleScanner.stopScan();
        console.info('stopScan success');
    } catch (err) {
        console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    }
}
stopScan();
```
