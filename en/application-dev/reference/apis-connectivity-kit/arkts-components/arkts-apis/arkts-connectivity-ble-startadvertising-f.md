# startAdvertising

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## startAdvertising

```TypeScript
function startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void
```

Starts BLE advertising.

- If only [includeDeviceName](arkts-connectivity-ble-advertisedata-i.md#includedevicename) is set to true,  
the local name will be carried in the broadcast packet.  
- If only [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) is set,  
its value will be used as a custom name and carried in the broadcast packet.  
- If [includeDeviceName](arkts-connectivity-ble-advertisedata-i.md#includedevicename) is set to true and [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) is specified,  
the [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) property will take effect.  
- To set [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename),  
ensure that ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME has been added.

**Since:** 10

**Required permissions:** 
- API version 23 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME)
- API versions 10 to 22: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| setting | [AdvertiseSetting](arkts-connectivity-ble-advertisesetting-i.md) | Yes | Indicates the settings for BLE advertising. |
| advData | [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md) | Yes | Indicates the advertising data. |
| advResponse | [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md) | No | Indicates the scan response associated with the advertising data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900010 | The number of advertising resources reaches the upper limit.<br>**Applicable version:** 20 and later |
| 2900099 | Operation failed. |
| 2902054 | The length of the advertising data exceeds the upper limit.<br>**Applicable version:** 20 and later |

**Examples**

```TypeScript
let manufactureValueBuffer = new Uint8Array(4);
manufactureValueBuffer[0] = 1;
manufactureValueBuffer[1] = 2;
manufactureValueBuffer[2] = 3;
manufactureValueBuffer[3] = 4;

let serviceValueBuffer = new Uint8Array(4);
serviceValueBuffer[0] = 4;
serviceValueBuffer[1] = 6;
serviceValueBuffer[2] = 7;
serviceValueBuffer[3] = 8;
console.info('manufactureValueBuffer = '+ JSON.stringify(manufactureValueBuffer));
console.info('serviceValueBuffer = '+ JSON.stringify(serviceValueBuffer));
try {
    let setting: ble.AdvertiseSetting = {
        interval:150,
        txPower:0,
        connectable:true
    };
    let manufactureDataUnit: ble.ManufactureData = {
        manufactureId:4567,
        manufactureValue:manufactureValueBuffer.buffer
    };
    let serviceDataUnit: ble.ServiceData = {
        serviceUuid:"00001888-0000-1000-8000-00805f9b34fb",
        serviceValue:serviceValueBuffer.buffer
    };
    let advData: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // You need to apply for the ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME permission.
    };
    let advResponse: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // You need to apply for the ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME permission.
    };
    ble.startAdvertising(setting, advData ,advResponse);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```


<a id="startadvertising-1"></a>

## startAdvertising

```TypeScript
function startAdvertising(advertisingParams: AdvertisingParams, callback: AsyncCallback<number>): void
```

Starts BLE advertising. The API returns a advertising ID. The ID can be used to temporarily enable or disable this advertising using the API [enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md) or [disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md). To completely stop the advertising corresponding to the ID, invoke the API [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) with ID.

- If only [includeDeviceName](arkts-connectivity-ble-advertisedata-i.md#includedevicename) is set to true,  
the local name will be carried in the broadcast packet.  
- If only [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) is set,  
its value will be used as a custom name and carried in the broadcast packet.  
- If [includeDeviceName](arkts-connectivity-ble-advertisedata-i.md#includedevicename) is set to true and [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) is specified,  
the [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) property will take effect.  
- To set [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename),  
ensure that ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME has been added.

**Since:** 11

**Required permissions:** 
- API version 23 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME)
- API versions 11 to 22: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| advertisingParams | [AdvertisingParams](arkts-connectivity-ble-advertisingparams-i.md) | Yes | Indicates the params for BLE advertising. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | the callback of advertise ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900010 | The number of advertising resources reaches the upper limit.<br>**Applicable version:** 20 and later |
| 2900099 | Operation failed. |
| 2902054 | The length of the advertising data exceeds the upper limit.<br>**Applicable version:** 20 and later |

**Examples**

```TypeScript
let manufactureValueBuffer = new Uint8Array(4);
manufactureValueBuffer[0] = 1;
manufactureValueBuffer[1] = 2;
manufactureValueBuffer[2] = 3;
manufactureValueBuffer[3] = 4;

let serviceValueBuffer = new Uint8Array(4);
serviceValueBuffer[0] = 4;
serviceValueBuffer[1] = 6;
serviceValueBuffer[2] = 7;
serviceValueBuffer[3] = 8;
console.info('manufactureValueBuffer = '+ JSON.stringify(manufactureValueBuffer));
console.info('serviceValueBuffer = '+ JSON.stringify(serviceValueBuffer));
try {
    let setting: ble.AdvertiseSetting = {
        interval:150,
        txPower:0,
        connectable:true,
    };
    let manufactureDataUnit: ble.ManufactureData = {
        manufactureId:4567,
        manufactureValue:manufactureValueBuffer.buffer
    };
    let serviceDataUnit: ble.ServiceData = {
        serviceUuid:"00001888-0000-1000-8000-00805f9b34fb",
        serviceValue:serviceValueBuffer.buffer
    };
    let advData: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // You need to apply for the ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME permission.
    };
    let advResponse: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // You need to apply for the ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME permission.
    };
    let advertisingParams: ble.AdvertisingParams = {
        advertisingSettings: setting,
        advertisingData: advData,
        advertisingResponse: advResponse,
        duration: 0
    }
    let advHandle = 0xFF;
    ble.startAdvertising(advertisingParams, (err, outAdvHandle) => {
        if (err) {
            return;
        } else {
            advHandle = outAdvHandle;
            console.info("advHandle: " + advHandle);
        }
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```


<a id="startadvertising-2"></a>

## startAdvertising

```TypeScript
function startAdvertising(advertisingParams: AdvertisingParams): Promise<number>
```

Starts BLE advertising. The API returns a advertising ID. The ID can be used to temporarily enable or disable this advertising using the API [enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md) or [disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md). To completely stop the advertising corresponding to the ID, invoke the API [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) with ID.

- If only [includeDeviceName](arkts-connectivity-ble-advertisedata-i.md#includedevicename) is set to true,  
the local name will be carried in the broadcast packet.  
- If only [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) is set,  
its value will be used as a custom name and carried in the broadcast packet.  
- If [includeDeviceName](arkts-connectivity-ble-advertisedata-i.md#includedevicename) is set to true and [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) is specified,  
the [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename) property will take effect.  
- To set [advertiseName](arkts-connectivity-ble-advertisedata-i.md#advertisename),  
ensure that ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME has been added.

**Since:** 11

**Required permissions:** 
- API version 23 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME)
- API versions 11 to 22: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| advertisingParams | [AdvertisingParams](arkts-connectivity-ble-advertisingparams-i.md) | Yes | Indicates the param for BLE advertising. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Returns the promise object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900010 | The number of advertising resources reaches the upper limit.<br>**Applicable version:** 20 and later |
| 2900099 | Operation failed. |
| 2902054 | The length of the advertising data exceeds the upper limit.<br>**Applicable version:** 20 and later |

**Examples**

```TypeScript
let manufactureValueBuffer = new Uint8Array(4);
manufactureValueBuffer[0] = 1;
manufactureValueBuffer[1] = 2;
manufactureValueBuffer[2] = 3;
manufactureValueBuffer[3] = 4;

let serviceValueBuffer = new Uint8Array(4);
serviceValueBuffer[0] = 4;
serviceValueBuffer[1] = 6;
serviceValueBuffer[2] = 7;
serviceValueBuffer[3] = 8;
console.info('manufactureValueBuffer = '+ JSON.stringify(manufactureValueBuffer));
console.info('serviceValueBuffer = '+ JSON.stringify(serviceValueBuffer));
try {
    let setting: ble.AdvertiseSetting = {
        interval:150,
        txPower:0,
        connectable:true
    };
    let manufactureDataUnit: ble.ManufactureData = {
        manufactureId:4567,
        manufactureValue:manufactureValueBuffer.buffer
    };
    let serviceDataUnit: ble.ServiceData = {
        serviceUuid:"00001888-0000-1000-8000-00805f9b34fb",
        serviceValue:serviceValueBuffer.buffer
    };
    let advData: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // You need to apply for the ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME permission.
    };
    let advResponse: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // You need to apply for the ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME permission.
    };
    let advertisingParams: ble.AdvertisingParams = {
        advertisingSettings: setting,
        advertisingData: advData,
        advertisingResponse: advResponse,
        duration: 0
    }
    let advHandle = 0xFF;
    ble.startAdvertising(advertisingParams)
        .then(outAdvHandle => {
            advHandle = outAdvHandle;
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
