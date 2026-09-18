# WifiDeviceConfig

Wi-Fi device configuration information. @typedef WifiDeviceConfig

**Since:** 12

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

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType?: DeviceAddressType
```

Wi-Fi bssid type.

**Type:** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## eapConfig

```TypeScript
eapConfig?: WifiEapConfig
```

EAP config info.

**Type:** [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md)

**Since:** 10

**System capability:** SystemCapability.Communication.WiFi.STA

## isHiddenSsid

```TypeScript
isHiddenSsid?: boolean
```

Hide SSID or not, false(default): not hide

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Communication.WiFi.STA

## preSharedKey

```TypeScript
preSharedKey: string
```

Wi-Fi key: maximum length is 64.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

Security type: reference definition of WifiSecurityType

**Type:** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## showNoInternetDialog

```TypeScript
showNoInternetDialog?: boolean
```

Whether to show a dialog when the first network probe detects no internet. If false, the default network is bound to cellular with no dialog shown. If true, will show a no-internet dialog prompts the user to select the default network binding. Default value: true.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

Wi-Fi SSID: the maximum length is 32.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.WiFi.STA

## wapiConfig

```TypeScript
wapiConfig?: WifiWapiConfig
```

WAPI config info.

**Type:** [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md)

**Since:** 12

**System capability:** SystemCapability.Communication.WiFi.STA
