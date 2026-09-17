# setWantAgentMultithreading (System API)

## Modules to Import

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## setWantAgentMultithreading

```TypeScript
function setWantAgentMultithreading(isMultithreadingSupported: boolean) : void
```

Enables or disables the WantAgent multithreading feature.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isMultithreadingSupported | boolean | Yes | Whether to enable the multithreading feature. The value &lt;code&gt;true&lt;/code&gt; means to enable multithreading, and &lt;code&gt;false&lt;/code&gt; means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
