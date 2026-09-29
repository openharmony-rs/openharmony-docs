# InterfaceConfig

```TypeScript
interface InterfaceConfig
```

Enumerates Ethernet network interface configurations. Only IPv4 is supported.

**Since:** 23

<!--Device-networkManager-interface InterfaceConfig--><!--Device-networkManager-interface InterfaceConfig-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## dnsServers

```TypeScript
dnsServers?: string
```

DNS service address. The value ranges from **0.0.0.0** to **255.255.255.255**. (This parameter is not required in DHCP mode.) Multiple addresses are separated by commas (,).

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InterfaceConfig-dnsServers?: string--><!--Device-InterfaceConfig-dnsServers?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## gateway

```TypeScript
gateway?: string
```

Gateway. The value ranges from **0.0.0.0** to **255.255.255.255**. (This parameter is not required in DHCP mode.)

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InterfaceConfig-gateway?: string--><!--Device-InterfaceConfig-gateway?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ipAddress

```TypeScript
ipAddress?: string
```

Static IP address. The value ranges from **0.0.0.0** to **255.255.255.255**. (This parameter is not required in DHCP mode.)

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InterfaceConfig-ipAddress?: string--><!--Device-InterfaceConfig-ipAddress?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ipSetMode

```TypeScript
ipSetMode: IpSetMode
```

Ethernet connection configuration mode.

**Type:** [IpSetMode](arkts-mdm-networkmanager-ipsetmode-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InterfaceConfig-ipSetMode: IpSetMode--><!--Device-InterfaceConfig-ipSetMode: IpSetMode-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## netMask

```TypeScript
netMask?: string
```

Subnet mask. The value ranges from **0.0.0.0** to **255.255.255.255**. (This parameter is not required in DHCP mode.)

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InterfaceConfig-netMask?: string--><!--Device-InterfaceConfig-netMask?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
