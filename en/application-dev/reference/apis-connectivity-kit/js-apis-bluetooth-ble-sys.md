# @ohos.bluetooth.ble (Bluetooth BLE Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

This module provides [Bluetooth Low Energy (BLE)](../../connectivity/terminology.md#ble) capabilities. The first batch of APIs include the characteristic value write method based on the [Generic Attribute Profile (GATT)](../../connectivity/terminology.md#gatt).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.bluetooth.ble (Bluetooth BLE Module)](js-apis-bluetooth-ble.md).



## Modules to Import

```js
import { ble } from '@kit.ConnectivityKit';
```

## GattClientDevice

Represents a GATT client class. It provides APIs for connecting to and transmitting data with the server.

- Before using the methods of this class, use the [createGattClientDevice](js-apis-bluetooth-ble.md#blecreategattclientdevice) method to construct an instance of this class.
- You can create multiple instances of this class to manage multiple GATT connections.

### writeCharacteristicValueWithContext

writeCharacteristicValueWithContext(characteristic: BLECharacteristic, writeType: GattWriteType): Promise&lt;GattRspContext&gt;

Writes a value to the specified characteristic. This API uses a promise to return the result.<br>
- Unlike the [writeCharacteristicValue](js-apis-bluetooth-ble.md#writecharacteristicvalue) API, this API supports the function of returning responses from the server. After the characteristic value is written, the caller can obtain the timestamp and other information of the response message received by the local end from the server.
- This API supports only the write mode where writeType is set to [WRITE](js-apis-bluetooth-ble.md#gattwritetype) to obtain the response information from the server.
- You need to call [getServices](js-apis-bluetooth-ble.md#getservices) to obtain all capabilities supported by the server, and the specified input parameter characteristic value UUID must be included. Otherwise, the write operation fails.<br>
- You can call the following APIs only after receiving an asynchronous callback: [readCharacteristicValue](js-apis-bluetooth-ble.md#readcharacteristicvalue), [readDescriptorValue](js-apis-bluetooth-ble.md#readdescriptorvalue), [writeCharacteristicValue](js-apis-bluetooth-ble.md#writecharacteristicvalue), [writeDescriptorValue](js-apis-bluetooth-ble.md#writedescriptorvalue), [setCharacteristicChangeNotification](js-apis-bluetooth-ble.md#setcharacteristicchangenotification), and [setCharacteristicChangeIndication](js-apis-bluetooth-ble.md#setcharacteristicchangeindication).<br>
- The length of the characteristic data that can be written by an application at a time is limited to (MTU-3) bytes. The caller can specify the MTU size by calling [setBLEMtuSize](js-apis-bluetooth-ble.md#setblemtusize) as required to change the length of the characteristic data that can be written at a time.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name           | Type                                     | Mandatory  | Description                 |
| -------------- | --------------------------------------- | ---- | ------------------- |
| characteristic | [BLECharacteristic](js-apis-bluetooth-ble.md#blecharacteristic) | Yes   | Characteristic to write.|
| writeType | [GattWriteType](js-apis-bluetooth-ble.md#gattwritetype) | Yes   | Write mode.|

**Return value**

| Type                                      | Description                        |
| ---------------------------------------- | -------------------------- |
| Promise&lt;GattRspContext&gt; | Promise used to return the [GattRspContext](#gattrspcontext) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs.                 |
|801 | Capability not supported.          |
|2900011 | The operation is busy. The last operation is not complete.             |
|2900099 | Operation failed.                        |
|2901001 | Write forbidden.                        |
|2901003 | The connection is not established.                |
|2901004 | The connection is congested.                |
|2901005 | The connection is not encrypted.                |
|2901006 | The connection is not authenticated.                |
|2901007 | The connection is not authorized.                |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
let descriptors: Array<ble.BLEDescriptor>  = [];
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // Use the Client Characteristic Configuration descriptor as an example. When bit 0 and bit 1 are both set to 0, the notification and indication functions are disabled.
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  characteristicValue: bufferCCC, descriptors:descriptors};
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.writeCharacteristicValueWithContext(characteristic, ble.GattWriteType.WRITE).then((rspContext: ble.GattRspContext) => {
        console.info('timestamp is: ' + rspContext.timestamp);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## GattRspContext

Information reported by the Bluetooth subsystem to the application after the client calls the [writeCharacteristicValueWithContext](#writecharacteristicvaluewithcontext) API and receives a response from the server.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name      | Type       | Read-Only| Optional  | Description                                |
| -------- | ----------- | ---- | ---- | ---------------------------------- |
| timestamp     | number      | No| No   | Time when the local end receives the GATT response message from the peer end, in the UNIX timestamp format. The value is in microseconds.                   |
