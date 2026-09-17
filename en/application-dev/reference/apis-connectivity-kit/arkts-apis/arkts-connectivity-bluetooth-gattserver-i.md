# GattServer

Manages GATT server. Before calling an Gatt server method, you must use [createGattServer](arkts-connectivity-ble-creategattserver-f.md) to create an GattServer instance.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GattServer](arkts-connectivity-bluetoothmanager-gattserver-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## addService

```TypeScript
addService(service: GattService): boolean
```

Adds a specified service to be hosted. The added service and its characteristics are provided by the local device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addService](arkts-connectivity-bluetoothmanager-gattserver-i.md#addservice)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| service | [GattService](arkts-connectivity-bluetooth-gattservice-i.md) | Yes | Indicates the service to add. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the service is added; returns `false` otherwise. |

**Examples**

```TypeScript
// Create descriptors.
let descriptors : Array<bluetooth.BLEDescriptor> = [];
let arrayBuffer = new ArrayBuffer(8);
let descV = new Uint8Array(arrayBuffer);
descV[0] = 11;
let descriptor : bluetooth.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: arrayBuffer};
descriptors[0] = descriptor;

// Create characteristics.
let characteristics : Array<bluetooth.BLECharacteristic> = [];
let arrayBufferC = new ArrayBuffer(8);
let cccV = new Uint8Array(arrayBufferC);
cccV[0] = 1;
let characteristic : bluetooth.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB', characteristicValue: arrayBufferC, descriptors:descriptors};
let characteristicN : bluetooth.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001821-0000-1000-8000-00805F9B34FB', characteristicValue: arrayBufferC, descriptors:descriptors};
characteristics[0] = characteristic;

// Create a gattService instance.
let gattService : bluetooth.GattService = {serviceUuid:'00001810-0000-1000-8000-00805F9B34FB', isPrimary: true, characteristics:characteristics, includeServices:[]};

let gattServer : bluetooth.GattServer = bluetooth.BLE.createGattServer();
let ret : boolean = gattServer.addService(gattService);
if (ret) {
   console.info("add service successfully");
} else {
   console.error("add service failed");
}
```

## close

```TypeScript
close(): void
```

Closes this `GattServer` object and unregisters its callbacks.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [close](arkts-connectivity-bluetoothmanager-gattserver-i.md#close)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Examples**

```TypeScript
let server : bluetooth.GattServer = bluetooth.BLE.createGattServer();
server.close();
```

## notifyCharacteristicChanged

```TypeScript
notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic): boolean
```

Sends a notification of a change in a specified local characteristic.

This method should be called for every BLE peripheral device that has requested notifications.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [notifyCharacteristicChanged](arkts-connectivity-bluetoothmanager-gattserver-i.md#notifycharacteristicchanged)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates the address of the BLE peripheral device to receive the notification. |
| notifyCharacteristic | [NotifyCharacteristic](arkts-connectivity-bluetooth-notifycharacteristic-i.md) | Yes | Indicates the local characteristic that has changed. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the notification is sent successfully; returns `false` otherwise. |

**Examples**

```TypeScript
// Create descriptors.
let descriptors : Array<bluetooth.BLEDescriptor> = [];
let arrayBuffer = new ArrayBuffer(8);
let descV = new Uint8Array(arrayBuffer);
descV[0] = 11;
let descriptor : bluetooth.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: arrayBuffer};
descriptors[0] = descriptor;
let arrayBufferC = new ArrayBuffer(8);
let characteristic : bluetooth.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB', characteristicValue: arrayBufferC, descriptors:descriptors};
let notifyCharacteristic : bluetooth.NotifyCharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001821-0000-1000-8000-00805F9B34FB', characteristicValue: characteristic.characteristicValue, confirm: false};
let server : bluetooth.GattServer = bluetooth.BLE.createGattServer();
server.notifyCharacteristicChanged('XX:XX:XX:XX:XX:XX', notifyCharacteristic);
```

## off('characteristicRead')

```TypeScript
off(type: 'characteristicRead', callback?: Callback<CharacteristicReadReq>): void
```

Unsubscribe characteristic read event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** characteristicRead

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'characteristicRead' | Yes | Type of the characteristic read event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CharacteristicReadReq](arkts-connectivity-bluetooth-characteristicreadreq-i.md)&gt; | No | Callback used to listen for the characteristic read event. |

## off('characteristicWrite')

```TypeScript
off(type: 'characteristicWrite', callback?: Callback<CharacteristicWriteReq>): void
```

Unsubscribe characteristic write event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** characteristicWrite

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'characteristicWrite' | Yes | Type of the characteristic write event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CharacteristicWriteReq](arkts-connectivity-bluetooth-characteristicwritereq-i.md)&gt; | No | Callback used to listen for the characteristic write event. |

## off('descriptorRead')

```TypeScript
off(type: 'descriptorRead', callback?: Callback<DescriptorReadReq>): void
```

Unsubscribe descriptor read event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** descriptorRead

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'descriptorRead' | Yes | Type of the descriptor read event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DescriptorReadReq](arkts-connectivity-bluetooth-descriptorreadreq-i.md)&gt; | No | Callback used to listen for the descriptor read event. |

