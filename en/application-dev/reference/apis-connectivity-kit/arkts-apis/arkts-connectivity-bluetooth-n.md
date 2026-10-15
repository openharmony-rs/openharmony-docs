# bluetooth

```TypeScript
declare namespace bluetooth
```

Provides methods to operate or manage Bluetooth.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** bluetoothManager

<!--Device-unnamed-declare namespace bluetooth--><!--Device-unnamed-declare namespace bluetooth-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [BLE](arkts-connectivity-bluetooth-ble-n.md) | Provides methods to operate or manage Bluetooth. |

### Functions

| Name | Description |
| --- | --- |
| [disableBluetooth](arkts-connectivity-bluetooth-disablebluetooth-f.md#disablebluetooth) | Disables Bluetooth on a device. |
| [enableBluetooth](arkts-connectivity-bluetooth-enablebluetooth-f.md#enablebluetooth) | Enables Bluetooth on a device. |
| [getBluetoothScanMode](arkts-connectivity-bluetooth-getbluetoothscanmode-f.md#getbluetoothscanmode) | Obtains the Bluetooth scanning mode of a device. |
| [getBtConnectionState](arkts-connectivity-bluetooth-getbtconnectionstate-f.md#getbtconnectionstate) | Get the local device connection state to any profile of any remote device. |
| [getLocalName](arkts-connectivity-bluetooth-getlocalname-f.md#getlocalname) | Obtains the Bluetooth local name of a device. |
| [getPairedDevices](arkts-connectivity-bluetooth-getpaireddevices-f.md#getpaireddevices) | Obtains the list of Bluetooth devices that have been paired with the current device. |
| [getProfile](arkts-connectivity-bluetooth-getprofile-f.md#getprofile) | Obtains the instance of profile. |
| [getProfileConnState](arkts-connectivity-bluetooth-getprofileconnstate-f.md#getprofileconnstate) | Obtains the connection state of profile. |
| [getRemoteDeviceClass](arkts-connectivity-bluetooth-getremotedeviceclass-f.md#getremotedeviceclass) | Obtains the class of a peer Bluetooth device. |
| [getRemoteDeviceName](arkts-connectivity-bluetooth-getremotedevicename-f.md#getremotedevicename) | Obtains the name of a peer Bluetooth device. |
| [getState](arkts-connectivity-bluetooth-getstate-f.md#getstate) | Obtains the Bluetooth status of a device. |
| [off('bluetoothDeviceFind')](arkts-connectivity-bluetooth-off-f.md#offbluetoothdevicefind) | Unsubscribe the event reported when a remote Bluetooth device is discovered. |
| [off('bondStateChange')](arkts-connectivity-bluetooth-off-f.md#offbondstatechange) | Unsubscribe the event reported when a remote Bluetooth device is bonded. |
| [off('pinRequired')](arkts-connectivity-bluetooth-off-f.md#offpinrequired) | Unsubscribe the event of a pairing request from a remote Bluetooth device. |
| [off('stateChange')](arkts-connectivity-bluetooth-off-f.md#offstatechange) | Unsubscribe the event reported when the Bluetooth state changes. |
| [off('sppRead')](arkts-connectivity-bluetooth-off-f.md#offsppread) | Unsubscribe the event reported when data is read from the socket. |
| [on('bluetoothDeviceFind')](arkts-connectivity-bluetooth-on-f.md#onbluetoothdevicefind) | Subscribe the event reported when a remote Bluetooth device is discovered. |
| [on('bondStateChange')](arkts-connectivity-bluetooth-on-f.md#onbondstatechange) | Subscribe the event reported when a remote Bluetooth device is bonded. |
| [on('pinRequired')](arkts-connectivity-bluetooth-on-f.md#onpinrequired) | Subscribe the event of a pairing request from a remote Bluetooth device. |
| [on('stateChange')](arkts-connectivity-bluetooth-on-f.md#onstatechange) | Subscribe the event reported when the Bluetooth state changes. |
| [on('sppRead')](arkts-connectivity-bluetooth-on-f.md#onsppread) | Subscribe the event reported when data is read from the socket. |
| [pairDevice](arkts-connectivity-bluetooth-pairdevice-f.md#pairdevice) | Starts pairing with a remote Bluetooth device. |
| [setBluetoothScanMode](arkts-connectivity-bluetooth-setbluetoothscanmode-f.md#setbluetoothscanmode) | Sets the Bluetooth scan mode for a device. |
| [setDevicePairingConfirmation](arkts-connectivity-bluetooth-setdevicepairingconfirmation-f.md#setdevicepairingconfirmation) | Sets the confirmation of pairing with a certain device. |
| [setLocalName](arkts-connectivity-bluetooth-setlocalname-f.md#setlocalname) | Sets the Bluetooth friendly name of a device. |
| [sppAccept](arkts-connectivity-bluetooth-sppaccept-f.md#sppaccept) | Waits for a remote device to connect. |
| [sppCloseClientSocket](arkts-connectivity-bluetooth-sppcloseclientsocket-f.md#sppcloseclientsocket) | Disables an spp client socket and releases related resources. |
| [sppCloseServerSocket](arkts-connectivity-bluetooth-sppcloseserversocket-f.md#sppcloseserversocket) | Disables an spp server socket and releases related resources. |
| [sppConnect](arkts-connectivity-bluetooth-sppconnect-f.md#sppconnect) | Connects to a remote device over the socket. |
| [sppListen](arkts-connectivity-bluetooth-spplisten-f.md#spplisten) | Creates a Bluetooth server listening socket. |
| [sppWrite](arkts-connectivity-bluetooth-sppwrite-f.md#sppwrite) | Write data through the socket. |
| [startBluetoothDiscovery](arkts-connectivity-bluetooth-startbluetoothdiscovery-f.md#startbluetoothdiscovery) | Starts scanning Bluetooth devices. |
| [stopBluetoothDiscovery](arkts-connectivity-bluetooth-stopbluetoothdiscovery-f.md#stopbluetoothdiscovery) | Stops Bluetooth device scanning. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [cancelPairedDevice](arkts-connectivity-bluetooth-cancelpaireddevice-f-sys.md#cancelpaireddevice) | Remove a paired remote device. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [A2dpSourceProfile](arkts-connectivity-bluetooth-a2dpsourceprofile-i.md) | Manager a2dp source profile. |
| [AdvertiseData](arkts-connectivity-bluetooth-advertisedata-i.md) | Describes the advertising data. |
| [AdvertiseSetting](arkts-connectivity-bluetooth-advertisesetting-i.md) | Describes the settings for BLE advertising. |
| [BaseProfile](arkts-connectivity-bluetooth-baseprofile-i.md) | Base interface of profile. |
| [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) | Describes the Gatt characteristic. |
| [BLEConnectChangedState](arkts-connectivity-bluetooth-bleconnectchangedstate-i.md) | Describes the Gatt profile connection state. |
| [BLEDescriptor](arkts-connectivity-bluetooth-bledescriptor-i.md) | Describes the Gatt descriptor. |
| [BondStateParam](arkts-connectivity-bluetooth-bondstateparam-i.md) | Describes the class of a bluetooth device. |
| [CharacteristicReadReq](arkts-connectivity-bluetooth-characteristicreadreq-i.md) | Describes the parameters of the Gatt client's characteristic read request. |
| [CharacteristicWriteReq](arkts-connectivity-bluetooth-characteristicwritereq-i.md) | Describes the parameters of the of the Gatt client's characteristic write request. |
| [DescriptorReadReq](arkts-connectivity-bluetooth-descriptorreadreq-i.md) | Describes the parameters of the Gatt client's descriptor read request. |
| [DescriptorWriteReq](arkts-connectivity-bluetooth-descriptorwritereq-i.md) | Describes the parameters of the Gatt client's characteristic write request. |
| [DeviceClass](arkts-connectivity-bluetooth-deviceclass-i.md) | Describes the class of a bluetooth device. |
| [GattClientDevice](arkts-connectivity-bluetooth-gattclientdevice-i.md) | Manages GATT client. Before calling an Gatt client method, you must use [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) to create an GattClientDevice instance. |
| [GattServer](arkts-connectivity-bluetooth-gattserver-i.md) | Manages GATT server. Before calling an Gatt server method, you must use [createGattServer](arkts-connectivity-ble-creategattserver-f.md) to create an GattServer instance. |
| [GattService](arkts-connectivity-bluetooth-gattservice-i.md) | Describes the Gatt service. |
| [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetooth-handsfreeaudiogatewayprofile-i.md) | Manager handsfree AG profile. |
| [ManufactureData](arkts-connectivity-bluetooth-manufacturedata-i.md) | Describes the manufacturer data. |
| [NotifyCharacteristic](arkts-connectivity-bluetooth-notifycharacteristic-i.md) | Describes the value of the indication or notification sent by the Gatt server. |
| [PinRequiredParam](arkts-connectivity-bluetooth-pinrequiredparam-i.md) | Describes the bond key param. |
| [ScanFilter](arkts-connectivity-bluetooth-scanfilter-i.md) | Describes the criteria for filtering scanning results can be set. |
| [ScanOptions](arkts-connectivity-bluetooth-scanoptions-i.md) | Describes the parameters for scan. |
| [ScanResult](arkts-connectivity-bluetooth-scanresult-i.md) | Describes the contents of the scan results. |
| [ServerResponse](arkts-connectivity-bluetooth-serverresponse-i.md) | Describes the parameters of a response send by the server to a specified read or write request. |
| [ServiceData](arkts-connectivity-bluetooth-servicedata-i.md) | Describes the service data. |
| [SppOption](arkts-connectivity-bluetooth-sppoption-i.md) | Describes the spp parameters. |
| [StateChangeParam](arkts-connectivity-bluetooth-statechangeparam-i.md) | Profile state change parameters. |

### Enums

| Name | Description |
| --- | --- |
| [BluetoothState](arkts-connectivity-bluetooth-bluetoothstate-e.md) | The enum of bluetooth state. |
| [BondState](arkts-connectivity-bluetooth-bondstate-e.md) | The enum of bond state. |
| [MajorClass](arkts-connectivity-bluetooth-majorclass-e.md) | The enum of major class of a bluetooth device. |
| [MajorMinorClass](arkts-connectivity-bluetooth-majorminorclass-e.md) | The enum of major minor class of a bluetooth device. |
| [MatchMode](arkts-connectivity-bluetooth-matchmode-e.md) | The enum of BLE match mode. |
| [PlayingState](arkts-connectivity-bluetooth-playingstate-e.md) | The enum of a2dp playing state. |
| [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md) | The enum of profile connection state. |
| [ProfileId](arkts-connectivity-bluetooth-profileid-e.md) | The enum of profile id. |
| [ScanDuty](arkts-connectivity-bluetooth-scanduty-e.md) | The enum of scan duty. |
| [ScanMode](arkts-connectivity-bluetooth-scanmode-e.md) | The enum of BR scan mode. |
| [SppType](arkts-connectivity-bluetooth-spptype-e.md) | The enum of SPP type. |
