# WifiProfile

Represents the Wi-Fi configuration information.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## bssid

```TypeScript
bssid?: string
```

MAC address of the Wi-Fi hotspot, with a length of 6 bytes. For example, **00:11:22:33:44:55**. To obtain the MAC address, enable **Enable Wi-Fi verbose logging** under **Settings**  
> **System & updates**
> **Developer options** first, and then go to the WLAN list to check the MAC address. If a Wi-Fi network has multiple MAC addresses, all of them must be added here.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## creatorUid

```TypeScript
creatorUid?: number
```

ID of the user who creates the network. The default value is **-1**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## disableReason

```TypeScript
disableReason?: number
```

Disabling reason. The default value is **0**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## eapProfile

```TypeScript
eapProfile?: WifiEapProfile
```

Extensible Authentication Protocol (EAP) configuration. This field is mandatory only when **securityType** is set to **WIFI_SEC_TYPE_EAP**.

**Type:** [WifiEapProfile](arkts-mdm-wifimanager-wifieapprofile-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ipType

```TypeScript
ipType?: IpType
```

IP address type. The default value is **DHCP**.

**Type:** [IpType](arkts-mdm-wifimanager-iptype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## isHiddenSsid

```TypeScript
isHiddenSsid?: boolean
```

Whether the network is hidden. The value **true** indicates yes, and the value **false** indicates no. The default value is **false**.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## netId

```TypeScript
netId?: number
```

Allocated network ID. The default value is **-1**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## preSharedKey

```TypeScript
preSharedKey: string
```

Key of the hotspot, which is used for Wi-Fi connection authentication. The maximum length is 64 bytes.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## randomMacAddr

```TypeScript
randomMacAddr?: string
```

MAC address. This field is mandatory when **randomMacType** is set to device MAC address.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## randomMacType

```TypeScript
randomMacType?: number
```

Random MAC. The value **0** indicates random MAC address, and the value **1** indicates device MAC address. The default value is **0**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## securityType

```TypeScript
securityType: WifiSecurityType
```

Security type.

**Type:** [WifiSecurityType](arkts-mdm-wifimanager-wifisecuritytype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ssid

```TypeScript
ssid: string
```

Wi-Fi hotspot name. The maximum length is 32 bytes, and the encoding format is UTF-8.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## staticIp

```TypeScript
staticIp?: IpProfile
```

Static IP address information. This field is mandatory when **ipType** is set to **STATIC**.

**Type:** [IpProfile](arkts-mdm-wifimanager-ipprofile-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
