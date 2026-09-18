# openInputMethodSettings

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## openInputMethodSettings

```TypeScript
function openInputMethodSettings(context: Context): void
```

Open the input method settings page.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. Only UIAbilityContext and UIExtensionContext are supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16900010](../errorcode-settings.md#16900010-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Go to the input method settings page.
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
settings.openInputMethodSettings(context);
```
