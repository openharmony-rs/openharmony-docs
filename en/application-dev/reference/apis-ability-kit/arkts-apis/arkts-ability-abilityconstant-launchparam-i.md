# LaunchParam

Describes the launch parameters, which mainly include the ability launch reasons and reasons for the last exit. The parameter values are automatically passed in by the system when the ability is launched. You do not need to change the values.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { AbilityConstant } from '@kit.AbilityKit';
```

## lastExitDetailInfo

```TypeScript
lastExitDetailInfo?: LastExitDetailInfo
```

Key runtime information for the last exit of the ability (including process ID, exit timestamp, and RSS memory value).

**Type:** [LastExitDetailInfo](arkts-ability-abilityconstant-lastexitdetailinfo-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## lastExitMessage

```TypeScript
lastExitMessage: string
```

Detailed message that describes the reason for the last exit of the ability.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## lastExitReason

```TypeScript
lastExitReason: LastExitReason
```

An enumerated value indicating the reason for the last exit of the ability.

**Type:** [LastExitReason](arkts-ability-abilityconstant-lastexitreason-e.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## launchReason

```TypeScript
launchReason: LaunchReason
```

An enumerated value indicating the reason for ability launch (for example, recovery from a fault, intent invocation, or atomic service sharing). For details, see [LaunchReason](arkts-ability-abilityconstant-launchreason-e.md).

**Type:** [LaunchReason](arkts-ability-abilityconstant-launchreason-e.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## launchReasonMessage

```TypeScript
launchReasonMessage?: string
```

Detailed message that describes the reason for the ability launch.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## launchUptime

```TypeScript
launchUptime?: number
```

System uptime (the time elapsed since the system booted up) when the UIAbility starts, in milliseconds.

**Constraints**:

This feature takes effect only when the UIAbility is started. For other types of abilities (for example, UIExtensionAbility), the obtained start time is the default value **0**.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## launchUTCTime

```TypeScript
launchUTCTime?: number
```

UTC timestamp when the UIAbility starts, in milliseconds.

This API can be used in atomic services since API version 23.

**Constraints**:

This feature takes effect only when the UIAbility is started. For other types of abilities (for example, UIExtensionAbility), the obtained start time is the default value **0**.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
