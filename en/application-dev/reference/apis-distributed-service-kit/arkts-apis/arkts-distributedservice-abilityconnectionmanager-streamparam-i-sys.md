# StreamParam (System API)

Streaming configuration parameters.

@interface StreamParam

**Since:** 18

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## bitrate

```TypeScript
bitrate?: number
```

This value indicates video bitrate, default 80(kbps). Only valid on the sender side.

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.

## colorSpaceConversionTarget

```TypeScript
colorSpaceConversionTarget?: colorSpaceManager.ColorSpace
```

The target color space for conversion. Currently, only BT709_LIMIT is supported. If the video format on the sender side is HDR and needs to be converted to SDR during transmission, this parameter should be set.

**Type:** [colorSpaceManager.ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Stream name, the receive end must be consistent with the transmit end.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.

## role

```TypeScript
role: StreamRole
```

Stream transmission role, which can be a receive stream or a transmit stream.

**Type:** [StreamRole](arkts-distributedservice-abilityconnectionmanager-streamrole-e-sys.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.
