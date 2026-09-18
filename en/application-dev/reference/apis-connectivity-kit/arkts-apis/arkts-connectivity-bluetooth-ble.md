# @ohos.bluetooth.ble

Provides methods to operate or manage Bluetooth.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createBleScanner](arkts-connectivity-ble-createblescanner-f.md) | Create a ble scanner instance. Each ble scanner instance can be independently started or stopped. |
| [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) | create a Gatt client device instance. |
| [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) | create a Gatt client device instance with custom setting. |
| [createGattServer](arkts-connectivity-ble-creategattserver-f.md) | create a Gatt server instance. |
| [disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md) | Disable the advertising with a specific ID temporarily. |
| [disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md) | Disable the advertising with a specific ID temporarily. |
| [enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md) | Enable the advertising with a specific ID temporarily. |
| [enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md) | Enable the advertising with a specific ID temporarily. |
| [getConnectedBLEDevices](arkts-connectivity-ble-getconnectedbledevices-f.md) | Obtains the list of devices in the connected status. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual. |
| [getConnectedBLEDevices](arkts-connectivity-ble-getconnectedbledevices-f.md) | Obtains the list of devices in the connected status. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual. |
| [off](arkts-connectivity-ble-off-f.md#offadvertisingstatechange) | Unsubscribe from advertising state change event. |
| [off](arkts-connectivity-ble-off-f.md#offbledevicefind) | Unsubscribe BLE scan result. |
| [on](arkts-connectivity-ble-on-f.md#onadvertisingstatechange) | Subscribing to advertising state change event. |
| [on](arkts-connectivity-ble-on-f.md#onbledevicefind) | Subscribe BLE scan result. On API 26.0.0 and above, if the application has ohos.permission.GET_BLUETOOTH_PEERS_MAC, the type of the peer device address is real. Otherwise, the type of the peer device address is virtual. |
| [startAdvertising](arkts-connectivity-ble-startadvertising-f.md) | Starts BLE advertising. |
| [startAdvertising](arkts-connectivity-ble-startadvertising-f.md) | Starts BLE advertising. The API returns a advertising ID. The ID can be used to temporarily enable or disable this advertising using the API [enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md) or [disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md). To completely stop the advertising corresponding to the ID, invoke the API [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) with ID. |
| [startAdvertising](arkts-connectivity-ble-startadvertising-f.md) | Starts BLE advertising. The API returns a advertising ID. The ID can be used to temporarily enable or disable this advertising using the API [enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md) or [disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md). To completely stop the advertising corresponding to the ID, invoke the API [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) with ID. |
| [startBLEScan](arkts-connectivity-ble-startblescan-f.md) | Starts scanning for specified BLE devices with filters. |
| [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) | Stops BLE advertising. |
| [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) | Stops BLE advertising. Completely stop the advertising corresponding to the ID. |
| [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) | Stops BLE advertising. Completely stop the advertising corresponding to the ID. |
| [stopBLEScan](arkts-connectivity-ble-stopblescan-f.md) | Stops BLE scanning. |

### Interfaces

| Name | Description |
| --- | --- |
| [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md) | Describes the advertising data. |
| [AdvertiseSetting](arkts-connectivity-ble-advertisesetting-i.md) | Describes the settings for BLE advertising. |
| [AdvertisingDisableParams](arkts-connectivity-ble-advertisingdisableparams-i.md) | Parameter for dynamically disable advertising. |
| [AdvertisingEnableParams](arkts-connectivity-ble-advertisingenableparams-i.md) | Parameter for dynamically enable advertising. |
| [AdvertisingParams](arkts-connectivity-ble-advertisingparams-i.md) | Describes the advertising parameters. |
| [AdvertisingStateChangeInfo](arkts-connectivity-ble-advertisingstatechangeinfo-i.md) | Advertising state change information. |
| [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | Describes the Gatt characteristic. |
| [BLEConnectionChangeState](arkts-connectivity-ble-bleconnectionchangestate-i.md) | Describes the Gatt profile connection state. |
| [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md) | Describes the Gatt descriptor. |
| [BleScanner](arkts-connectivity-ble-blescanner-i.md) | Manages the ble scanner. Before calling a ble scanner method, you must use [createBleScanner](arkts-connectivity-ble-createblescanner-f.md) to create an BleScanner instance. |
| [CharacteristicReadRequest](arkts-connectivity-ble-characteristicreadrequest-i.md) | Describes the parameters of the Gatt client's characteristic read request. |
| [CharacteristicWriteRequest](arkts-connectivity-ble-characteristicwriterequest-i.md) | Describes the parameters of the of the Gatt client's characteristic write request. |
| [DescriptorReadRequest](arkts-connectivity-ble-descriptorreadrequest-i.md) | Describes the parameters of the Gatt client's descriptor read request. |
| [DescriptorWriteRequest](arkts-connectivity-ble-descriptorwriterequest-i.md) | Describes the parameters of the Gatt client's characteristic write request. |
| [GattClientDevice](arkts-connectivity-ble-gattclientdevice-i.md) | Manages GATT client. Before calling an Gatt client method, you must use [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) to create an GattClientDevice instance. |
| [GattPermissions](arkts-connectivity-ble-gattpermissions-i.md) | Describes the permission of a att attribute item. |
| [GattProperties](arkts-connectivity-ble-gattproperties-i.md) | Describes the properties of a gatt characteristic. |
| [GattServer](arkts-connectivity-ble-gattserver-i.md) | Manages GATT server. Before calling an Gatt server method, you must use [createGattServer](arkts-connectivity-ble-creategattserver-f.md) to create an GattServer instance. |
| [GattService](arkts-connectivity-ble-gattservice-i.md) | Describes the Gatt service. |
| [GattSetting](arkts-connectivity-ble-gattsetting-i.md) | Describes the setting for Gatt Connection. |
| [ManufactureData](arkts-connectivity-ble-manufacturedata-i.md) | Describes the manufacturer data. |
| [NotifyCharacteristic](arkts-connectivity-ble-notifycharacteristic-i.md) | Describes the value of the indication or notification sent by the Gatt server. |
| [PhyValue](arkts-connectivity-ble-phyvalue-i.md) | Describes the parameters of the Ble phy. |
| [ScanFilter](arkts-connectivity-ble-scanfilter-i.md) | Describes the criteria for filtering scanning results can be set. |
| [ScanOptions](arkts-connectivity-ble-scanoptions-i.md) | Describes the parameters for scan. |
| [ScanReport](arkts-connectivity-ble-scanreport-i.md) | Describes the contents of the scan report. |
| [ScanResult](arkts-connectivity-ble-scanresult-i.md) | Describes the contents of the scan results. |
| [ServerResponse](arkts-connectivity-ble-serverresponse-i.md) | Describes the parameters of a response send by the server to a specified read or write request. |
| [ServiceData](arkts-connectivity-ble-servicedata-i.md) | Describes the service data. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [GattClientDevice](arkts-connectivity-ble-gattclientdevice-i-sys.md) | Manages GATT client. Before calling an Gatt client method, you must use [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) to create an GattClientDevice instance. |
| [GattRspContext](arkts-connectivity-ble-gattrspcontext-i-sys.md) | Describe the context of GATT responses. |
| [ScanEnhanceMode](arkts-connectivity-ble-scanenhancemode-i-sys.md) | Describes the configuration of scan enhance mode. |
| [ScanFilter](arkts-connectivity-ble-scanfilter-i-sys.md) | Describes the criteria for filtering scanning results can be set. |
| [ScanOptions](arkts-connectivity-ble-scanoptions-i-sys.md) | Describes the parameters for scan. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AdvertisingState](arkts-connectivity-ble-advertisingstate-e.md) | The enum of BLE advertising state. |
| [BlePhy](arkts-connectivity-ble-blephy-e.md) | Phy type for advertising or connection. |
| [BleProfile](arkts-connectivity-ble-bleprofile-e.md) | The Profile of the BLE protocol. |
| [CodedPhyMode](arkts-connectivity-ble-codedphymode-e.md) | Coded phy mode for advertising or connection. |
| [ConnectionParam](arkts-connectivity-ble-connectionparam-e.md) | GATT connection parameters. |
| [GattDisconnectReason](arkts-connectivity-ble-gattdisconnectreason-e.md) | The enum of gatt disconnection reasons. |
| [GattWriteType](arkts-connectivity-ble-gattwritetype-e.md) | The enum of gatt characteristic write type |
| [MatchMode](arkts-connectivity-ble-matchmode-e.md) | The enum of BLE match mode. |
| [PhyType](arkts-connectivity-ble-phytype-e.md) | Phy type used during scan. |
| [ScanDuty](arkts-connectivity-ble-scanduty-e.md) | The enum of scan duty. |
| [ScanReportMode](arkts-connectivity-ble-scanreportmode-e.md) | Report mode used during scan. |
| [ScanReportType](arkts-connectivity-ble-scanreporttype-e.md) | Scan report type used during scan. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [EnhanceMode](arkts-connectivity-ble-enhancemode-e-sys.md) | Scan enhance mode. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [BluetoothAddress](arkts-connectivity-ble-bluetoothaddress-t.md) | Bluetooth device address. |
| [BluetoothTransport](arkts-connectivity-ble-bluetoothtransport-t.md) | Indicate the transport of a remote device. |
| [ProfileConnectionState](arkts-connectivity-ble-profileconnectionstate-t.md) | Indicate the profile connection state. |
