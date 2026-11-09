# DevicePowerSubMode

```TypeScript
export enum DevicePowerSubMode
```

电源模式子模式枚举。

枚举值由电源模式值和序号组成：  
- 前缀：子模式所属的电源模式枚举值。例如 603001 中的 603 表示该子模式属于[MODE_EXTREME_POWER_SAVE](arkts-basicservices-power-devicepowermode-e.md)。  
- 后缀：同一电源模式下的子模式序号，从 001 开始递增。

SUB_MODE_INVALID（-1）不遵循此规则，表示当前电源模式不支持子模式。

**起始版本：** 26.1.0

<!--Device-power-export enum DevicePowerSubMode--><!--Device-power-export enum DevicePowerSubMode-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## SUB_MODE_EMERGENCY

```TypeScript
SUB_MODE_EMERGENCY = 603002
```

应急子模式。适用于电源模式[MODE_EXTREME_POWER_SAVE](arkts-basicservices-power-devicepowermode-e.md)。此值为 MODE_EXTREME_POWER_SAVE 的默认子模式。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DevicePowerSubMode-SUB_MODE_EMERGENCY = 603002--><!--Device-DevicePowerSubMode-SUB_MODE_EMERGENCY = 603002-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## SUB_MODE_INVALID

```TypeScript
SUB_MODE_INVALID = -1
```

非法子模式值。当前电源模式不支持子模式时使用此值。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DevicePowerSubMode-SUB_MODE_INVALID = -1--><!--Device-DevicePowerSubMode-SUB_MODE_INVALID = -1-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## SUB_MODE_SUPER_POWER_SAVE

```TypeScript
SUB_MODE_SUPER_POWER_SAVE = 603001
```

超级省电子模式。适用于电源模式 [MODE_EXTREME_POWER_SAVE](arkts-basicservices-power-devicepowermode-e.md)。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DevicePowerSubMode-SUB_MODE_SUPER_POWER_SAVE = 603001--><!--Device-DevicePowerSubMode-SUB_MODE_SUPER_POWER_SAVE = 603001-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core
