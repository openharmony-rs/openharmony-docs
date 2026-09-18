# RangingStateChangeInfo

Describes the ranging state change information.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## cause

```TypeScript
cause: RangingStoppedCause
```

Cause of ranging stop.

**Type:** [RangingStoppedCause](arkts-connectivity-ranging-rangingstoppedcause-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## deviceId

```TypeScript
deviceId?: string
```

Address of the ranging device.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## handle

```TypeScript
handle?: number
```

Indicates the handle number of ranging monitoring. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## state

```TypeScript
state: RangingState
```

Ranging state.

**Type:** [RangingState](arkts-connectivity-ranging-rangingstate-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core
