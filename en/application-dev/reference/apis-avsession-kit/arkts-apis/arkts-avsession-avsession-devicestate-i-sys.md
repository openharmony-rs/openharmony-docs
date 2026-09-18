# DeviceState (System API)

Device state used to describe states including discovery, authentication and other scenes.

**Since:** 20

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## deviceId

```TypeScript
readonly deviceId: string
```

Unique device descriptor.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## deviceState

```TypeScript
readonly deviceState: number
```

Device connection state.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## radarErrorCode

```TypeScript
readonly radarErrorCode: number
```

System radar error code returned by cast+services.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

## reasonCode

```TypeScript
readonly reasonCode: number
```

Reason for connection failure, for example, user cancellation and timeout.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.
