# openBiometricsSettingsPage

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## openBiometricsSettingsPage

```TypeScript
function openBiometricsSettingsPage(context: Context): void
```

Open the biometrics and password settings page.

**Since:** 24

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
| [16900020](../errorcode-settings.md#16900020-failed-to-open-the-settings-page) | Failed to open the settings page via redirection. |

**Examples**

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  settings.openBiometricsSettingsPage(context);
} catch (err) {
  console.error(`Failed to open the biometrics and password settings page. code: ${err?.code}, message: ${err?.message}`);
}
```
