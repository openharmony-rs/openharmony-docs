# invokePublicFunction

## Modules to Import

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## invokePublicFunction

```TypeScript
function invokePublicFunction(functionNamespace: string, functionName: string,
    args: Record<string, Object>, options?: InvokeOptions): Promise<InvokeResult>
```

Invoke a public function by functionNamespace and functionName. Third-party applications can invoke public functions through this API after being granted the required permission via ACL.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ACCESS_PUBLIC_FUNCTION

**Model restriction:** This API can be used only in the stage model.

<!--Device-functionManager-function invokePublicFunction(functionNamespace: string, functionName: string,    args: Record<string, Object>, options?: InvokeOptions): Promise<InvokeResult>--><!--Device-functionManager-function invokePublicFunction(functionNamespace: string, functionName: string,    args: Record<string, Object>, options?: InvokeOptions): Promise<InvokeResult>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| functionNamespace | string | Yes | The namespace of the target function. |
| functionName | string | Yes | The name of the target function. |
| args | Record&lt;string, Object&gt; | Yes | The input arguments of the function. |
| options | [InvokeOptions](arkts-ability-functionmanager-invokeoptions-i.md) | No | The invocation options of the function. Default value: see the default values of the specific attributes in [InvokeOptions](arkts-ability-functionmanager-invokeoptions-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[InvokeResult](arkts-ability-functionmanager-invokeresult-i.md)&gt; | The promise used to return the function execution result [InvokeResult](arkts-ability-functionmanager-invokeresult-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Connect to system service failed;         2. System service failed to communicate with dependency module. |
| [35600060](../errorcode-ability.md#35600060-function-does-not-exist) | The function does not exist. |
| [35600061](../errorcode-ability.md#35600061-function-execution-failed) | The function execute failed. |
| [35600062](../errorcode-ability.md#35600062-function-execution-timeout) | The function execute timeout. |
