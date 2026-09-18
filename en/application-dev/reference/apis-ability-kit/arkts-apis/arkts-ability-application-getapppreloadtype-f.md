# getAppPreloadType

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## getAppPreloadType

```TypeScript
export function getAppPreloadType(): AppPreloadType
```

Obtains the preloading type of the current application process.

> **NOTE:** 
> 
> - This API can return the actual preloading type only if it is called before the first execution of [AbilityStage.onCreate](arkts-ability-app-ability-abilitystage-abilitystage-c.md#oncreate).
> 
> - Once the AbilityStage creation finishes, the preloaded data of the application is cleared. Any subsequent calls will return **UNSPECIFIED** instead of the original preloading type.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| [AppPreloadType](arkts-ability-application-apppreloadtype-e.md) | Obtains the preloading type of the current application process. |

**Examples**

```TypeScript
import { AbilityStage, application } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage{
  onCreate() {
    let appPreloadType = application.getAppPreloadType();
  }
}
```
