# @ohos.bluetooth.common (Bluetooth Common Module)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=70e02f92e8ba0ab4c9c44ed0461b8cded7089b65 translatedAt=2026-09-15T02:28:14.263Z pushedAt=2026-09-15T11:34:38.207Z -->

This module provides Bluetooth common APIs and parameter types. The first batch of APIs allow applications to specify the MAC address and address type of the target device when calling [connection.pairDevice](../../reference/apis-connectivity-kit/js-apis-bluetooth-connection.md#connectionpairdevice21).

> **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { common } from '@kit.ConnectivityKit';
```

## BluetoothAddress

Defines the address information of a Bluetooth device, including the address and address type.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name      | Type  | Read-Only  | Optional  | Description         |
| -------- | ------ | ---- | ---- | ----------- |
| address    | string      | No   | No   | Address of the Bluetooth device, for example, XX:XX:XX:XX:XX:XX.|
| addressType     | [BluetoothAddressType](#bluetoothaddresstype)      | No   | No   | Address type, which can be the actual or virtual MAC address of the Bluetooth device.|
| rawAddressType<sup>23+</sup>     | [BluetoothRawAddressType](#bluetoothrawaddresstype23)      | No    | Yes    | Bluetooth device address type defined by the Bluetooth protocol, which can be **Public** or **Random**. For details about the default value, see the related API description. If no value is passed, the default address type of the system is used.|

## BluetoothAddressType

Enumerates the Bluetooth device address types defined by the Bluetooth subsystem. The actual MAC address of a Bluetooth device is private information. During device discovery, the Bluetooth subsystem assigns a virtual MAC address to each Bluetooth device and saves the mapping between the virtual MAC address and the actual MAC address. For details about the address types, see [Bluetooth Device Address Type](../../connectivity/bluetooth/bluetooth-overview.md#bluetooth-device-address-type).

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name                | Value | Description    |
| ------------------ | ---- | ------ |
| VIRTUAL        | 1    | Virtual MAC address.|
| REAL       | 2    | Actual MAC address.|

## BluetoothRawAddressType<sup>23+</sup>

Enumerates the Bluetooth device address types defined by the Bluetooth protocol. For details about the address types, see [Bluetooth Device Address Type](../../connectivity/bluetooth/bluetooth-overview.md#bluetooth-device-address-type).

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name                | Value | Description    |
| ------------------ | ---- | ------ |
| PUBLIC        | 0    | Public device address type, which is allocated by the IEEE and is globally unique. The address remains unchanged permanently. |
| RANDOM       | 1    | Random device address type, which is randomly generated and includes sub-types such as static random address and private random address. The address may change periodically.|