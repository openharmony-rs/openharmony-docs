# FactoryResetInfo (System API)

Describes the information of restoring factory settings.

**Since:** 26.0.0

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## duration

```TypeScript
duration: number
```

Duration required for restoring factory settings, in minutes. The value range is [0, +∞]. An exception is thrown if the value is out of range.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
