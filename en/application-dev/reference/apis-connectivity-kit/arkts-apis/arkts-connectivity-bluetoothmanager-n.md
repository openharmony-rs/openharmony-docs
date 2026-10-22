# bluetoothManager

```TypeScript
declare namespace bluetoothManager
```

Provides methods to operate or manage Bluetooth.

**Since:** 9

**Deprecated since:** 10

<!--Device-unnamed-declare namespace bluetoothManager--><!--Device-unnamed-declare namespace bluetoothManager-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [BLE](arkts-connectivity-bluetoothmanager-ble-n.md) | Provides methods to operate or manage Bluetooth. |

### Functions

| Name | Description |
| --- | --- |
| [disableBluetooth](arkts-connectivity-bluetoothmanager-disablebluetooth-f.md#disablebluetooth-1) | Disables Bluetooth on a device. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |
| [enableBluetooth](arkts-connectivity-bluetoothmanager-enablebluetooth-f.md#enablebluetooth-1) | Enables Bluetooth on a device. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |
| [getBluetoothScanMode](arkts-connectivity-bluetoothmanager-getbluetoothscanmode-f.md#getbluetoothscanmode-1) | Obtains the Bluetooth scanning mode of a device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [getBtConnectionState](arkts-connectivity-bluetoothmanager-getbtconnectionstate-f.md#getbtconnectionstate-1) | Get the local device connection state to any profile of any remote device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [getLocalName](arkts-connectivity-bluetoothmanager-getlocalname-f.md#getlocalname-1) | Obtains the Bluetooth local name of a device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [getPairedDevices](arkts-connectivity-bluetoothmanager-getpaireddevices-f.md#getpaireddevices-1) | Obtains the list of Bluetooth devices that have been paired with the current device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [getProfileConnectionState](arkts-connectivity-bluetoothmanager-getprofileconnectionstate-f.md#getprofileconnectionstate-1) | Obtains the connection state of profile. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [getProfileInstance](arkts-connectivity-bluetoothmanager-getprofileinstance-f.md#getprofileinstance-1) | Obtains the instance of profile. |
| [getRemoteDeviceClass](arkts-connectivity-bluetoothmanager-getremotedeviceclass-f.md#getremotedeviceclass-1) | Obtains the class of a peer Bluetooth device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [getRemoteDeviceName](arkts-connectivity-bluetoothmanager-getremotedevicename-f.md#getremotedevicename-1) | Obtains the name of a peer Bluetooth device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [getState](arkts-connectivity-bluetoothmanager-getstate-f.md#getstate-1) | Obtains the Bluetooth status of a device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [off('bluetoothDeviceFind')](arkts-connectivity-bluetoothmanager-off-f.md#offbluetoothdevicefind) | Unsubscribe the event reported when a remote Bluetooth device is discovered. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [off('bondStateChange')](arkts-connectivity-bluetoothmanager-off-f.md#offbondstatechange) | Unsubscribe the event reported when a remote Bluetooth device is bonded. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [off('pinRequired')](arkts-connectivity-bluetoothmanager-off-f.md#offpinrequired) | Unsubscribe the event of a pairing request from a remote Bluetooth device. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |
| [off('stateChange')](arkts-connectivity-bluetoothmanager-off-f.md#offstatechange) | Unsubscribe the event reported when the Bluetooth state changes. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [off('sppRead')](arkts-connectivity-bluetoothmanager-off-f.md#offsppread) | Unsubscribe the event reported when data is read from the socket. |
| [on('bluetoothDeviceFind')](arkts-connectivity-bluetoothmanager-on-f.md#onbluetoothdevicefind) | Subscribe the event reported when a remote Bluetooth device is discovered. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [on('bondStateChange')](arkts-connectivity-bluetoothmanager-on-f.md#onbondstatechange) | Subscribe the event reported when a remote Bluetooth device is bonded. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [on('pinRequired')](arkts-connectivity-bluetoothmanager-on-f.md#onpinrequired) | Subscribe the event of a pairing request from a remote Bluetooth device. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |
| [on('stateChange')](arkts-connectivity-bluetoothmanager-on-f.md#onstatechange) | Subscribe the event reported when the Bluetooth state changes. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [on('sppRead')](arkts-connectivity-bluetoothmanager-on-f.md#onsppread) | Subscribe the event reported when data is read from the socket. |
| [pairDevice](arkts-connectivity-bluetoothmanager-pairdevice-f.md#pairdevice-1) | Starts pairing with a remote Bluetooth device. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |
| [setBluetoothScanMode](arkts-connectivity-bluetoothmanager-setbluetoothscanmode-f.md#setbluetoothscanmode-1) | Sets the Bluetooth scan mode for a device. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [setDevicePairingConfirmation](arkts-connectivity-bluetoothmanager-setdevicepairingconfirmation-f.md#setdevicepairingconfirmation-1) | Sets the confirmation of pairing with a certain device. On API 10 and above, the permission required by this interface is changed from MANAGE_BLUETOOTH to ACCESS_BLUETOOTH and MANAGE_BLUETOOTH. |
| [setLocalName](arkts-connectivity-bluetoothmanager-setlocalname-f.md#setlocalname-1) | Sets the Bluetooth friendly name of a device. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |
| [sppAccept](arkts-connectivity-bluetoothmanager-sppaccept-f.md#sppaccept-1) | Waits for a remote device to connect. |
| [sppCloseClientSocket](arkts-connectivity-bluetoothmanager-sppcloseclientsocket-f.md#sppcloseclientsocket-1) | Disables an spp client socket and releases related resources. |
| [sppCloseServerSocket](arkts-connectivity-bluetoothmanager-sppcloseserversocket-f.md#sppcloseserversocket-1) | Disables an spp server socket and releases related resources. |
| [sppConnect](arkts-connectivity-bluetoothmanager-sppconnect-f.md#sppconnect-1) | Connects to a remote device over the socket. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [sppListen](arkts-connectivity-bluetoothmanager-spplisten-f.md#spplisten-1) | Creates a Bluetooth server listening socket. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [sppWrite](arkts-connectivity-bluetoothmanager-sppwrite-f.md#sppwrite-1) | Write data through the socket. |
| [startBluetoothDiscovery](arkts-connectivity-bluetoothmanager-startbluetoothdiscovery-f.md#startbluetoothdiscovery-1) | Starts scanning Bluetooth devices. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH and LOCATION and APPROXIMATELY_LOCATION to ACCESS_BLUETOOTH. |
| [stopBluetoothDiscovery](arkts-connectivity-bluetoothmanager-stopbluetoothdiscovery-f.md#stopbluetoothdiscovery-1) | Stops Bluetooth device scanning. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [cancelPairedDevice](arkts-connectivity-bluetoothmanager-cancelpaireddevice-f-sys.md#cancelpaireddevice-1) | Remove a paired remote device. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [A2dpSourceProfile](arkts-connectivity-bluetoothmanager-a2dpsourceprofile-i.md) | Manager a2dp source profile. |
| [AdvertiseData](arkts-connectivity-bluetoothmanager-advertisedata-i.md) | Describes the advertising data. |
| [AdvertiseSetting](arkts-connectivity-bluetoothmanager-advertisesetting-i.md) | Describes the settings for BLE advertising. |
| [BaseProfile](arkts-connectivity-bluetoothmanager-baseprofile-i.md) | Base interface of profile. |
| [BLECharacteristic](arkts-connectivity-bluetoothmanager-blecharacteristic-i.md) | Describes the Gatt characteristic. |
| [BLEConnectChangedState](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md) | Describes the Gatt profile connection state. |
| [BLEDescriptor](arkts-connectivity-bluetoothmanager-bledescriptor-i.md) | Describes the Gatt descriptor. |
| [BondStateParam](arkts-connectivity-bluetoothmanager-bondstateparam-i.md) | Describes the class of a bluetooth device. |
| [CharacteristicReadRequest](arkts-connectivity-bluetoothmanager-characteristicreadrequest-i.md) | Describes the parameters of the Gatt client's characteristic read request. |
| [CharacteristicWriteRequest](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md) | Describes the parameters of the of the Gatt client's characteristic write request. |
| [DescriptorReadRequest](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md) | Describes the parameters of the Gatt client's descriptor read request. |
| [DescriptorWriteRequest](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md) | Describes the parameters of the Gatt client's characteristic write request. |
| [DeviceClass](arkts-connectivity-bluetoothmanager-deviceclass-i.md) | Describes the class of a bluetooth device. |
| [GattClientDevice](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md) | Manages GATT client. Before calling an Gatt client method, you must use [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) to create an GattClientDevice instance. |
| [GattServer](arkts-connectivity-bluetoothmanager-gattserver-i.md) | Manages GATT server. Before calling an Gatt server method, you must use [createGattServer](arkts-connectivity-ble-creategattserver-f.md) to create an GattServer instance. |
| [GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md) | Describes the Gatt service. |
| [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetoothmanager-handsfreeaudiogatewayprofile-i.md) | Manager handsfree AG profile. |
| [HidHostProfile](arkts-connectivity-bluetoothmanager-hidhostprofile-i.md) | Manager hid host profile. |
| [ManufactureData](arkts-connectivity-bluetoothmanager-manufacturedata-i.md) | Describes the manufacturer data. |
| [NotifyCharacteristic](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md) | Describes the value of the indication or notification sent by the Gatt server. |
| [PanProfile](arkts-connectivity-bluetoothmanager-panprofile-i.md) | Manager pan profile. |
| [PinRequiredParam](arkts-connectivity-bluetoothmanager-pinrequiredparam-i.md) | Describes the bond key param. |
| [ScanFilter](arkts-connectivity-bluetoothmanager-scanfilter-i.md) | Describes the criteria for filtering scanning results can be set. |
| [ScanOptions](arkts-connectivity-bluetoothmanager-scanoptions-i.md) | Describes the parameters for scan. |
| [ScanResult](arkts-connectivity-bluetoothmanager-scanresult-i.md) | Describes the contents of the scan results. |
| [ServerResponse](arkts-connectivity-bluetoothmanager-serverresponse-i.md) | Describes the parameters of a response send by the server to a specified read or write request. |
| [ServiceData](arkts-connectivity-bluetoothmanager-servicedata-i.md) | Describes the service data. |
| [SppOption](arkts-connectivity-bluetoothmanager-sppoption-i.md) | Describes the spp parameters. |
| [StateChangeParam](arkts-connectivity-bluetoothmanager-statechangeparam-i.md) | Profile state change parameters. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HidHostProfile](arkts-connectivity-bluetoothmanager-hidhostprofile-i-sys.md) | Manager hid host profile. |
| [PanProfile](arkts-connectivity-bluetoothmanager-panprofile-i-sys.md) | Manager pan profile. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [BluetoothState](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md) | The enum of bluetooth state. |
| [BondState](arkts-connectivity-bluetoothmanager-bondstate-e.md) | The enum of bond state. |
| [MajorClass](arkts-connectivity-bluetoothmanager-majorclass-e.md) | The enum of major class of a bluetooth device. |
| [MajorMinorClass](arkts-connectivity-bluetoothmanager-majorminorclass-e.md) | The enum of major minor class of a bluetooth device. |
| [MatchMode](arkts-connectivity-bluetoothmanager-matchmode-e.md) | The enum of BLE match mode. |
| [PlayingState](arkts-connectivity-bluetoothmanager-playingstate-e.md) | The enum of a2dp playing state. |
| [ProfileConnectionState](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md) | The enum of profile connection state. |
| [ProfileId](arkts-connectivity-bluetoothmanager-profileid-e.md) | The enum of profile id. |
| [ScanDuty](arkts-connectivity-bluetoothmanager-scanduty-e.md) | The enum of scan duty. |
| [ScanMode](arkts-connectivity-bluetoothmanager-scanmode-e.md) | The enum of BR scan mode. |
| [SppType](arkts-connectivity-bluetoothmanager-spptype-e.md) | The enum of SPP type. |
