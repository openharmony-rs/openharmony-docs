# IpProfile

```TypeScript
interface IpProfile
```

Represents IP configuration information.

**Since:** 12

<!--Device-wifiManager-interface IpProfile--><!--Device-wifiManager-interface IpProfile-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## dnsServers

```TypeScript
dnsServers: number[]
```

DNS server. The array can contain a maximum of two addresses: the primary DNS server and the secondary DNS server. The address ranges from 0.0.0.0 to 255.255.255.255.

**Type:** number[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-IpProfile-dnsServers: number[]--><!--Device-IpProfile-dnsServers: number[]-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## domains

```TypeScript
domains: Array<string>
```

Domain information.

**Type:** Array&lt;string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-IpProfile-domains: Array<string>--><!--Device-IpProfile-domains: Array<string>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## gateway

```TypeScript
gateway: number
```

Default gateway, represented in decimal format, usually the IP address of the router. The address ranges from 0.0.0.0 to 255.255.255.255.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-IpProfile-gateway: number--><!--Device-IpProfile-gateway: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ipAddress

```TypeScript
ipAddress: number
```

IP address, represented in decimal format. For example, the standard dotted decimal notation **192.168.1.1** corresponds to the decimal value **3232235777**. The address ranges from 0.0.0.0 to 255.255.255.255.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-IpProfile-ipAddress: number--><!--Device-IpProfile-ipAddress: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## prefixLength

```TypeScript
prefixLength: number
```

Subnet mask. The address ranges from 0.0.0.0 to 255.255.255.255.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-IpProfile-prefixLength: number--><!--Device-IpProfile-prefixLength: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
