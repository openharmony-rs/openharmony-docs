# createPluginModuleContextForHostBundle (System API)

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## createPluginModuleContextForHostBundle

```TypeScript
export function createPluginModuleContextForHostBundle(context: Context, pluginBundleName: string, pluginModuleName: string,
    hostBundleName: string): Promise<Context>
```

Creates the context for a plugin based on a given context, plugin bundle name, plugin module name, and application bundle name to obtain the basic information about the plugin. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Application context. |
| pluginBundleName | string | Yes | Bundle name of the plugin. |
| pluginModuleName | string | Yes | Module name of the plugin. |
| hostBundleName | string | Yes | Bundle name of the application for which the plugin is installed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Context](arkts-ability-context-c.md)&gt; | Promise used to return the context created, in which the **processName** and **config** properties are the same as those of the input context. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, application, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let moduleContext: common.Context;
    try {
      application.createPluginModuleContextForHostBundle(this.context, 'com.example.pluginBundleName', 'pluginModuleName', 'com.example.hostBundleName')
        .then((data: common.Context) => {
          moduleContext = data;
          console.info('createPluginModuleContextForHostBundle success!');
        })
        .catch((error: BusinessError) => {
          console.error(`createPluginModuleContextForHostBundle failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (error: BusinessError) {
      console.error(`createPluginModuleContextForHostBundle failed, error.code: ${error.code}, error.message: ${error.message}`);
    }
  }
}
```
