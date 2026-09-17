# @ohos.telephony.radio(网络搜索)

网络搜索模块提供管理网络搜索的一些基础功能，包括获取当前接入的CS域和PS域无线接入技术、获取网络状态、获取当前选网模式、获取注册网络所在国家的ISO国家码、获取主卡所在卡槽的索引号、获取指定SIM卡槽对应的注册网络信号强度信息列表、获取运营商名称，判断当前设备是否支持NR(New Radio)、判断主卡的Radio是否打开等。其中，CS域为电路交换域，PS为分组交换域。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getISOCountryCodeForNetwork](arkts-telephony-radio-getisocountrycodefornetwork-f.md) | 获取注册网络所在国家的ISO国家码。使用callback异步回调。 |
| [getISOCountryCodeForNetwork](arkts-telephony-radio-getisocountrycodefornetwork-f.md) | 获取注册网络所在国家的ISO国家码。使用Promise异步回调。 |
| [getISOCountryCodeForNetworkSync](arkts-telephony-radio-getisocountrycodefornetworksync-f.md) | 获取注册网络所在国家的ISO国家码。 |
| [getNetworkSelectionMode](arkts-telephony-radio-getnetworkselectionmode-f.md) | 获取当前选网模式。使用callback异步回调。 |
| [getNetworkSelectionMode](arkts-telephony-radio-getnetworkselectionmode-f.md) | 获取当前选网模式。使用Promise异步回调。 |
| [getNetworkState](arkts-telephony-radio-getnetworkstate-f.md) | 获取网络状态。使用callback异步回调。 |
| [getNetworkState](arkts-telephony-radio-getnetworkstate-f.md) | 获取网络状态。使用Promise异步回调。 |
| [getNetworkState](arkts-telephony-radio-getnetworkstate-f.md) | 获取网络状态。使用callback异步回调。 |
| [getOperatorName](arkts-telephony-radio-getoperatorname-f.md) | 获取运营商名称。使用callback异步回调。 |
| [getOperatorName](arkts-telephony-radio-getoperatorname-f.md) | 获取运营商名称。使用Promise异步回调。 |
| [getOperatorNameSync](arkts-telephony-radio-getoperatornamesync-f.md) | 获取运营商名称。 |
| [getPrimarySlotId](arkts-telephony-radio-getprimaryslotid-f.md) | 获取主卡所在卡槽的索引号。使用callback异步回调。 |
| [getPrimarySlotId](arkts-telephony-radio-getprimaryslotid-f.md) | 获取主卡所在卡槽的索引号。使用Promise异步回调。 |
| [getRadioTech](arkts-telephony-radio-getradiotech-f.md) | 获取当前接入的CS域和PS域无线接入技术。使用callback异步回调。其中，CS域为电路交换域，PS为分组交换域。 |
| [getRadioTech](arkts-telephony-radio-getradiotech-f.md) | 获取当前接入的CS域和PS域无线接入技术。使用Promise异步回调。其中，CS域为电路交换域，PS为分组交换域。 |
| [getRadioTechSync](arkts-telephony-radio-getradiotechsync-f.md) | 获取当前接入的CS域和PS域无线接入技术。CS域为电路交换域，PS为分组交换域。 |
| [getSignalInformation](arkts-telephony-radio-getsignalinformation-f.md) | 获取指定SIM卡槽对应的注册网络信号强度信息列表。使用callback异步回调。 |
| [getSignalInformation](arkts-telephony-radio-getsignalinformation-f.md) | 获取指定SIM卡槽对应的注册网络信号强度信息列表。使用Promise异步回调。 |
| [getSignalInformationSync](arkts-telephony-radio-getsignalinformationsync-f.md) | 获取指定SIM卡槽对应的注册网络信号强度信息列表。 |
| [isNrSupported](arkts-telephony-radio-isnrsupported-f.md) | 判断当前设备是否支持NR(New Radio)。 |
| [isNrSupported](arkts-telephony-radio-isnrsupported-f.md) | 判断当前设备是否支持NR(New Radio)。 |
| [isNRSupported](arkts-telephony-radio-isnrsupported-f.md) | 判断当前设备是否支持NR(New Radio)。 |
| [isNRSupported](arkts-telephony-radio-isnrsupported-f.md) | 判断当前设备是否支持NR(New Radio)。 |
| [isRadioOn](arkts-telephony-radio-isradioon-f.md) | 判断指定卡槽位的Radio是否打开。使用callback异步回调。 |
| [isRadioOn](arkts-telephony-radio-isradioon-f.md) | 判断Radio是否打开。使用Promise异步回调。 |
| [isRadioOn](arkts-telephony-radio-isradioon-f.md) | 判断主卡的Radio是否打开。使用callback异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [factoryReset](arkts-telephony-radio-factoryreset-f-sys.md) | Reset all network settings of telephony. |
| [getBasebandVersion](arkts-telephony-radio-getbasebandversion-f-sys.md) | Get the version of Baseband. |
| [getBasebandVersion](arkts-telephony-radio-getbasebandversion-f-sys.md) | Get the version of Baseband. |
| [getCellInformation](arkts-telephony-radio-getcellinformation-f-sys.md) | Get the current cell information. |
| [getCellInformation](arkts-telephony-radio-getcellinformation-f-sys.md) | Get the current cell information. |
| [getCellInformation](arkts-telephony-radio-getcellinformation-f-sys.md) | Get the current cell information. |
| [getIMEI](arkts-telephony-radio-getimei-f-sys.md) | Obtains the IMEI of a specified card slot of the device. |
| [getIMEI](arkts-telephony-radio-getimei-f-sys.md) | Obtains the IMEI of a specified card slot of the device. |
| [getIMEI](arkts-telephony-radio-getimei-f-sys.md) | Obtains the IMEI of a specified card slot of the device. |
| [getIMEISV](arkts-telephony-radio-getimeisv-f-sys.md) | Obtains the software version number of a specified card slot of the device. |
| [getImsRegInfo](arkts-telephony-radio-getimsreginfo-f-sys.md) | Get the IMS registration state info of specified IMS service type. |
| [getImsRegInfo](arkts-telephony-radio-getimsreginfo-f-sys.md) | Get the IMS registration state info of specified IMS service type. |
| [getMEID](arkts-telephony-radio-getmeid-f-sys.md) | Obtains the MEID of a specified card slot of the device. |
| [getMEID](arkts-telephony-radio-getmeid-f-sys.md) | Obtains the MEID of a specified card slot of the device. |
| [getMEID](arkts-telephony-radio-getmeid-f-sys.md) | Obtains the MEID of a specified card slot of the device. |
| [getNetworkCapability](arkts-telephony-radio-getnetworkcapability-f-sys.md) | Get the network capability state according to the specified capability type. |
| [getNetworkCapability](arkts-telephony-radio-getnetworkcapability-f-sys.md) | Get the network capability state according to the specified capability type. |
| [getNetworkSearchInformation](arkts-telephony-radio-getnetworksearchinformation-f-sys.md) | Get network search information. |
| [getNetworkSearchInformation](arkts-telephony-radio-getnetworksearchinformation-f-sys.md) | Get network search information. |
| [getNrOptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getNrOptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getNrOptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getNROptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getNROptionMode](arkts-telephony-radio-getnroptionmode-f-sys.md) | Get the option mode of NR. |
| [getPreferredNetwork](arkts-telephony-radio-getpreferrednetwork-f-sys.md) | Get the preferred network for the specified SIM card slot. |
| [getPreferredNetwork](arkts-telephony-radio-getpreferrednetwork-f-sys.md) | Get the preferred network for the specified SIM card slot. |
| [getUniqueDeviceId](arkts-telephony-radio-getuniquedeviceid-f-sys.md) | Obtains the unique device ID of a specified card slot of the device. |
| [getUniqueDeviceId](arkts-telephony-radio-getuniquedeviceid-f-sys.md) | Obtains the unique device ID of a specified card slot of the device. |
| [getUniqueDeviceId](arkts-telephony-radio-getuniquedeviceid-f-sys.md) | Obtains the unique device ID of a specified card slot of the device. |
| [isManualNetworkScanning](arkts-telephony-radio-ismanualnetworkscanning-f-sys.md) | 确定当前手动网络扫描是否正在进行 |
| [off](arkts-telephony-radio-off-f-sys.md#offimsregstatechange) | Unsubscribe from imsRegStateChange event. |
| [on](arkts-telephony-radio-on-f-sys.md#onimsregstatechange) | Called when the IMS registration state of specified IMS service type corresponding to a monitored `slotId` updates. |
| [sendUpdateCellLocationRequest](arkts-telephony-radio-sendupdatecelllocationrequest-f-sys.md) | Actively requests to update location information. |
| [sendUpdateCellLocationRequest](arkts-telephony-radio-sendupdatecelllocationrequest-f-sys.md) | Actively requests to update location information. |
| [sendUpdateCellLocationRequest](arkts-telephony-radio-sendupdatecelllocationrequest-f-sys.md) | Actively requests to update location information. |
| [setNetworkCapability](arkts-telephony-radio-setnetworkcapability-f-sys.md) | Set the type and state for the specified network capability. |
| [setNetworkCapability](arkts-telephony-radio-setnetworkcapability-f-sys.md) | Set the type and state for the specified network capability. |
| [setNetworkSelectionMode](arkts-telephony-radio-setnetworkselectionmode-f-sys.md) | Set the current network selection mode. |
| [setNetworkSelectionMode](arkts-telephony-radio-setnetworkselectionmode-f-sys.md) | Set the current network selection mode. |
| [setNROptionMode](arkts-telephony-radio-setnroptionmode-f-sys.md) | Set the NR option mode. |
| [setNROptionMode](arkts-telephony-radio-setnroptionmode-f-sys.md) | Set the NR option mode. |
| [setPreferredNetwork](arkts-telephony-radio-setpreferrednetwork-f-sys.md) | Set the preferred network for the specified SIM card slot. |
| [setPreferredNetwork](arkts-telephony-radio-setpreferrednetwork-f-sys.md) | Set the preferred network for the specified SIM card slot. |
| [setPrimarySlotId](arkts-telephony-radio-setprimaryslotid-f-sys.md) | Set the index number of the main SIM card slot. |
| [setPrimarySlotId](arkts-telephony-radio-setprimaryslotid-f-sys.md) | Set the index number of the main SIM card slot. |
| [startManualNetworkScan](arkts-telephony-radio-startmanualnetworkscan-f-sys.md) | 启动手动网络扫描，实时报告 |
| [stopManualNetworkScan](arkts-telephony-radio-stopmanualnetworkscan-f-sys.md) | 停止手动搜网 |
| [turnOffRadio](arkts-telephony-radio-turnoffradio-f-sys.md) | Turn off the radio service. |
| [turnOffRadio](arkts-telephony-radio-turnoffradio-f-sys.md) | Turn off the radio service. |
| [turnOffRadio](arkts-telephony-radio-turnoffradio-f-sys.md) | Turn off the radio service. |
| [turnOnRadio](arkts-telephony-radio-turnonradio-f-sys.md) | Turn on the radio service. |
| [turnOnRadio](arkts-telephony-radio-turnonradio-f-sys.md) | Turn on the radio service. |
| [turnOnRadio](arkts-telephony-radio-turnonradio-f-sys.md) | Turn on the radio service. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CellInformation](arkts-telephony-radio-cellinformation-i.md) | 小区信息。 |
| [NetworkRadioTech](arkts-telephony-radio-networkradiotech-i.md) | 网络中packet service (PS) 和 circuit service (CS) 无线接入技术。 |
| [NetworkState](arkts-telephony-radio-networkstate-i.md) | 网络注册状态。 |
| [SignalInformation](arkts-telephony-radio-signalinformation-i.md) | 网络信号强度信息对象。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CdmaCellInformation](arkts-telephony-radio-cdmacellinformation-i-sys.md) | Obtains CDMA cell information. |
| [CellInformation](arkts-telephony-radio-cellinformation-i-sys.md) | 小区信息。 |
| [GsmCellInformation](arkts-telephony-radio-gsmcellinformation-i-sys.md) | Obtains GSM cell information. |
| [ImsRegInfo](arkts-telephony-radio-imsreginfo-i-sys.md) | Indicates IMS registration information. |
| [LteCellInformation](arkts-telephony-radio-ltecellinformation-i-sys.md) | Obtains LTE cell information. |
| [NetworkInformation](arkts-telephony-radio-networkinformation-i-sys.md) | Obtains the network information. |
| [NetworkSearchRealTimeResult](arkts-telephony-radio-networksearchrealtimeresult-i-sys.md) | 表示手动网络扫描的结果 |
| [NetworkSearchResult](arkts-telephony-radio-networksearchresult-i-sys.md) | Obtains the network search results. |
| [NetworkSelectionModeOptions](arkts-telephony-radio-networkselectionmodeoptions-i-sys.md) | Obtains the network selection mode option. |
| [NrCellInformation](arkts-telephony-radio-nrcellinformation-i-sys.md) | Obtains NR cell information. |
| [TdscdmaCellInformation](arkts-telephony-radio-tdscdmacellinformation-i-sys.md) | Obtains TDSCDMA cell information. |
| [WcdmaCellInformation](arkts-telephony-radio-wcdmacellinformation-i-sys.md) | Obtains WCDMA cell information. |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NetworkSelectionMode](arkts-telephony-radio-networkselectionmode-e.md) | 选网模式。 |
| [NetworkType](arkts-telephony-radio-networktype-e.md) | 网络类型。 |
| [NsaState](arkts-telephony-radio-nsastate-e.md) | 非独立组网状态。 |
| [RadioTechnology](arkts-telephony-radio-radiotechnology-e.md) | 无线接入技术。 |
| [RegState](arkts-telephony-radio-regstate-e.md) | 网络注册状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ImsRegState](arkts-telephony-radio-imsregstate-e-sys.md) | Obtains IMS registration status. |
| [ImsRegTech](arkts-telephony-radio-imsregtech-e-sys.md) | Indicates IMS registration technology. |
| [ImsServiceType](arkts-telephony-radio-imsservicetype-e-sys.md) | Indicates the type of IMS service. |
| [NetworkCapabilityState](arkts-telephony-radio-networkcapabilitystate-e-sys.md) | Enum for network capability state. |
| [NetworkCapabilityType](arkts-telephony-radio-networkcapabilitytype-e-sys.md) | Enum for network capability type. |
| [NetworkInformationState](arkts-telephony-radio-networkinformationstate-e-sys.md) | Obtains network information status. |
| [NrOptionMode](arkts-telephony-radio-nroptionmode-e-sys.md) | Obtains the option mode of NR. |
| [NROptionMode](arkts-telephony-radio-nroptionmode-e-sys.md) | Obtains the option mode of NR. |
| [PreferredNetworkMode](arkts-telephony-radio-preferrednetworkmode-e-sys.md) | Indicates the preferred network. |
<!--DelEnd-->
