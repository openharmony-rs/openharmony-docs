# createPluginModuleContext

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## createPluginModuleContext

```TypeScript
export function createPluginModuleContext(context: Context, pluginBundleName: string, pluginModuleName: string): Promise<Context>
```

Creates the context of a plugin under the current application based on the context, plugin bundle name, and plugin module name, so as to obtain the basic information about the plugin. This API uses a promise to return the result.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Application context. |
| pluginBundleName | string | Yes | Bundle name of the plugin. |
| pluginModuleName | string | Yes | Module name of the plugin. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Context](arkts-ability-context-c.md)&gt; | Promise used to return the context created. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, application, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let moduleContext: common.Context;
    try {
      application.createPluginModuleContext(this.context, 'com.example.pluginBundleName', 'pluginModuleName')
        .then((data: common.Context) => {
          moduleContext = data;
          console.info('createPluginModuleContext success!');
        })
        .catch((error: BusinessError) => {
          let code: number = (error as BusinessError).code;
          let message: string = (error as BusinessError).message;
          console.error(`createPluginModuleContext failed, error.code: ${code}, error.message: ${message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`createPluginModuleContext failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}
```
