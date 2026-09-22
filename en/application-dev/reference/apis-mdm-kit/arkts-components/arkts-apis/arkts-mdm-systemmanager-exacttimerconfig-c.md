# ExactTimerConfig

```TypeScript
class ExactTimerConfig
```

Defines the initialization configuration for an exact timer.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## callback

```TypeScript
callback(): void
```

Callback to be executed when the timer expires.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## interval

```TypeScript
interval: number
```

Interval between two consecutive timer triggers. For a repeating timer, the minimum value of **interval** is 1000 ms and the maximum value is 86400000 ms. For a one-shot timer, the value is **0**. Unit: milliseconds.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

Timer name. The maximum length is 64 and cannot be empty.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## repeat

```TypeScript
repeat: boolean
```

Whether the timer is a repeating timer. The value **true** means that the timer is a repeating timer, and **false** means that the timer is a one-shot timer.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
