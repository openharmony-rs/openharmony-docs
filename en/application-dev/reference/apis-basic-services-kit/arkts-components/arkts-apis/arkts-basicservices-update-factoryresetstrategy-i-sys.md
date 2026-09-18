# FactoryResetStrategy (System API)

Represents the factory reset strategy, which contains the **scope** (reset scope) and **strategy** (reset strategy description) fields.

**Since:** 26.0.0

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## scope

```TypeScript
scope: FactoryResetScope
```

Reset scope. The value **DATA** indicates that only data in the user partition is cleared; **DATA_AND_OS** indicates that data in both the user partition and OS partition is cleared.

**Type:** [FactoryResetScope](arkts-basicservices-update-factoryresetscope-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## strategy

```TypeScript
strategy: string
```

Reset strategy, which specifies the specific strategy for the reset operation. The value is a string of 0 to 64 characters. The value can contain letters, digits, underscores (_), hyphens (-), and spaces. An exception is thrown if the value is out of range or contains invalid characters. This parameter describes the reset operation. For example, **quick erase** indicates fast data erasure, and **deep erase** indicates deep erasure.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
