# ExecuteResult

```TypeScript
interface ExecuteResult
```

Defines the result of ArkTS script execution.

**Since:** 26.0.0

<!--Device-scriptManager-interface ExecuteResult--><!--Device-scriptManager-interface ExecuteResult-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { scriptManager } from '@kit.AbilityKit';
```

## code

```TypeScript
code: number
```

Result code. The value is an integer, and the default value is 0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExecuteResult-code: number--><!--Device-ExecuteResult-code: number-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## flags

```TypeScript
flags?: number
```

Read/write permission of the URIs, which is the same as the flags field of [Want](arkts-ability-app-ability-want-want-c.md). The value can be any of the following:  
- [wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION](arkts-ability-wantconstant-flags-e.md#flag_auth_read_uri_permission):  
read permission.  
- [wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION](arkts-ability-wantconstant-flags-e.md#flag_auth_write_uri_permission):  
write permission.  
- A combination of the two flags above: grants both read and write permissions.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExecuteResult-flags?: number--><!--Device-ExecuteResult-flags?: number-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## result

```TypeScript
result?: Record<string, Object>
```

Script execution result.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExecuteResult-result?: Record<string, Object>--><!--Device-ExecuteResult-result?: Record<string, Object>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## uris

```TypeScript
uris?: Array<string>
```

List of URIs to be authorized to the caller.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExecuteResult-uris?: Array<string>--><!--Device-ExecuteResult-uris?: Array<string>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
