# IpSetMode

Enumerates Ethernet connection configuration modes.

**Since:** 23

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## STATIC

```TypeScript
STATIC = 0
```

Static configuration of network information for Ethernet connection. When this mode is set, the IP address, subnet mask, default gateway, and DNS server need to be configured synchronously.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DHCP

```TypeScript
DHCP = 1
```

Dynamic configuration of network information for Ethernet connection. When this mode is set, the DHCP server in the network automatically assigns the IP address and other related information.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
