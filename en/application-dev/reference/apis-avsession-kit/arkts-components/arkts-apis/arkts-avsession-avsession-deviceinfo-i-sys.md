# DeviceInfo

Device Information Definition

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## authenticationStatus

```TypeScript
authenticationStatus?: number
```

Define different authentication status. 0: Device not authenticated. 1: Device already authenticated.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## hiPlayDeviceInfo

```TypeScript
hiPlayDeviceInfo?: HiPlayDeviceInfo
```

HiPlayDeviceInfo is used to obtain device-specific information for HiPlay. transmit info during casting.

**Type:** [HiPlayDeviceInfo](arkts-avsession-avsession-hiplaydeviceinfo-i-sys.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## ipAddress

```TypeScript
ipAddress?: string
```

device ip address if available.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## isLegacy

```TypeScript
isLegacy?: boolean
```

Indicates the current device is legacy or not.

**Type:** boolean

**Since:** 13

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## mediumTypes

```TypeScript
mediumTypes?: number
```

Medium types used to discover devices. 1: BLE 2: COAP

**Type:** number

**Since:** 13

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## networkId

```TypeScript
networkId?: string
```

Network id.

**Type:** string

**Since:** 13

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## providerId

```TypeScript
providerId?: number
```

device provider which supplies the route capability.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.
