# queryFunctions (System API)

## Modules to Import

```TypeScript
import { functionManager } from '@kit.AbilityKit';
```

## queryFunctions

```TypeScript
function queryFunctions(): Promise<Array<FunctionInfo>>
```

Query all available functions.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_FUNCTION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[FunctionInfo](arkts-ability-functioninfo-i-sys.md)&gt;&gt; | The promise used to return available functions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
