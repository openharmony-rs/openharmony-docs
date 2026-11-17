# queryPublicFunctions

## Modules to Import

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## queryPublicFunctions

```TypeScript
function queryPublicFunctions(): Promise<Array<FunctionInfo>>
```

Query public functions. Third-party applications can query public functions through this API after being granted the required permission via ACL.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ACCESS_PUBLIC_FUNCTION

**Model restriction:** This API can be used only in the stage model.

<!--Device-functionManager-function queryPublicFunctions(): Promise<Array<FunctionInfo>>--><!--Device-functionManager-function queryPublicFunctions(): Promise<Array<FunctionInfo>>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[FunctionInfo](arkts-ability-functioninfo-i.md)&gt;&gt; | The promise used to return the list of public functions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Connect to system service failed;         2. System service failed to communicate with dependency module. |
