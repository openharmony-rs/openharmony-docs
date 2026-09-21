# GattServer

```TypeScript
interface GattServer
```

Manages GATT server. Before calling an Gatt server method, you must use [createGattServer](arkts-connectivity-ble-creategattserver-f.md) to create an GattServer instance.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## addService

```TypeScript
addService(service: GattService): void
```

Adds a specified service to be hosted.

The added service and its characteristics are provided by the local device.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| service | [GattService](arkts-connectivity-ble-gattservice-i.md) | Yes | Indicates the service to add. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// Create descriptors.
let descriptors: Array<ble.BLEDescriptor> = [];
let arrayBuffer = new ArrayBuffer(2);
let descV = new Uint8Array(arrayBuffer);
descV[0] = 0; // Use the Client Characteristic Configuration descriptor as an example. When bit 0 and bit 1 are both set to 0, the notification and indication functions are disabled.
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: arrayBuffer};
descriptors[0] = descriptor;

// Create characteristics.
let characteristics: Array<ble.BLECharacteristic> = [];
let arrayBufferC = new ArrayBuffer(8);
let cccV = new Uint8Array(arrayBufferC);
cccV[0] = 1;
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB', characteristicValue: arrayBufferC, descriptors:descriptors};
characteristics[0] = characteristic;

// Create a gattService instance.
let gattService: ble.GattService = {serviceUuid:'00001810-0000-1000-8000-00805F9B34FB', isPrimary: true, characteristics:characteristics, includeServices:[]};

try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.addService(gattService);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## close

```TypeScript
close(): void
```

