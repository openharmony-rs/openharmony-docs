# unregisterFunctionHook (System API)

## Modules to Import

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## unregisterFunctionHook

```TypeScript
function unregisterFunctionHook(hook: FunctionHook): Promise<void>
```

Unregister the previously registered function hook. The hook object must be the same as the one passed to registerFunctionHook. If no hook is registered, the call will fail with an error.

**Since:** 26.0.1

**Required permissions:** ohos.permission.REGISTER_AGENT_HOOK

**Model restriction:** This API can be used only in the stage model.

<!--Device-functionManager-function unregisterFunctionHook(hook: FunctionHook): Promise<void>--><!--Device-functionManager-function unregisterFunctionHook(hook: FunctionHook): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hook | [FunctionHook](arkts-ability-functionhook-i-sys.md) | Yes | The hook object to unregister. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| 35600036 | No hook is registered; nothing to unregister. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
