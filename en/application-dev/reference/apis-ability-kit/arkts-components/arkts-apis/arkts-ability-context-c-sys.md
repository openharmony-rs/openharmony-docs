# Context

```TypeScript
declare class Context extends BaseContext
```

Context is the context base class of the stage model. It is used to access application-specific resources and perform callbacks for application-level operations. ../../../

**Inheritance/Implementation:** Context extends [BaseContext](arkts-ability-basecontext-c.md)

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## createBundleContext

```TypeScript
createBundleContext(bundleName: string): Context
```

Creates the context based on the bundle name.

> **NOTE:** 
> 
> If there are multiple modules in the stage model, resource ID conflicts may occur. You are advised to use
> [application.createModuleContext](arkts-ability-application-createmodulecontext-f-sys.md#createmodulecontext-1)
> instead.
> 
> This API has been supported since API version 9 and deprecated since API version 12. You are advised to use
> [application.createBundleContext](arkts-ability-application-createbundlecontext-f-sys.md)
> instead.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [createBundleContext](arkts-ability-application-createbundlecontext-f-sys.md)

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| [Context](arkts-ability-context-c.md) | Context created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { common, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let bundleContext: common.Context;
    try {
      bundleContext = this.context.createBundleContext('com.example.test');
    } catch (error) {
      console.error(`createBundleContext failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
    }
  }
}
```

<a id="createmodulecontext-1"></a>

## createModuleContext

```TypeScript
createModuleContext(bundleName: string, moduleName: string): Context
```

Creates the context based on the bundle name and module name.

> **NOTE:** 
> 
> This API has been supported since API version 9 and deprecated since API version 12. You are advised to use
> [application.createModuleContext](arkts-ability-application-createmodulecontext-f-sys.md#createmodulecontext-1)
> instead.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [createModuleContext](arkts-ability-application-createmodulecontext-f.md)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| moduleName | string | Yes | Module name. |

**Return value:**

| Type | Description |
| --- | --- |
| [Context](arkts-ability-context-c.md) | Context created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { common, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let moduleContext: common.Context;
    try {
      moduleContext = this.context.createModuleContext('com.example.test', 'entry');
    } catch (error) {
      console.error(`createModuleContext failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
    }
  }
}
```

## createModuleResourceManager

```TypeScript
createModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager
```

Creates a resource management object for a module.

**Since:** 11

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| moduleName | string | Yes | Module name. |

**Return value:**

| Type | Description |
| --- | --- |
| [resmgr.ResourceManager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md) | Object for resource management. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let ModuleResourceManager: resourceManager.ResourceManager;
    try {
      ModuleResourceManager = this.context.createModuleResourceManager('com.example.test', 'entry');
    } catch (error) {
      console.error(`createModuleResourceManager failed, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
    }
  }
}
```

## createSystemHspModuleResourceManager

```TypeScript
createSystemHspModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager
```

Creates a [resource manager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-getresourcemanager-f.md) for an OEM-preset [system-level HSP](../../../quick-start/application-package-glossary.md#system-level-hsp).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| moduleName | string | Yes | Module name. |

**Return value:**

| Type | Description |
| --- | --- |
| [resmgr.ResourceManager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md) | Returns the system HSP module resource manager. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16400001](../errorcode-ability.md#16400001-target-application-type-is-not-a-system-hsp) | The input bundleName is not a system HSP. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    this.context.createSystemHspModuleResourceManager("com.example.myapplication", "library");
  }
}
```
