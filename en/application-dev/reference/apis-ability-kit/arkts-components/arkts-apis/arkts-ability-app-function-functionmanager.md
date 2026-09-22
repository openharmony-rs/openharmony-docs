# @ohos.app.function.functionManager

A Function is a business logic unit defined in an application package. It can receive structured data provided by a large model to complete application-defined functions, such as querying real-time weather information or opening a specified application page.

This module provides the capability to manage and invoke Functions, including querying available Function information and invoking a specified Function to execute business logic.

@namespace functionManager

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [invokeFunction](arkts-ability-functionmanager-invokefunction-f-sys.md) | Invoke a function by functionNamespace and functionName. |
| [queryFunctions](arkts-ability-functionmanager-queryfunctions-f-sys.md) | Query all available functions. |
| [registerFunctionHook](arkts-ability-functionmanager-registerfunctionhook-f-sys.md) | Register a function hook for intercepting function invocation. Only one function hook can be registered at a time; registering again while one is already active will fail. This API is only available in developer mode. To update a registered hook, call unregisterFunctionHook first, then register again. The hook object must implement at least one of the optional methods in FunctionHook. |
| [unregisterFunctionHook](arkts-ability-functionmanager-unregisterfunctionhook-f-sys.md) | Unregister the previously registered function hook. The hook object must be the same as the one passed to registerFunctionHook. If no hook is registered, the call will fail with an error. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [InvokeOptions](arkts-ability-functionmanager-invokeoptions-i-sys.md) | Optional parameters for Function invocation. Contains the application context information for the Function invocation. |
| [InvokeResult](arkts-ability-functionmanager-invokeresult-i-sys.md) | Encapsulates the success or failure status of function invocation. |
<!--DelEnd-->
