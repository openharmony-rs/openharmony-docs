# @ohos.bluetooth.common (Bluetooth Common Module)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

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

## BluetoothAddressType

Enumerate the address types of the Bluetooth device. The actual MAC address of a Bluetooth device is private information. During device discovery, the Bluetooth subsystem assigns a virtual MAC address to each Bluetooth device and saves the mapping between the virtual MAC address and the actual MAC address.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name                | Value | Description    |
| ------------------ | ---- | ------ |
| VIRTUAL        | 1    | Virtual MAC address.|
| REAL       | 2    | Actual MAC address.|
