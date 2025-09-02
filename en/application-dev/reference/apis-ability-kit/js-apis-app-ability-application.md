#  @ohos.app.ability.application (Application Utility Class)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2-->
<!--Designer: @li-weifeng2-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

You can use this module to manage and obtain the application [context](../../application-models/application-context-stage.md) and control the application process state.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { application } from '@kit.AbilityKit';
```

## application.createModuleContext<sup>12+</sup>

createModuleContext(context: Context, moduleName: string): Promise\<Context>

Creates the context for a module. The [resourceManager.Configuration](../apis-localization-kit/js-apis-resource-manager.md#configuration) in the created module context inherits from the input context, making it convenient for you to access [application resources across HAP/HSP packages](../../quick-start/resource-categories-and-access.md#cross-haphsp-resources).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| context | [Context](js-apis-inner-application-context.md) | Yes| Application context.|
| moduleName | string | Yes| Module name.|

**Return value**

| Type              | Description               |
| ------------------ | ------------------- |
| Promise\<[Context](../../reference/apis-ability-kit/js-apis-inner-application-context.md)> | Promise used to return the context created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message       |
| -------- | --------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { AbilityConstant, UIAbility, application, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let moduleContext: common.Context;
    try {
      application.createModuleContext(this.context, 'entry').then((data: Context) => {
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

## application.getApplicationContext<sup>14+</sup>

getApplicationContext(): ApplicationContext

Obtains the application context. This API provides context access independent of the base class **Context**.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type                                                        | Description               |
| ------------------------------------------------------------ | ------------------- |
| [ApplicationContext](js-apis-inner-application-applicationContext.md) | Application context.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message       |
| -------- | --------------- |
| 16000050 | Internal error. |

**Example**

```ts
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let applicationContext = application.getApplicationContext();
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`getApplicationContext failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}
```

## application.createPluginModuleContext<sup>19+</sup>

createPluginModuleContext(context: Context, pluginBundleName: string, pluginModuleName: string): Promise\<Context>

Creates the context of a plugin under the current application based on the context, plugin bundle name, and plugin module name, so as to obtain the basic information about the plugin. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| context | [Context](js-apis-inner-application-context.md) | Yes| Application context.|
| pluginBundleName | string | Yes| Bundle name of the plugin.|
| pluginModuleName | string | Yes| Module name of the plugin.|

**Return value**

| Type              | Description               |
| ------------------ | ------------------- |
| Promise\<[Context](../../reference/apis-ability-kit/js-apis-inner-application-context.md)> | Promise used to return the context created.|

**Example**

```ts
import { AbilityConstant, UIAbility, application, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let moduleContext: common.Context;
    try {
      application.createPluginModuleContext(this.context, 'com.example.pluginBundleName', 'pluginModuleName')
        .then((data: Context) => {
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

## application.promoteCurrentToCandidateMasterProcess<sup>20+</sup>

promoteCurrentToCandidateMasterProcess(insertToHead: boolean): Promise\<void>

Adds the current process into the [candidate master process](../../application-models/ability-terminology.md#candidate-master-process) list. This API uses a promise to return the result.

When the [master process](../../application-models/ability-terminology.md#master-process) is destroyed and a UIAbility or UIExtensionAbility with **isolationProcess** set to **true** is restarted, the system takes corresponding actions based on whether there is a candidate master process.

- If a candidate master process exists, the system sets the process at the head of the candidate master process list as the new master process and triggers the [onNewProcessRequest](js-apis-app-ability-abilityStage.md#onnewprocessrequest11) callback.
- If no candidate master process exists, the system performs the following operations based on the component type:
	- For a UIAbility, the system creates an empty process as the master process.
	- For a UIExtensionAbility, the system first tries to reuse an existing UIExtensionAbility process as the new master process. If no available process exists, it creates an empty process as the master process.

> **NOTE**
> - Currently, only 2-in-1 devices and tablets are supported.
<!--Del-->
>
> - The **isolationProcess** field can be set to **true** in the [module.json5](../../quick-start/module-configuration-file.md) file, but only for the UIExtensionAbility of the sys/commonUI type.
<!--DelEnd-->

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| insertToHead | boolean | Yes| Whether to add the current process to the head of the candidate master process list. **true** to add the current process to the head of the list, **false** to add the current process to the tail of the list.|

**Return value**

| Type              | Description               |
| ------------------ | ------------------- |
|Promise\<void> | Promise that returns no result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](./errorcode-ability.md).

| ID| Error Message       |
| -------- | --------------- |
| 801 | Capability not supported.|
| 16000115 | The current process is not running a component configured with "isolationProcess" and cannot be set as a candidate master process. |


**Example**

```ts
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      application.promoteCurrentToCandidateMasterProcess(true)
        .then(() => {
          console.info('promote succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`promote failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`promoteCurrentToCandidateMasterProcess failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}
```

## application.demoteCurrentFromCandidateMasterProcess<sup>20+</sup>

demoteCurrentFromCandidateMasterProcess(): Promise\<void>

Removes the current process from the candidate master process list. This API uses a promise to return the result.

> **NOTE**
>
> Currently, only 2-in-1 devices and tablets are supported.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type              | Description               |
| ------------------ | ------------------- |
|Promise\<void> | Promise that returns no result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message       |
| -------- | --------------- |
| 801 | Capability not supported.|
| 16000116 | The current process is already a master process and does not support cancellation. |
| 16000117 | The current process is not a candidate master process and does not support cancellation. |

**Example**

```ts
import { AbilityConstant, UIAbility, application, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      application.demoteCurrentFromCandidateMasterProcess()
        .then(() => {
          console.info('demote succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`demote failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`demoteCurrentFromCandidateMasterProcess failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}
```
