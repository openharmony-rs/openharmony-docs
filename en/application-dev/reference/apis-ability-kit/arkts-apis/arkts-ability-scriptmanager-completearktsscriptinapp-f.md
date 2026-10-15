# completeArkTSScriptInApp

## Modules to Import

```TypeScript
import { scriptManager } from '@kit.AbilityKit';
```

## completeArkTSScriptInApp

```TypeScript
function completeArkTSScriptInApp(context: Context, requestCode: string, result: ExecuteResult): Promise<void>
```

Completes the ArkTS script execution of an app and reports the execution result. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-scriptManager-function completeArkTSScriptInApp(context: Context, requestCode: string, result: ExecuteResult): Promise<void>--><!--Device-scriptManager-function completeArkTSScriptInApp(context: Context, requestCode: string, result: ExecuteResult): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Ability context, used for temporary file authorization. |
| requestCode | string | Yes | Request code used to identify the current operation. |
| result | [ExecuteResult](arkts-ability-scriptmanager-executeresult-i.md) | Yes | Execution result of the ArkTS script. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000020](../errorcode-ability.md#16000020-context-is-not-an-ability-level-context) | The context is not ability context. |
| [16000003](../errorcode-ability.md#16000003-id-does-not-exist) | The specified ID does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |
