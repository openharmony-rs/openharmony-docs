# AddFilterRule (System API)

Defines the network packet filtering rule to add.

**Since:** 10

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## action

```TypeScript
action: Action
```

Action to take, that is, receive or discard the data packets.

**Type:** [Action](arkts-mdm-networkmanager-action-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

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

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## method

```TypeScript
method: AddMethod
```

Method used to add the data packets.

**Type:** [AddMethod](arkts-mdm-networkmanager-addmethod-e-sys.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

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

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## ruleNo

```TypeScript
ruleNo?: number
```

Sequence number of the rule.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

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

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.
