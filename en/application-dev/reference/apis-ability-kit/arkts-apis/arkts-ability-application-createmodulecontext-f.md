# createModuleContext

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## createModuleContext

```TypeScript
export function createModuleContext(context: Context, moduleName: string): Promise<Context>
```

Creates the context for a module. The [resourceManager.Configuration](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-configuration-c.md) in the created module context inherits from the input context, making it convenient for you to access [application resources across HAP/HSP packages](../../../quick-start/resource-categories-and-access.md#cross-haphsp-resources). This API uses a promise to return the result.

> **NOTE:** 
> 
> Creating a module context involves resource querying and initialization, which can be time-consuming. In
> scenarios where application fluidity is critical, avoid frequently or repeatedly calling the
> **createModuleContext** API to create multiple context instances, as this may negatively impact user experience.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Application context. |
| moduleName | string | Yes | Module name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Context](arkts-ability-context-c.md)&gt; | Promise used to return the context created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, application, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let moduleContext: common.Context;
    try {
      application.createModuleContext(this.context, 'entry').then((data: common.Context) => {
        moduleContext = data;
        console.info('createModuleContext success!');
      }).catch((error: BusinessError) => {
        let code: number = (error as BusinessError).code;
        let message: string = (error as BusinessError).message;
        console.error(`createModuleContext failed, error.code: ${code}, error.message: ${message}`);
      });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`createModuleContext failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}
```

```TypeScript
import { UIAbility, application, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    let moduleContext: common.Context;
    try {
      application.createModuleContext(this.context, 'bundlename', 'entry').then((data: common.Context)=>{
        moduleContext = data;
        console.info('createModuleContext success!');
      }).catch((error : BusinessError)=>{
        console.error(`createModuleContext failed, error.code: ${error.code}, error.message: ${error.message}`);
      })
    } catch (error) {
      console.error(`createModuleContext failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
    }
  }
}
```