## off('descriptorWrite')

```TypeScript
off(type: 'descriptorWrite', callback?: Callback<DescriptorWriteReq>): void
```

Unsubscribe descriptor write event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** descriptorWrite

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'descriptorWrite' | Yes | Type of the descriptor write event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DescriptorWriteReq](arkts-connectivity-bluetooth-descriptorwritereq-i.md)&gt; | No | Callback used to listen for the descriptor write event. |

## off('connectStateChange')

```TypeScript
off(type: 'connectStateChange', callback?: Callback<BLEConnectChangedState>): void
```

Unsubscribe server connection state changed event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** connectStateChange

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connectStateChange' | Yes | Type of the connection state changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLEConnectChangedState](arkts-connectivity-bluetooth-bleconnectchangedstate-i.md)&gt; | No | Callback used to listen for the connection state changed event. |

## on('characteristicRead')

```TypeScript
on(type: 'characteristicRead', callback: Callback<CharacteristicReadReq>): void
```

Subscribe characteristic read event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** characteristicRead

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'characteristicRead' | Yes | Type of the characteristic read event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CharacteristicReadReq](arkts-connectivity-bluetooth-characteristicreadreq-i.md)&gt; | Yes | Callback used to listen for the characteristic read event. |

## on('characteristicWrite')

```TypeScript
on(type: 'characteristicWrite', callback: Callback<CharacteristicWriteReq>): void
```

Subscribe characteristic write event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** characteristicWrite

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'characteristicWrite' | Yes | Type of the characteristic write event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CharacteristicWriteReq](arkts-connectivity-bluetooth-characteristicwritereq-i.md)&gt; | Yes | Callback used to listen for the characteristic write event. |

## on('descriptorRead')

```TypeScript
on(type: 'descriptorRead', callback: Callback<DescriptorReadReq>): void
```

Subscribe descriptor read event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** descriptorRead

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'descriptorRead' | Yes | Type of the descriptor read event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DescriptorReadReq](arkts-connectivity-bluetooth-descriptorreadreq-i.md)&gt; | Yes | Callback used to listen for the descriptor read event. |

## on('descriptorWrite')

```TypeScript
on(type: 'descriptorWrite', callback: Callback<DescriptorWriteReq>): void
```

Subscribe descriptor write event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** descriptorWrite

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'descriptorWrite' | Yes | Type of the descriptor write event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DescriptorWriteReq](arkts-connectivity-bluetooth-descriptorwritereq-i.md)&gt; | Yes | Callback used to listen for the descriptor write event. |

## on('connectStateChange')

```TypeScript
on(type: 'connectStateChange', callback: Callback<BLEConnectChangedState>): void
```

Subscribe server connection state changed event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** connectStateChange

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connectStateChange' | Yes | Type of the connection state changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLEConnectChangedState](arkts-connectivity-bluetooth-bleconnectchangedstate-i.md)&gt; | Yes | Callback used to listen for the connection state changed event. |

