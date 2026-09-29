# WifiDeviceConfig

```TypeScript
interface WifiDeviceConfig
```

Wi-Fi device configuration information. @typedef WifiDeviceConfig

**Since:** 12

<!--Device-wifiManager-interface WifiDeviceConfig--><!--Device-wifiManager-interface WifiDeviceConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## bssid

```TypeScript
bssid?: string
```

Wi-Fi bssid(MAC): the length is 6.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiDeviceConfig-bssid?: string--><!--Device-WifiDeviceConfig-bssid?: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType?: DeviceAddressType
```

Wi-Fi bssid type.

**Type:** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiDeviceConfig-bssidType?: DeviceAddressType--><!--Device-WifiDeviceConfig-bssidType?: DeviceAddressType-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## eapConfig

```TypeScript
eapConfig?: WifiEapConfig
```

EAP config info.

**Type:** [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md)

**Since:** 10

<!--Device-WifiDeviceConfig-eapConfig?: WifiEapConfig--><!--Device-WifiDeviceConfig-eapConfig?: WifiEapConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## isHiddenSsid

```TypeScript
isHiddenSsid?: boolean
```

Hide SSID or not, false(default): not hide

**Type:** boolean

**Since:** 9

<!--Device-WifiDeviceConfig-isHiddenSsid?: boolean--><!--Device-WifiDeviceConfig-isHiddenSsid?: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## preSharedKey

```TypeScript
preSharedKey: string
```

Wi-Fi key: maximum length is 64.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiDeviceConfig-preSharedKey: string--><!--Device-WifiDeviceConfig-preSharedKey: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

Security type: reference definition of WifiSecurityType

**Type:** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiDeviceConfig-securityType: WifiSecurityType--><!--Device-WifiDeviceConfig-securityType: WifiSecurityType-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## showNoInternetDialog

```TypeScript
showNoInternetDialog?: boolean
```

Whether to show a dialog when the first network probe detects no internet. If false, the default network is bound to cellular with no dialog shown. If true, will show a no-internet dialog prompts the user to select the default network binding. Default value: true.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WifiDeviceConfig-showNoInternetDialog?: boolean--><!--Device-WifiDeviceConfig-showNoInternetDialog?: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

Wi-Fi SSID: the maximum length is 32.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-WifiDeviceConfig-ssid: string--><!--Device-WifiDeviceConfig-ssid: string-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

## wapiConfig

```TypeScript
wapiConfig?: WifiWapiConfig
```

WAPI config info.

**Type:** [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md)

**Since:** 12

<!--Device-WifiDeviceConfig-wapiConfig?: WifiWapiConfig--><!--Device-WifiDeviceConfig-wapiConfig?: WifiWapiConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.STA
