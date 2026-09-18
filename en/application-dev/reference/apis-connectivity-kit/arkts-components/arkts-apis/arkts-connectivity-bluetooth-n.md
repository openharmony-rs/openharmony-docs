# bluetooth

Provides methods to operate or manage Bluetooth.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** bluetoothManager

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
| [getState](arkts-connectivity-bluetooth-getstate-f.md) | Obtains the Bluetooth status of a device. |
| [getBtConnectionState](arkts-connectivity-bluetooth-getbtconnectionstate-f.md) | Get the local device connection state to any profile of any remote device. |
| [pairDevice](arkts-connectivity-bluetooth-pairdevice-f.md) | Starts pairing with a remote Bluetooth device. |
| [getRemoteDeviceName](arkts-connectivity-bluetooth-getremotedevicename-f.md) | Obtains the name of a peer Bluetooth device. |
| [getRemoteDeviceClass](arkts-connectivity-bluetooth-getremotedeviceclass-f.md) | Obtains the class of a peer Bluetooth device. |
| [enableBluetooth](arkts-connectivity-bluetooth-enablebluetooth-f.md) | Enables Bluetooth on a device. |
| [disableBluetooth](arkts-connectivity-bluetooth-disablebluetooth-f.md) | Disables Bluetooth on a device. |
| [getLocalName](arkts-connectivity-bluetooth-getlocalname-f.md) | Obtains the Bluetooth local name of a device. |
| [getPairedDevices](arkts-connectivity-bluetooth-getpaireddevices-f.md) | Obtains the list of Bluetooth devices that have been paired with the current device. |
| [getProfileConnState](arkts-connectivity-bluetooth-getprofileconnstate-f.md) | Obtains the connection state of profile. |
| [setDevicePairingConfirmation](arkts-connectivity-bluetooth-setdevicepairingconfirmation-f.md) | Sets the confirmation of pairing with a certain device. |
| [setLocalName](arkts-connectivity-bluetooth-setlocalname-f.md) | Sets the Bluetooth friendly name of a device. |
| [setBluetoothScanMode](arkts-connectivity-bluetooth-setbluetoothscanmode-f.md) | Sets the Bluetooth scan mode for a device. |
| [getBluetoothScanMode](arkts-connectivity-bluetooth-getbluetoothscanmode-f.md) | Obtains the Bluetooth scanning mode of a device. |
| [startBluetoothDiscovery](arkts-connectivity-bluetooth-startbluetoothdiscovery-f.md) | Starts scanning Bluetooth devices. |
| [stopBluetoothDiscovery](arkts-connectivity-bluetooth-stopbluetoothdiscovery-f.md) | Stops Bluetooth device scanning. |
| [on](arkts-connectivity-bluetooth-on-f.md#onbluetoothdevicefind) | Subscribe the event reported when a remote Bluetooth device is discovered. |
| [off](arkts-connectivity-bluetooth-off-f.md#offbluetoothdevicefind) | Unsubscribe the event reported when a remote Bluetooth device is discovered. |
| [on](arkts-connectivity-bluetooth-on-f.md#onbondstatechange) | Subscribe the event reported when a remote Bluetooth device is bonded. |
| [off](arkts-connectivity-bluetooth-off-f.md#offbondstatechange) | Unsubscribe the event reported when a remote Bluetooth device is bonded. |
| [on](arkts-connectivity-bluetooth-on-f.md#onpinrequired) | Subscribe the event of a pairing request from a remote Bluetooth device. |
| [off](arkts-connectivity-bluetooth-off-f.md#offpinrequired) | Unsubscribe the event of a pairing request from a remote Bluetooth device. |
| [on](arkts-connectivity-bluetooth-on-f.md#onstatechange) | Subscribe the event reported when the Bluetooth state changes. |
| [off](arkts-connectivity-bluetooth-off-f.md#offstatechange) | Unsubscribe the event reported when the Bluetooth state changes. |
| [sppListen](arkts-connectivity-bluetooth-spplisten-f.md) | Creates a Bluetooth server listening socket. |
| [sppAccept](arkts-connectivity-bluetooth-sppaccept-f.md) | Waits for a remote device to connect. |
| [sppConnect](arkts-connectivity-bluetooth-sppconnect-f.md) | Connects to a remote device over the socket. |
| [sppCloseServerSocket](arkts-connectivity-bluetooth-sppcloseserversocket-f.md) | Disables an spp server socket and releases related resources. |
| [sppCloseClientSocket](arkts-connectivity-bluetooth-sppcloseclientsocket-f.md) | Disables an spp client socket and releases related resources. |
| [sppWrite](arkts-connectivity-bluetooth-sppwrite-f.md) | Write data through the socket. |
| [on](arkts-connectivity-bluetooth-on-f.md#onsppread) | Subscribe the event reported when data is read from the socket. |
| [off](arkts-connectivity-bluetooth-off-f.md#offsppread) | Unsubscribe the event reported when data is read from the socket. |
| [getProfile](arkts-connectivity-bluetooth-getprofile-f.md) | Obtains the instance of profile. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [cancelPairedDevice](arkts-connectivity-bluetooth-cancelpaireddevice-f-sys.md) | Remove a paired remote device. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BaseProfile](arkts-connectivity-bluetooth-baseprofile-i.md) | Base interface of profile. |
| [A2dpSourceProfile](arkts-connectivity-bluetooth-a2dpsourceprofile-i.md) | Manager a2dp source profile. |
| [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetooth-handsfreeaudiogatewayprofile-i.md) | Manager handsfree AG profile. |
| [GattServer](arkts-connectivity-bluetooth-gattserver-i.md) | Manages GATT server. Before calling an Gatt server method, you must use [createGattServer](arkts-connectivity-ble-creategattserver-f.md) to create an GattServer instance. |
| [GattClientDevice](arkts-connectivity-bluetooth-gattclientdevice-i.md) | Manages GATT client. Before calling an Gatt client method, you must use [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) to create an GattClientDevice instance. |
| [GattService](arkts-connectivity-bluetooth-gattservice-i.md) | Describes the Gatt service. |
| [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) | Describes the Gatt characteristic. |
| [BLEDescriptor](arkts-connectivity-bluetooth-bledescriptor-i.md) | Describes the Gatt descriptor. |
| [NotifyCharacteristic](arkts-connectivity-bluetooth-notifycharacteristic-i.md) | Describes the value of the indication or notification sent by the Gatt server. |
| [CharacteristicReadReq](arkts-connectivity-bluetooth-characteristicreadreq-i.md) | Describes the parameters of the Gatt client's characteristic read request. |
| [CharacteristicWriteReq](arkts-connectivity-bluetooth-characteristicwritereq-i.md) | Describes the parameters of the of the Gatt client's characteristic write request. |
| [DescriptorReadReq](arkts-connectivity-bluetooth-descriptorreadreq-i.md) | Describes the parameters of the Gatt client's descriptor read request. |
| [DescriptorWriteReq](arkts-connectivity-bluetooth-descriptorwritereq-i.md) | Describes the parameters of the Gatt client's characteristic write request. |
| [ServerResponse](arkts-connectivity-bluetooth-serverresponse-i.md) | Describes the parameters of a response send by the server to a specified read or write request. |
| [BLEConnectChangedState](arkts-connectivity-bluetooth-bleconnectchangedstate-i.md) | Describes the Gatt profile connection state. |
| [ScanResult](arkts-connectivity-bluetooth-scanresult-i.md) | Describes the contents of the scan results. |
| [AdvertiseSetting](arkts-connectivity-bluetooth-advertisesetting-i.md) | Describes the settings for BLE advertising. |
| [AdvertiseData](arkts-connectivity-bluetooth-advertisedata-i.md) | Describes the advertising data. |
| [ManufactureData](arkts-connectivity-bluetooth-manufacturedata-i.md) | Describes the manufacturer data. |
| [ServiceData](arkts-connectivity-bluetooth-servicedata-i.md) | Describes the service data. |
| [ScanFilter](arkts-connectivity-bluetooth-scanfilter-i.md) | Describes the criteria for filtering scanning results can be set. |
| [ScanOptions](arkts-connectivity-bluetooth-scanoptions-i.md) | Describes the parameters for scan. |
| [SppOption](arkts-connectivity-bluetooth-sppoption-i.md) | Describes the spp parameters. |
| [PinRequiredParam](arkts-connectivity-bluetooth-pinrequiredparam-i.md) | Describes the bond key param. |
| [DeviceClass](arkts-connectivity-bluetooth-deviceclass-i.md) | Describes the class of a bluetooth device. |
| [BondStateParam](arkts-connectivity-bluetooth-bondstateparam-i.md) | Describes the class of a bluetooth device. |
| [StateChangeParam](arkts-connectivity-bluetooth-statechangeparam-i.md) | Profile state change parameters. |

### Enums

| Name | Description |
| --- | --- |
| [ScanDuty](arkts-connectivity-bluetooth-scanduty-e.md) | The enum of scan duty. |
| [MatchMode](arkts-connectivity-bluetooth-matchmode-e.md) | The enum of BLE match mode. |
| [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md) | The enum of profile connection state. |
| [BluetoothState](arkts-connectivity-bluetooth-bluetoothstate-e.md) | The enum of bluetooth state. |
| [SppType](arkts-connectivity-bluetooth-spptype-e.md) | The enum of SPP type. |
| [ScanMode](arkts-connectivity-bluetooth-scanmode-e.md) | The enum of BR scan mode. |
| [BondState](arkts-connectivity-bluetooth-bondstate-e.md) | The enum of bond state. |
| [MajorClass](arkts-connectivity-bluetooth-majorclass-e.md) | The enum of major class of a bluetooth device. |
| [MajorMinorClass](arkts-connectivity-bluetooth-majorminorclass-e.md) | The enum of major minor class of a bluetooth device. |
| [PlayingState](arkts-connectivity-bluetooth-playingstate-e.md) | The enum of a2dp playing state. |
| [ProfileId](arkts-connectivity-bluetooth-profileid-e.md) | The enum of profile id. |