## removeService

```TypeScript
removeService(serviceUuid: string): boolean
```

Removes a specified service from the list of GATT services provided by this device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [removeService](arkts-connectivity-bluetoothmanager-gattserver-i.md#removeservice)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceUuid | string | Yes | Indicates the UUID of the service to remove. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the service is removed; returns `false` otherwise. |

**Examples**

```TypeScript
let server : bluetooth.GattServer = bluetooth.BLE.createGattServer();
server.removeService('00001810-0000-1000-8000-00805F9B34FB');
```

## sendResponse

```TypeScript
sendResponse(serverResponse: ServerResponse): boolean
```

Sends a response to a specified read or write request to a given BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [sendResponse](arkts-connectivity-bluetoothmanager-gattserver-i.md#sendresponse)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serverResponse | [ServerResponse](arkts-connectivity-bluetooth-serverresponse-i.md) | Yes | Indicates the response parameters [ServerResponse](arkts-connectivity-bluetooth-serverresponse-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the response is sent successfully; returns `false` otherwise. |

**Examples**

```TypeScript
/* send response */
let arrayBufferCCC = new ArrayBuffer(8);
let cccValue = new Uint8Array(arrayBufferCCC);
cccValue[0] = 1;
let serverResponse : bluetooth.ServerResponse = {
    "deviceId": "XX:XX:XX:XX:XX:XX",
    "transId": 0,
    "status": 0,
    "offset": 0,
    "value": arrayBufferCCC,
};

let gattServer : bluetooth.GattServer = bluetooth.BLE.createGattServer();
let ret : boolean = gattServer.sendResponse(serverResponse);
if (ret) {
  console.info('bluetooth sendResponse successfully');
} else {
  console.error('bluetooth sendResponse failed');
}
```

## startAdvertising

```TypeScript
startAdvertising(setting: AdvertiseSetting, advData: AdvertiseData, advResponse?: AdvertiseData): void
```

Starts BLE advertising.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [startAdvertising](arkts-connectivity-bluetoothmanager-gattserver-i.md#startadvertising)

**Required permissions:** ohos.permission.DISCOVER_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| setting | [AdvertiseSetting](arkts-connectivity-bluetooth-advertisesetting-i.md) | Yes | Indicates the settings for BLE advertising. If you need to use the default value, set this parameter to `null`. |
| advData | [AdvertiseData](arkts-connectivity-bluetooth-advertisedata-i.md) | Yes | Indicates the advertising data. |
| advResponse | [AdvertiseData](arkts-connectivity-bluetooth-advertisedata-i.md) | No | Indicates the scan response associated with the advertising data. |

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
let gattServer : bluetooth.GattServer = bluetooth.BLE.createGattServer();
let setting : bluetooth.AdvertiseSetting = {
    interval:150,
    txPower:60,
    connectable:true,
}

let manufactureData : bluetooth.ManufactureData = {
    manufactureId:4567,
    manufactureValue:manufactureValueBuffer.buffer
}

let serviceData : bluetooth.ServiceData = {
    serviceUuid:"00001888-0000-1000-8000-00805f9b34fb",
    serviceValue:serviceValueBuffer.buffer
}

let advData : bluetooth.AdvertiseData = {
    serviceUuids:["00001889-0000-1000-8000-00805f9b34fb"],
    manufactureData:[manufactureData],
    serviceData:[serviceData],
}

let advResponse : bluetooth.AdvertiseData = {
    serviceUuids:["00001889-0000-1000-8000-00805f9b34fb"],
    manufactureData:[manufactureData],
    serviceData:[serviceData],
}
gattServer.startAdvertising(setting, advData, advResponse);
```

## stopAdvertising

```TypeScript
stopAdvertising(): void
```

Stops BLE advertising.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [stopAdvertising](arkts-connectivity-bluetoothmanager-gattserver-i.md#stopadvertising)

**Required permissions:** ohos.permission.DISCOVER_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Examples**

```TypeScript
let server : bluetooth.GattServer = bluetooth.BLE.createGattServer();
server.stopAdvertising();
```