Closes this `GattServer` object and unregisters its callbacks.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

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
let server: ble.GattServer = ble.createGattServer();
try {
    server.close();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## connect

```TypeScript
connect(deviceId: string, autoConnect?: boolean): void
```

Connects to a BLE central device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |
| autoConnect | boolean | No | Indicates whether to automatically connect to the remote device. If `true`, it will automatically connect when the remote device is available, default is `false`. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API because the short-range chip is not inserted on the 2in1 device. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

## disconnect

```TypeScript
disconnect(deviceId: string): void
```

Disconnects from or stops an ongoing connection to a BLE central device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API because the short-range chip is not inserted on the 2in1 device. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

## getConnectedState

```TypeScript
getConnectedState(deviceId: string): ProfileConnectionState
```

Get the connection state of a specific device.

**Since:** 22

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |

**Return value:**

| Type | Description |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-ble-profileconnectionstate-t.md) | Connection state. |

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
import { BusinessError } from '@kit.BasicServicesKit';
let gattServer: ble.GattServer = ble.createGattServer();
let deviceId: string = 'XX:XX:XX:XX:XX:XX';
try {
    let result: ble.ProfileConnectionState = gattServer.getConnectedState(deviceId);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## getService

```TypeScript
getService(serviceUuid: string): GattService
```

Obtain a specific GATT service by using a UUID.

**Since:** 22

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceUuid | string | Yes | Indicates the UUID of the service. |

**Return value:**

| Type | Description |
| --- | --- |
| [GattService](arkts-connectivity-ble-gattservice-i.md) | The GATT service has been obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |
| 2901008 | Gatt service is not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let server: ble.GattServer = ble.createGattServer();
try {
    // Before calling the getService API, you need to use the addService API to add the service.
    let service: ble.GattService = server.getService('00001810-0000-1000-8000-00805F9B34FB');
    console.info('characteristics size is: ' + service.characteristics.length);
    for (let i = 0; i < service.characteristics.length; i++) {
        console.info('characterUuid is: ' + service.characteristics[i].characteristicUuid);
    }
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## getServices

```TypeScript
getServices(): GattService[]
```

Obtain the list of GATT services registered by the application.

**Since:** 22

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [GattService](arkts-connectivity-ble-gattservice-i.md)[] | The list of GATT service has been obtained. |

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
import { BusinessError } from '@kit.BasicServicesKit';
let server: ble.GattServer = ble.createGattServer();
try {
    let services: ble.GattService[] = server.getServices();
    console.info('services size is: ' + services.length);
    for (let i = 0; i < services.length; i++) {
        console.info('serviceUuid is: ' + services[i].serviceUuid);
    }
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## notifyCharacteristicChanged

```TypeScript
notifyCharacteristicChanged(
      deviceId: string,
      notifyCharacteristic: NotifyCharacteristic,
      callback: AsyncCallback<void>
    ): void
```

Sends a notification of a change in a specified local characteristic with a asynchronous callback.

This method should be called for every BLE peripheral device that has requested notifications.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |
| notifyCharacteristic | [NotifyCharacteristic](arkts-connectivity-ble-notifycharacteristic-i.md) | Yes | Indicates the local characteristic that has changed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let arrayBufferC = new ArrayBuffer(8);
let notifyCharacter: ble.NotifyCharacteristic = {
    serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
    characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
    characteristicValue: arrayBufferC,
    confirm: true
};
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.notifyCharacteristicChanged('XX:XX:XX:XX:XX:XX', notifyCharacter, (err: BusinessError) => {
        if (err) {
            console.error('notifyCharacteristicChanged callback failed');
        } else {
            console.info('notifyCharacteristicChanged callback successful');
        }
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="notifycharacteristicchanged-1"></a>

## notifyCharacteristicChanged

```TypeScript
notifyCharacteristicChanged(deviceId: string, notifyCharacteristic: NotifyCharacteristic): Promise<void>
```

Sends a notification of a change in a specified local characteristic with a asynchronous callback.

This method should be called for every BLE peripheral device that has requested notifications.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |
| notifyCharacteristic | [NotifyCharacteristic](arkts-connectivity-ble-notifycharacteristic-i.md) | Yes | Indicates the local characteristic that has changed. |

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
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let arrayBufferC = new ArrayBuffer(8);
let notifyCharacter: ble.NotifyCharacteristic = {
    serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
    characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
    characteristicValue: arrayBufferC,
    confirm: true
};
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.notifyCharacteristicChanged('XX:XX:XX:XX:XX:XX', notifyCharacter).then(() => {
        console.info('notifyCharacteristicChanged promise successful');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## off('characteristicRead')

```TypeScript
off(type: 'characteristicRead', callback?: Callback<CharacteristicReadRequest>): void
```

Unsubscribe characteristic read event.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'characteristicRead' | Yes | Type of the characteristic read event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CharacteristicReadRequest](arkts-connectivity-ble-characteristicreadrequest-i.md)&gt; | No | Callback used to listen for the characteristic read event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.off('characteristicRead');
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```

## off('characteristicWrite')

```TypeScript
off(type: 'characteristicWrite', callback?: Callback<CharacteristicWriteRequest>): void
```

Unsubscribe characteristic write event.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'characteristicWrite' | Yes | Type of the characteristic write event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CharacteristicWriteRequest](arkts-connectivity-ble-characteristicwriterequest-i.md)&gt; | No | Callback used to listen for the characteristic write event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.off('characteristicWrite');
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```

## off('descriptorRead')

```TypeScript
off(type: 'descriptorRead', callback?: Callback<DescriptorReadRequest>): void
```

Unsubscribe descriptor read event.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'descriptorRead' | Yes | Type of the descriptor read event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DescriptorReadRequest](arkts-connectivity-ble-descriptorreadrequest-i.md)&gt; | No | Callback used to listen for the descriptor read event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.off('descriptorRead');
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```

## off('descriptorWrite')

```TypeScript
off(type: 'descriptorWrite', callback?: Callback<DescriptorWriteRequest>): void
```

Unsubscribe descriptor write event.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'descriptorWrite' | Yes | Type of the descriptor write event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DescriptorWriteRequest](arkts-connectivity-ble-descriptorwriterequest-i.md)&gt; | No | Callback used to listen for the descriptor write event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
let gattServer: ble.GattServer = ble.createGattServer();
gattServer.off('descriptorWrite');
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```

## off('connectionStateChange')

```TypeScript
off(type: 'connectionStateChange', callback?: Callback<BLEConnectionChangeState>): void
```

Unsubscribe server connection state changed event.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connectionStateChange' | Yes | Type of the connection state changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLEConnectionChangeState](arkts-connectivity-ble-bleconnectionchangestate-i.md)&gt; | No | Callback used to listen for the connection state changed event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.off('connectionStateChange');
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```

## off('BLEMtuChange')

```TypeScript
off(type: 'BLEMtuChange', callback?: Callback<number>): void
```

Unsubscribe mtu changed event.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLEMtuChange' | Yes | Type of the mtu changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to listen for the mtu changed event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.off('BLEMtuChange');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## offBlePhyUpdate

```TypeScript
offBlePhyUpdate(callback?: Callback<PhyValue>): void
```

Unsubscribe phy updated event.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhyValue](arkts-connectivity-ble-phyvalue-i.md)&gt; | No | Callback used to listen for the phy updated event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
function BlePhyCallback(data:ble.PhyValue) {
    console.info(`txPhy: ${data.txPhy}, rxPhy: ${data.rxPhy}`);
}
let gattServer: ble.GattServer = ble.createGattServer();
try {
    gattServer.offBlePhyUpdate(BlePhyCallback);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## on('characteristicRead')

```TypeScript
on(type: 'characteristicRead', callback: Callback<CharacteristicReadRequest>): void
```

Subscribe characteristic read event. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual.

**Since:** 10

**Required permissions:** 
- API version 26 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 25: N/A
- API versions 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'characteristicRead' | Yes | Type of the characteristic read event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CharacteristicReadRequest](arkts-connectivity-ble-characteristicreadrequest-i.md)&gt; | Yes | Callback used to listen for the characteristic read event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**Applicable version:** 10 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let arrayBufferCCC = new ArrayBuffer(8);
let cccValue = new Uint8Array(arrayBufferCCC);
cccValue[0] = 1;
let gattServer: ble.GattServer = ble.createGattServer();
function ReadCharacteristicReq(characteristicReadRequest: ble.CharacteristicReadRequest) {
    let deviceId: string = characteristicReadRequest.deviceId;
    let transId: number = characteristicReadRequest.transId;
    let offset: number = characteristicReadRequest.offset;
    let characteristicUuid: string = characteristicReadRequest.characteristicUuid;

    let serverResponse: ble.ServerResponse = {deviceId: deviceId, transId: transId, status: 0, offset: offset, value:arrayBufferCCC};

    try {
        gattServer.sendResponse(serverResponse);
    } catch (err) {
        console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    }
}
gattServer.on('characteristicRead', ReadCharacteristicReq);
```

## on('characteristicWrite')

```TypeScript
on(type: 'characteristicWrite', callback: Callback<CharacteristicWriteRequest>): void
```

Subscribe characteristic write event. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual.

**Since:** 10

**Required permissions:** 
- API version 26 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 25: N/A
- API versions 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'characteristicWrite' | Yes | Type of the characteristic write event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CharacteristicWriteRequest](arkts-connectivity-ble-characteristicwriterequest-i.md)&gt; | Yes | Callback used to listen for the characteristic write event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**Applicable version:** 10 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let arrayBufferCCC = new ArrayBuffer(8);
let cccValue = new Uint8Array(arrayBufferCCC);
let gattServer: ble.GattServer = ble.createGattServer();
function WriteCharacteristicReq(characteristicWriteRequest: ble.CharacteristicWriteRequest) {
    let deviceId: string = characteristicWriteRequest.deviceId;
    let transId: number = characteristicWriteRequest.transId;
    let offset: number = characteristicWriteRequest.offset;
    let isPrepared: boolean = characteristicWriteRequest.isPrepared;
    let needRsp: boolean = characteristicWriteRequest.needRsp;
    let value: Uint8Array =  new Uint8Array(characteristicWriteRequest.value);
    let characteristicUuid: string = characteristicWriteRequest.characteristicUuid;

    cccValue[0] = value[0];
    let serverResponse: ble.ServerResponse = {deviceId: deviceId, transId: transId, status: 0, offset: offset, value:arrayBufferCCC};

    try {
        gattServer.sendResponse(serverResponse);
    } catch (err) {
        console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    }
}
gattServer.on('characteristicWrite', WriteCharacteristicReq);
```

## on('descriptorRead')

```TypeScript
on(type: 'descriptorRead', callback: Callback<DescriptorReadRequest>): void
```

Subscribe descriptor read event. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual.

**Since:** 10

**Required permissions:** 
- API version 26 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 25: N/A
- API versions 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'descriptorRead' | Yes | Type of the descriptor read event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DescriptorReadRequest](arkts-connectivity-ble-descriptorreadrequest-i.md)&gt; | Yes | Callback used to listen for the descriptor read event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**Applicable version:** 10 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let arrayBufferDesc = new ArrayBuffer(8);
let descValue = new Uint8Array(arrayBufferDesc);
descValue[0] = 1;
let gattServer: ble.GattServer = ble.createGattServer();
function ReadDescriptorReq(descriptorReadRequest: ble.DescriptorReadRequest) {
    let deviceId: string = descriptorReadRequest.deviceId;
    let transId: number = descriptorReadRequest.transId;
    let offset: number = descriptorReadRequest.offset;
    let descriptorUuid: string = descriptorReadRequest.descriptorUuid;

    let serverResponse: ble.ServerResponse = {deviceId: deviceId, transId: transId, status: 0, offset: offset, value:arrayBufferDesc};

    try {
        gattServer.sendResponse(serverResponse);
    } catch (err) {
        console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    }
}
gattServer.on('descriptorRead', ReadDescriptorReq);
```

## on('descriptorWrite')

```TypeScript
on(type: 'descriptorWrite', callback: Callback<DescriptorWriteRequest>): void
```

Subscribe descriptor write event. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual.

**Since:** 10

**Required permissions:** 
- API version 26 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 25: N/A
- API versions 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'descriptorWrite' | Yes | Type of the descriptor write event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DescriptorWriteRequest](arkts-connectivity-ble-descriptorwriterequest-i.md)&gt; | Yes | Callback used to listen for the descriptor write event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**Applicable version:** 10 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let arrayBufferDesc = new ArrayBuffer(8);
let descValue = new Uint8Array(arrayBufferDesc);
let gattServer: ble.GattServer = ble.createGattServer();
function WriteDescriptorReq(descriptorWriteRequest: ble.DescriptorWriteRequest) {
    let deviceId: string = descriptorWriteRequest.deviceId;
    let transId: number = descriptorWriteRequest.transId;
    let offset: number = descriptorWriteRequest.offset;
    let isPrepared: boolean = descriptorWriteRequest.isPrepared;
    let needRsp: boolean = descriptorWriteRequest.needRsp;
    let value: Uint8Array = new Uint8Array(descriptorWriteRequest.value);
    let descriptorUuid: string = descriptorWriteRequest.descriptorUuid;

    descValue[0] = value[0];
    let serverResponse: ble.ServerResponse = {deviceId: deviceId, transId: transId, status: 0, offset: offset, value:arrayBufferDesc};

    try {
        gattServer.sendResponse(serverResponse);
    } catch (err) {
        console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    }
}
gattServer.on('descriptorWrite', WriteDescriptorReq);
```

## on('connectionStateChange')

```TypeScript
on(type: 'connectionStateChange', callback: Callback<BLEConnectionChangeState>): void
```

Subscribe server connection state changed event. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual.

**Since:** 10

**Required permissions:** 
- API version 26 and later: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 25: N/A
- API versions 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connectionStateChange' | Yes | Type of the connection state changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLEConnectionChangeState](arkts-connectivity-ble-bleconnectionchangestate-i.md)&gt; | Yes | Callback used to listen for the connection state changed event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**Applicable version:** 10 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { constant } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
let connected = (bleConnectionChangeState: ble.BLEConnectionChangeState) => {
    let deviceId: string = bleConnectionChangeState.deviceId;
    let status: constant.ProfileConnectionState = bleConnectionChangeState.state;
}
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.on('connectionStateChange', connected);
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```

## on('BLEMtuChange')

```TypeScript
on(type: 'BLEMtuChange', callback: Callback<number>): void
```

Subscribe mtu changed event.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLEMtuChange' | Yes | Type of the mtu changed event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to listen for the mtu changed event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.on('BLEMtuChange', (mtu: number) => {
    console.info('BLEMtuChange, mtu: ' + mtu);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## onBlePhyUpdate

```TypeScript
onBlePhyUpdate(callback: Callback<PhyValue>): void
```

Subscribe phy updated event.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhyValue](arkts-connectivity-ble-phyvalue-i.md)&gt; | Yes | Callback used to listen for the phy updated event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
function BlePhyCallback(data:ble.PhyValue) {
    console.info(`txPhy: ${data.txPhy}, rxPhy: ${data.rxPhy}`);
}
let gattServer: ble.GattServer = ble.createGattServer();
try {
    gattServer.onBlePhyUpdate(BlePhyCallback);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## readPhy

```TypeScript
readPhy(deviceId: string): Promise<PhyValue>
```

Read the phy associated with the connection.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PhyValue](arkts-connectivity-ble-phyvalue-i.md)&gt; | Promise used to return the phy value read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |
| 2901003 | The connection is not established. |

**Examples**

```TypeScript
let gattServer: ble.GattServer = ble.createGattServer();
let deviceId: string = 'XX:XX:XX:XX:XX:XX';
try {
    gattServer.readPhy(deviceId).then((phyValue:ble.PhyValue) => {
        console.info(`txPhy: ${phyValue.txPhy}, rxPhy: ${phyValue.rxPhy}`);
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## removeAllServices

```TypeScript
removeAllServices(): void
```

Removes all services from the list of GATT services offered by this device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API because the short-range chip is not inserted on the 2in1 device. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
let server: ble.GattServer = ble.createGattServer();
try {
    server.removeAllServices();
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## removeService

```TypeScript
removeService(serviceUuid: string): void
```

Removes a specified service from the list of GATT services provided by this device.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceUuid | string | Yes | Indicates the UUID of the service to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900004 | Profile not supported. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let server: ble.GattServer = ble.createGattServer();
try {
    server.removeService('00001810-0000-1000-8000-00805F9B34FB');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## sendResponse

```TypeScript
sendResponse(serverResponse: ServerResponse): void
```

Sends a response to a specified read or write request to a given BLE peripheral device.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serverResponse | [ServerResponse](arkts-connectivity-ble-serverresponse-i.md) | Yes | Indicates the response parameters [ServerResponse](arkts-connectivity-ble-serverresponse-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
/* send response */
let arrayBufferCCC = new ArrayBuffer(8);
let cccValue = new Uint8Array(arrayBufferCCC);
cccValue[0] = 1;
let serverResponse: ble.ServerResponse = {
    deviceId: 'XX:XX:XX:XX:XX:XX',
    transId: 0,
    status: 0,
    offset: 0,
    value: arrayBufferCCC
};
try {
    let gattServer: ble.GattServer = ble.createGattServer();
    gattServer.sendResponse(serverResponse);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## setPhy

```TypeScript
setPhy(deviceId: string, phyValue: PhyValue): Promise<void>
```

Set the preferred phy associated with the connection. Whether the phy value will be changed depends on the strategy of the Bluetooth chip. A successful call to this interface does not guarantee that the chip's phy value has been successfully set.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |
| phyValue | [PhyValue](arkts-connectivity-ble-phyvalue-i.md) | Yes | Indicates the phy to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |
| 2901003 | The connection is not established. |

**Examples**

```TypeScript
let gattServer: ble.GattServer = ble.createGattServer();
let deviceId: string = 'XX:XX:XX:XX:XX:XX';
try {
    let phyValue:ble.PhyValue = {
        txPhy: ble.BlePhy.BLE_PHY_1M,
        rxPhy: ble.BlePhy.BLE_PHY_1M
    };
    gattServer.setPhy(deviceId,phyValue);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
