# SteadyStandingStatus

```TypeScript
export enum SteadyStandingStatus
```

Defines the steady standing state (that is, stand mode).

The device enters the stand mode when it is stationary and the angle between the screen and the horizontal plane is between 45 and 135 degrees. A foldable phone must be in the folded state or the fully unfolded state. The system detects the motion state and angle changes of the device through sensors to determine whether the device meets the stand mode conditions.

**Since:** 18

<!--Device-deviceStatus-export enum SteadyStandingStatus--><!--Device-deviceStatus-export enum SteadyStandingStatus-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

## STATUS_ENTER

```TypeScript
STATUS_ENTER = 1
```

Entry to the stand mode.

**Since:** 18

<!--Device-SteadyStandingStatus-STATUS_ENTER = 1--><!--Device-SteadyStandingStatus-STATUS_ENTER = 1-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

## STATUS_EXIT

```TypeScript
STATUS_EXIT = 0
```

Exit of the stand mode.

**Since:** 18

<!--Device-SteadyStandingStatus-STATUS_EXIT = 0--><!--Device-SteadyStandingStatus-STATUS_EXIT = 0-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus
