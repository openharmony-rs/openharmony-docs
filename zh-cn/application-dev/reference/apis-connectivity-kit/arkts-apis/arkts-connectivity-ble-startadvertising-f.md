# startAdvertising

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## startAdvertising

```TypeScript
function startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void
```

开始发送BLE广播报文。

当应用不再需要发送BLE广播报文时，需主动调用[ble.stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md)停止发送。同步接口，不要和API version 11的[ble.stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md)搭配使用。

**起始版本：** 10

**需要权限：** 
- API版本23+：ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME)
- API版本10-22：ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| setting | [AdvertiseSetting](arkts-connectivity-ble-advertisesetting-i.md) | 是 | BLE广播的相关参数。 |
| advData | [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md) | 是 | BLE广播报文内容。 |
| advResponse | [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md) | 否 | BLE扫描回复广播报文。若不填写，则不携带扫描回复广播报文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900010](../errorcode-bluetoothManager.md#2900010-资源达到上限) | The number of advertising resources reaches the upper limit.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2902054](../errorcode-bluetoothManager.md#2902054-广播报文超限) | The length of the advertising data exceeds the upper limit.<br>**适用版本：** 20+ |

**示例**

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
        isExtended:false
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
        advertiseName:"testName" // 需申请ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME权限
    };
    let advResponse: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // 需申请ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME权限
    };
    ble.startAdvertising(setting, advData ,advResponse);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

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
        isExtended:false
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
        advertiseName:"testName" // 需申请ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME权限
    };
    let advResponse: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // 需申请ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME权限
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
        isExtended:false
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
        advertiseName:"testName" // 需申请ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME权限
    };
    let advResponse: ble.AdvertiseData = {
        serviceUuids:["00001888-0000-1000-8000-00805f9b34fb"],
        manufactureData:[manufactureDataUnit],
        serviceData:[serviceDataUnit],
        advertiseName:"testName" // 需申请ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME权限
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


## startAdvertising

```TypeScript
function startAdvertising(advertisingParams: AdvertisingParams, callback: AsyncCallback<number>): void
```

首次启动发送BLE广播报文。使用Callback异步回调。

启动成功后，蓝牙子系统会分配相关资源，并使用Callback异步返回该广播的标识。若携带了发送广播持续时间，则达到该持续时间后，广播会停止发送，但分配的广播资源还存在，可以通过[ble.enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md)重新启动发送该广播。从API version 15开始，应用可多次调用，支持发起多路广播，每一路广播通过不同的ID标识管理。当应用不再需要该广播时，需调用API version 11开始支持的[ble.stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md)完全停止该广播，不要与API version 10开始支持的[ble.stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md)混用。

**起始版本：** 11

**需要权限：** 
- API版本23+：ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME)
- API版本11-22：ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| advertisingParams | [AdvertisingParams](arkts-connectivity-ble-advertisingparams-i.md) | 是 | 启动BLE广播的相关参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当广播启动成功，err为undefined，data为分配的广播ID标识；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900010](../errorcode-bluetoothManager.md#2900010-资源达到上限) | The number of advertising resources reaches the upper limit.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2902054](../errorcode-bluetoothManager.md#2902054-广播报文超限) | The length of the advertising data exceeds the upper limit.<br>**适用版本：** 20+ |

**示例**

参见 [startAdvertising](#startadvertising)


## startAdvertising

```TypeScript
function startAdvertising(advertisingParams: AdvertisingParams): Promise<number>
```

首次启动发送BLE广播报文。使用Promise异步回调。

启动成功后，蓝牙子系统会分配相关资源，并使用Promise异步返回该广播的标识。若携带了发送广播持续时间，则达到该持续时间后，广播会停止发送，但分配的广播资源还存在，可以通过[ble.enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md)重新启动发送该广播。从API version 15开始，应用可多次调用，支持发起多路广播，每一路广播通过不同的ID标识管理。当应用不再需要该广播时，需调用API version 11开始支持的[ble.stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md)完全停止该广播，不要与API version 10开始支持的[ble.stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md)混用。

**起始版本：** 11

**需要权限：** 
- API版本23+：ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME)
- API版本11-22：ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| advertisingParams | [AdvertisingParams](arkts-connectivity-ble-advertisingparams-i.md) | 是 | 启动BLE广播的相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 广播ID标识，通过promise形式获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900010](../errorcode-bluetoothManager.md#2900010-资源达到上限) | The number of advertising resources reaches the upper limit.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2902054](../errorcode-bluetoothManager.md#2902054-广播报文超限) | The length of the advertising data exceeds the upper limit.<br>**适用版本：** 20+ |

**示例**

参见 [startAdvertising](#startadvertising)
