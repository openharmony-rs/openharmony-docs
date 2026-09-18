# FirewallRule

Represents a firewall rule.

In API version 21 and earlier versions, only IPv4 is supported. IPv4 and IPv6 are supported since API version 22.

[LogType](arkts-mdm-networkmanager-logtype-e.md) is supported since API version 23.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## action

```TypeScript
action?: Action
```

Action to take, that is, receive or discard the data packets.

This parameter is mandatory when a firewall filtering rule is added.

This parameter is optional when a firewall is removed. If this parameter is left empty, all [Action](arkts-mdm-networkmanager-action-e.md) chains are cleared, and **srcAddr**, **destAddr**, **srcPort**, **destPort**, and **appUid** must be also left empty.

**Type:** [Action](arkts-mdm-networkmanager-action-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## appUid

```TypeScript
appUid?: string
```

UID of the application.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## destAddr

```TypeScript
destAddr?: string
```

Destination IP address. An IP address segment, for example, **192.168.0.0/22** or **192.168.1.100-192.168.1.200** is supported.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## destPort

```TypeScript
destPort?: string
```

Destination port.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## direction

```TypeScript
direction?: Direction
```

Direction chains to which the rule applies.

This parameter is mandatory when a firewall filtering rule is added.

This parameter is optional when a firewall is removed. If this parameter is left empty, all [Direction](arkts-mdm-networkmanager-direction-e.md) chains are cleared, and **srcAddr**, **destAddr**, **srcPort**, **destPort**, and **appUid** must be also left empty.

**Type:** [Direction](arkts-mdm-networkmanager-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## family

```TypeScript
family?: number
```

IP protocol version. The value can be **1** (IPv4) or **2** (IPv6).

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## logType

```TypeScript
logType?: LogType
```

Log type. Currently, only **NFLOG** is supported. This parameter applies only to PCs/2-in-1 devices.

When adding a firewall filter rule, this parameter is optional. If configured, it only takes effect when data packets are dropped or rejected.

When removing firewall filter rules, this parameter is optional if a chain is cleared. The clearing of the entire chain is not affected. When removing a single rule, the value of this parameter must be the same as that of the rule. Otherwise, the filter rule may have been removed, but logs are still recorded. When removing the same filter rule, you must remove the rule in the sequence in which the rule is added.

When obtaining firewall filter rules, the **logType** field can be obtained only when logs take effect.

**Type:** [LogType](arkts-mdm-networkmanager-logtype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## protocol

```TypeScript
protocol?: Protocol
```

Network protocol. If the value is **ALL** or **ICMP**, the settings of **srcPort** and **destPort** are invalid.

**Type:** [Protocol](arkts-mdm-networkmanager-protocol-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## srcAddr

```TypeScript
srcAddr?: string
```

Source IP address. An IP address segment, for example, **192.168.0.0/22** or **192.168.1.100-192.168.1.200** is supported.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## srcPort

```TypeScript
srcPort?: string
```

Source port.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
