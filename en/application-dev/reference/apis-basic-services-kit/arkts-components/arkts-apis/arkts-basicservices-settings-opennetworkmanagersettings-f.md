# openNetworkManagerSettings

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## openNetworkManagerSettings

```TypeScript
function openNetworkManagerSettings(context: Context): Promise<boolean>
```

Open the network manager settings page.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. Only UIAbilityContext and UIExtensionContext are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800000](../errorcode-settings.md#14800000-parameter-check-failed) | Parameter error. |
| [14800010](../errorcode-settings.md#14800010-uiability-required) | Original service error. |

**Examples**

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Redirect to the network manager settings page.
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
settings.openNetworkManagerSettings(context).then((status) => {
  console.info(`callback:return whether settings is open.`);
});
```
