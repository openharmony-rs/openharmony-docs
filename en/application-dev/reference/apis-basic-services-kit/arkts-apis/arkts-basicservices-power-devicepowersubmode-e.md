# DevicePowerSubMode

```TypeScript
export enum DevicePowerSubMode
```

Enumerates power sub-modes.

The enum value is composed of the power mode value and a sequence number:  
- Prefix: the power mode value that this sub-mode belongs to. For example,  
603 in 603001 indicates this sub-mode belongs to [MODE_EXTREME_POWER_SAVE](arkts-basicservices-power-devicepowermode-e.md).  
- Suffix: the sequence number within the power mode, starting from 001.

SUB_MODE_INVALID (-1) does not follow this rule and indicates that the current power mode does not support sub-mode.

**Since:** 26.1.0

<!--Device-power-export enum DevicePowerSubMode--><!--Device-power-export enum DevicePowerSubMode-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## SUB_MODE_EMERGENCY

```TypeScript
SUB_MODE_EMERGENCY = 603002
```

Emergency sub-mode. Applies to [MODE_EXTREME_POWER_SAVE](arkts-basicservices-power-devicepowermode-e.md). This is the default sub-mode for MODE_EXTREME_POWER_SAVE.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DevicePowerSubMode-SUB_MODE_EMERGENCY = 603002--><!--Device-DevicePowerSubMode-SUB_MODE_EMERGENCY = 603002-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## SUB_MODE_INVALID

```TypeScript
SUB_MODE_INVALID = -1
```

Invalid sub-mode. Used when the power mode does not support sub-mode.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DevicePowerSubMode-SUB_MODE_INVALID = -1--><!--Device-DevicePowerSubMode-SUB_MODE_INVALID = -1-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## SUB_MODE_SUPER_POWER_SAVE

```TypeScript
SUB_MODE_SUPER_POWER_SAVE = 603001
```

Super power save sub-mode. Applies to [MODE_EXTREME_POWER_SAVE](arkts-basicservices-power-devicepowermode-e.md).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DevicePowerSubMode-SUB_MODE_SUPER_POWER_SAVE = 603001--><!--Device-DevicePowerSubMode-SUB_MODE_SUPER_POWER_SAVE = 603001-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core
