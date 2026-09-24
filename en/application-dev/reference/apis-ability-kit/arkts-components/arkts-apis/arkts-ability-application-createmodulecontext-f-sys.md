# createModuleContext (System API)

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

<a id="createmodulecontext-1"></a>

## createModuleContext

```TypeScript
export function createModuleContext(context: Context, bundleName: string, moduleName: string): Promise<Context>
```

Creates the context for a module. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Starting from API version 18, the context can obtain the [process name](../../../reference/apis-ability-kit/js-apis-inner-application-context.md#context) of the current application. The **processName** property in the context created by **createModuleContext** is the same as the
> **processName** property in the input parameter **Context**. The values of other properties are obtained based on
> the input parameters **Context**, **bundleName**, and **moduleName**.
> 
> - Creating a module context involves resource querying and initialization, which can be time-consuming. In scenarios where application fluidity is critical, avoid frequently or repeatedly calling the
> **createModuleContext** API to create multiple context instances, as this may negatively impact user experience.

**Since:** 12

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | Yes | Application context. |
| bundleName | string | Yes | Bundle name of the application. If an empty string is passed in, the current application is used by default. |
| moduleName | string | Yes | Module name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Context](arkts-ability-context-c.md)&gt; | Promise used to return the context created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

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
