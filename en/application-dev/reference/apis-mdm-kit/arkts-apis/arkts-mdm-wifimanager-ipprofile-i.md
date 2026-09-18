# IpProfile

Represents IP configuration information.

**Since:** 12

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

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## domains

```TypeScript
domains: Array<string>
```

Domain information.

**Type:** Array&lt;string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## gateway

```TypeScript
gateway: number
```

Default gateway, represented in decimal format, usually the IP address of the router. The address ranges from 0.0.0.0 to 255.255.255.255.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ipAddress

```TypeScript
ipAddress: number
```

IP address, represented in decimal format. For example, the standard dotted decimal notation **192.168.1.1** corresponds to the decimal value **3232235777**. The address ranges from 0.0.0.0 to 255.255.255.255.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## prefixLength

```TypeScript
prefixLength: number
```

Subnet mask. The address ranges from 0.0.0.0 to 255.255.255.255.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
