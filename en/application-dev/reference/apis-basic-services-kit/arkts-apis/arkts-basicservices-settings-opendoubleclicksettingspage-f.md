# openDoubleClickSettingsPage

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## openDoubleClickSettingsPage

```TypeScript
function openDoubleClickSettingsPage(context: Context): void
```

1. Opens the settings page for double-pressing the Down key.
2. This API is used to set the default application started by double-pressing the Down key.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | 1. Application context. 2. Specify this parameter to set the application started by double-pressing the Down key. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16900010](../errorcode-settings.md#16900010-parameter-check-failed) | 1. The parameter is incorrect. 2. The parameter is not transferred or the transferred parameter is invalid. |
| [16900020](../errorcode-settings.md#16900020-failed-to-open-the-settings-page) | 1. The setting page cannot be opened through redirection. 2. Internal error |

**Examples**

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  settings.openDoubleClickSettingsPage(context);
} catch (err) {
  console.error(`Failed to open the DoubleClick settings page. code: ${err?.code}, message: ${err?.message}`);
}
```
