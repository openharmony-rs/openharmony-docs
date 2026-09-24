# ExecuteResult

```TypeScript
interface ExecuteResult
```

Enumerates the return results of intent execution.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## code

```TypeScript
code: number
```

Error code returned by the intent execution, defined by the developer.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## flags

```TypeScript
flags?: number
```

Permissions to be granted to the system entry point for the URI list returned by the intent execution.

**NOTE:** 

This parameter supports only FLAG_AUTH_READ_URI_PERMISSION, FLAG_AUTH_WRITE_URI_PERMISSION, and FLAG_AUTH_READ_URI_PERMISSION|FLAG_AUTH_WRITE_URI_PERMISSION. For details about the permissions, see [Flags](arkts-ability-wantconstant-flags-e.md).

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## result

```TypeScript
result?: Record<string, Object>
```

Result data returned by the intent execution, typically containing information to be passed back to the system entry point.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uris

```TypeScript
uris?: Array<string>
```

List of URIs returned by the intent execution. This field must be used together with the **flags** field to grant the corresponding permissions for the URI list to the system entry point.

**Type:** Array&lt;string&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
