# createModuleContextSync

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## createModuleContextSync

```TypeScript
export function createModuleContextSync(context: Context, moduleName: string): Context
```

Creates the context for a module. The [resourceManager.Configuration](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-configuration-c.md) in the created module context inherits from the input context, making it convenient for you to access [application resources across HAP/HSP packages](../../../quick-start/resource-categories-and-access.md#cross-haphsp-resources)

> **NOTE:** 
> 
> Creating a module context involves resource querying and initialization, which can be time-consuming. In
> scenarios where application fluidity is critical, avoid frequently or repeatedly calling the
> **createModuleContext** API to create multiple context instances, as this may negatively impact user experience.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Application context. |
| moduleName | string | Yes | Module name. |

**Return value:**

| Type | Description |
| --- | --- |
| [Context](arkts-ability-context-c.md) | Return the context created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000021](../errorcode-ability.md#16000021-module-name-does-not-exist) | The module does not exist. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let moduleContext = application.createModuleContextSync(this.context, 'entry');
  }
}
```
