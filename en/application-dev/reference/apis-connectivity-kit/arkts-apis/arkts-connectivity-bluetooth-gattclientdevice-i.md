# GattClientDevice

Manages GATT client. Before calling an Gatt client method, you must use [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) to create an GattClientDevice instance.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GattClientDevice](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## close

```TypeScript
close(): boolean
```

Disables a BLE peripheral device.

This method unregisters the device and clears the registered callbacks and handles.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [close](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#close)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the the device is disabled; returns `false` otherwise. |

**Examples**

```TypeScript
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let ret : boolean = device.close();
```

## connect

```TypeScript
connect(): boolean
```

Connects to a BLE peripheral device.

The 'BLEConnectionStateChange' event is subscribed to return the connection state.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [connect](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#connect)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the connection process starts; returns `false` otherwise. |

**Examples**

```TypeScript
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let ret : boolean = device.connect();
```

## disconnect

```TypeScript
disconnect(): boolean
```

Disconnects from or stops an ongoing connection to a BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [disconnect](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#disconnect)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the disconnection process starts; returns `false` otherwise. |

**Examples**

```TypeScript
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let ret : boolean = device.disconnect();
```

## getDeviceName

```TypeScript
getDeviceName(callback: AsyncCallback<string>): void
```

Obtains the name of BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getDeviceName](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#getdevicename)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to obtain the device name. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
// callback
let gattClient : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice("XX:XX:XX:XX:XX:XX");
let deviceName : void = gattClient.getDeviceName((err : BusinessError, data : string)=> {
    console.info('device name err ' + JSON.stringify(err));
    console.info('device name' + JSON.stringify(data));
})
```

```TypeScript
// promise
let gattClient : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice("XX:XX:XX:XX:XX:XX");
gattClient.getDeviceName().then((data) => {
    console.info('device name' + JSON.stringify(data));
})
```

## getDeviceName

```TypeScript
getDeviceName(): Promise<string>
```

Obtains the name of BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getDeviceName](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#getdevicename)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns a string representation of the name if obtained; returns `null` if the name fails to be obtained or the name does not exist. |

**Examples**

See [getDeviceName](#getdevicename)

## getRssiValue

```TypeScript
getRssiValue(callback: AsyncCallback<number>): void
```

Get the RSSI value of this BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getRssiValue](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#getrssivalue)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback invoked to return the RSSI, in dBm. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
// callback
let gattClient : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice("XX:XX:XX:XX:XX:XX");
let ret : boolean = gattClient.connect();
gattClient.getRssiValue((err : BusinessError, data : number)=> {
    console.info('rssi err ' + JSON.stringify(err));
    console.info('rssi value' + JSON.stringify(data));
})
```

```TypeScript
// promise
let gattClient : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice("XX:XX:XX:XX:XX:XX");
gattClient.getRssiValue().then((data : number) => {
    console.info('rssi' + JSON.stringify(data));
})
```

## getRssiValue

```TypeScript
getRssiValue(): Promise<number>
```

Get the RSSI value of this BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getRssiValue](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#getrssivalue)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Returns the RSSI value. |

**Examples**

See [getRssiValue](#getrssivalue)

## getServices

```TypeScript
getServices(callback: AsyncCallback<Array<GattService>>): void
```

Starts discovering services.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getServices](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#getservices)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[GattService](arkts-connectivity-bluetooth-gattservice-i.md)&gt;&gt; | Yes | Callback used to catch the services. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Callback mode.
function getServices(code : BusinessError, gattServices : Array<bluetooth.GattService>) {
  if (code.code == 0) {
      console.info(`bluetooth code is ${code.code}`);
      console.info(`bluetooth services size is ${gattServices.length}`);

      for (let i = 0; i < gattServices.length; i++) {
        console.info(`bluetooth serviceUuid is ${gattServices[i].serviceUuid}`);
      }
  }
}

let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
device.connect();
device.getServices(getServices);
```

```TypeScript
// Promise
let device : bluetooth.GattClientDevice= bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
device.connect();
device.getServices().then((result : Array<bluetooth.GattService>) => {
    console.info("getServices successfully:" + JSON.stringify(result));
});
```

## getServices

```TypeScript
getServices(): Promise<Array<GattService>>
```

Starts discovering services.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getServices](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#getservices)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[GattService](arkts-connectivity-bluetooth-gattservice-i.md)&gt;&gt; | Returns the list of services [GattService](arkts-connectivity-bluetooth-gattservice-i.md) of the BLE peripheral device. |

**Examples**

See [getServices](#getservices)

## off('BLECharacteristicChange')

```TypeScript
off(type: 'BLECharacteristicChange', callback?: Callback<BLECharacteristic>): void
```

Unsubscribe characteristic value changed event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** BLECharacteristicChange

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLECharacteristicChange' | Yes | Type of the characteristic value changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md)&gt; | No | Callback used to listen for the characteristic value changed event. |

## off('BLEConnectionStateChange')

```TypeScript
off(type: 'BLEConnectionStateChange', callback?: Callback<BLEConnectChangedState>): void
```

Unsubscribe client connection state changed event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** BLEConnectionStateChange

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLEConnectionStateChange' | Yes | Type of the connection state changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLEConnectChangedState](arkts-connectivity-bluetooth-bleconnectchangedstate-i.md)&gt; | No | Callback used to listen for the connection state changed event. |

## on('BLECharacteristicChange')

```TypeScript
on(type: 'BLECharacteristicChange', callback: Callback<BLECharacteristic>): void
```

Subscribe characteristic value changed event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** BLECharacteristicChange

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLECharacteristicChange' | Yes | Type of the characteristic value changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md)&gt; | Yes | Callback used to listen for the characteristic value changed event. |

## on('BLEConnectionStateChange')

```TypeScript
on(type: 'BLEConnectionStateChange', callback: Callback<BLEConnectChangedState>): void
```

Subscribe client connection state changed event.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** BLEConnectionStateChange

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLEConnectionStateChange' | Yes | Type of the connection state changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLEConnectChangedState](arkts-connectivity-bluetooth-bleconnectchangedstate-i.md)&gt; | Yes | Callback used to listen for the connection state changed event. |

## readCharacteristicValue

```TypeScript
readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback<BLECharacteristic>): void
```

Reads the characteristic of a BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [readCharacteristicValue](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#readcharacteristicvalue)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) | Yes | Indicates the characteristic to read. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md)&gt; | Yes | Callback invoked to return the characteristic value read. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
function readCcc(code : BusinessError, BLECharacteristic : bluetooth.BLECharacteristic) {
  if (code.code != 0) {
      return;
  }
  console.info(`bluetooth characteristic uuid: ${BLECharacteristic.characteristicUuid}`);
  let value = new Uint8Array(BLECharacteristic.characteristicValue);
}

let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let descriptors : Array<bluetooth.BLEDescriptor> = [];
let bufferDesc : ArrayBuffer = new ArrayBuffer(8);
let descV : Uint8Array = new Uint8Array(bufferDesc);
descV[0] = 11;
let descriptor : bluetooth.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
descriptorUuid: '00002903-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic : bluetooth.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
characteristicValue: bufferCCC, descriptors:descriptors};

device.readCharacteristicValue(characteristic, readCcc);
```

```TypeScript
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let descriptors : Array<bluetooth.BLEDescriptor> = [];
let bufferDesc = new ArrayBuffer(8);
let descV = new Uint8Array(bufferDesc);
descV[0] = 11;
let descriptor : bluetooth.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
descriptorUuid: '00002903-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic : bluetooth.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
characteristicValue: bufferCCC, descriptors:descriptors};

device.readCharacteristicValue(characteristic);
```

## readCharacteristicValue

```TypeScript
readCharacteristicValue(characteristic: BLECharacteristic): Promise<BLECharacteristic>
```

Reads the characteristic of a BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [readCharacteristicValue](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#readcharacteristicvalue)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) | Yes | Indicates the characteristic to read. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md)&gt; | Promise used to return the characteristic value read. |

**Examples**

See [readCharacteristicValue](#readcharacteristicvalue)

## readDescriptorValue

```TypeScript
readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback<BLEDescriptor>): void
```

Reads the descriptor of a BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [readDescriptorValue](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#readdescriptorvalue)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [BLEDescriptor](arkts-connectivity-bluetooth-bledescriptor-i.md) | Yes | Indicates the descriptor to read. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BLEDescriptor](arkts-connectivity-bluetooth-bledescriptor-i.md)&gt; | Yes | Callback invoked to return the descriptor read. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
function readDesc(code : BusinessError, BLEDescriptor : bluetooth.BLEDescriptor) {
  if (code.code != 0) {
      return;
  }
  console.info(`bluetooth descriptor uuid: ${BLEDescriptor.descriptorUuid}`);
  let value = new Uint8Array(BLEDescriptor.descriptorValue);
}

let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let bufferDesc = new ArrayBuffer(8);
let descV = new Uint8Array(bufferDesc);
descV[0] = 11;
let descriptor : bluetooth.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002903-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
device.readDescriptorValue(descriptor, readDesc);
```

```TypeScript
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let bufferDesc = new ArrayBuffer(8);
let descV = new Uint8Array(bufferDesc);
descV[0] = 11;
let descriptor : bluetooth.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002903-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
device.readDescriptorValue(descriptor);
```

## readDescriptorValue

```TypeScript
readDescriptorValue(descriptor: BLEDescriptor): Promise<BLEDescriptor>
```

Reads the descriptor of a BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [readDescriptorValue](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#readdescriptorvalue)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [BLEDescriptor](arkts-connectivity-bluetooth-bledescriptor-i.md) | Yes | Indicates the descriptor to read. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BLEDescriptor](arkts-connectivity-bluetooth-bledescriptor-i.md)&gt; | Promise used to return the descriptor read. |

**Examples**

See [readDescriptorValue](#readdescriptorvalue)

## setBLEMtuSize

```TypeScript
setBLEMtuSize(mtu: number): boolean
```

Set the mtu size of a BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setBLEMtuSize](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#setblemtusize)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mtu | number | Yes | The maximum transmission unit. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the set mtu is successfully; returns `false` otherwise. |

**Examples**

```TypeScript
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
device.setBLEMtuSize(128);
```

## setNotifyCharacteristicChanged

```TypeScript
setNotifyCharacteristicChanged(characteristic: BLECharacteristic, enable: boolean): boolean
```

Enables or disables notification of a characteristic when value changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setNotifyCharacteristicChanged](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#setnotifycharacteristicchanged)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) | Yes | BLE characteristic to listen for. |
| enable | boolean | Yes | Specifies whether to enable notification of the characteristic. The value `true` indicates that notification is enabled, and the value `false` indicates that notification is disabled. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if notification of the characteristic is enabled or disabled; returns `false` otherwise. |

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
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
device.setNotifyCharacteristicChanged(characteristic, false);
```

## writeCharacteristicValue

```TypeScript
writeCharacteristicValue(characteristic: BLECharacteristic): boolean
```

Writes the characteristic of a BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [writeCharacteristicValue](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#writecharacteristicvalue)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) | Yes | Indicates the characteristic to write. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the characteristic is written successfully; returns `false` otherwise. |

**Examples**

```TypeScript
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let descriptors : Array<bluetooth.BLEDescriptor> = [];
let bufferDesc = new ArrayBuffer(8);
let descV = new Uint8Array(bufferDesc);
descV[0] = 11;
let descriptor : bluetooth.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002903-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic : bluetooth.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  characteristicValue: bufferCCC, descriptors:descriptors};
let retWriteCcc : boolean = device.writeCharacteristicValue(characteristic);
if (retWriteCcc) {
  console.info('write characteristic successfully');
} else {
  console.error('write characteristic failed');
}
```

## writeDescriptorValue

```TypeScript
writeDescriptorValue(descriptor: BLEDescriptor): boolean
```

Writes the descriptor of a BLE peripheral device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [writeDescriptorValue](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md#writedescriptorvalue)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [BLEDescriptor](arkts-connectivity-bluetooth-bledescriptor-i.md) | Yes | Indicates the descriptor to write. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the descriptor is written successfully; returns `false` otherwise. |

**Examples**

```TypeScript
let device : bluetooth.GattClientDevice = bluetooth.BLE.createGattClientDevice('XX:XX:XX:XX:XX:XX');
let bufferDesc = new ArrayBuffer(8);
let descV = new Uint8Array(bufferDesc);
descV[0] = 22;
let descriptor : bluetooth.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002903-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
let retWriteDesc : boolean = device.writeDescriptorValue(descriptor);
if (retWriteDesc) {
  console.info('bluetooth write descriptor successfully');
} else {
  console.error('bluetooth write descriptor failed');
}
```
