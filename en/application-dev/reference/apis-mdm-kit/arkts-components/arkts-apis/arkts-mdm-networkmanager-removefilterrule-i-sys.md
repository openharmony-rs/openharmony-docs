# RemoveFilterRule (System API)

```TypeScript
interface RemoveFilterRule
```

Defines the network packet filtering rule to remove.

**Since:** 10

<!--Device-networkManager-interface RemoveFilterRule--><!--Device-networkManager-interface RemoveFilterRule-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## action

```TypeScript
action?: Action
```

Action to take, that is, receive or discard the data packets.

**Type:** [Action](arkts-mdm-networkmanager-action-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RemoveFilterRule-action?: Action--><!--Device-RemoveFilterRule-action?: Action-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## destAddr

```TypeScript
destAddr?: string
```

Destination IP address.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RemoveFilterRule-destAddr?: string--><!--Device-RemoveFilterRule-destAddr?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## destPort

```TypeScript
destPort?: string
```

Port of the destination IP address.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RemoveFilterRule-destPort?: string--><!--Device-RemoveFilterRule-destPort?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## direction

```TypeScript
direction: Direction
```

Direction chains to which the rule applies.

**Type:** [Direction](arkts-mdm-networkmanager-direction-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RemoveFilterRule-direction: Direction--><!--Device-RemoveFilterRule-direction: Direction-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## protocol

```TypeScript
protocol?: Protocol
```

Network protocol.

**Type:** [Protocol](arkts-mdm-networkmanager-protocol-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RemoveFilterRule-protocol?: Protocol--><!--Device-RemoveFilterRule-protocol?: Protocol-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## srcAddr

```TypeScript
srcAddr?: string
```

Source IP address.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RemoveFilterRule-srcAddr?: string--><!--Device-RemoveFilterRule-srcAddr?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## srcPort

```TypeScript
srcPort?: string
```

Port of the source IP address.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RemoveFilterRule-srcPort?: string--><!--Device-RemoveFilterRule-srcPort?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## uid

```TypeScript
uid?: string
```

UID of the application.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RemoveFilterRule-uid?: string--><!--Device-RemoveFilterRule-uid?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.
