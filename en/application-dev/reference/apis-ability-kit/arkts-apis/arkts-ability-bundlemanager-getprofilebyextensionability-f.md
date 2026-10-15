# getProfileByExtensionAbility

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

<a id="getprofilebyextensionability1"></a>

## getProfileByExtensionAbility

```TypeScript
function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName: string, callback: AsyncCallback<Array<string>>): void
```

Obtains the JSON string array of the current application's configuration file based on the given module name, ExtensionAbility name, and metadata name (name configured in [metadata](../../../quick-start/module-configuration-file.md#metadata) of the **module.json5** file). This API uses an asynchronous callback to return the result.

> If the profile uses the resource reference format, the return value retains this format (for example,
> **$string:res_id**). You can obtain the referenced resources through related APIs of the
> [resource manager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-bundleManager-function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName: string, callback: AsyncCallback<Array<string>>): void--><!--Device-bundleManager-function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName: string, callback: AsyncCallback<Array<string>>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name. |
| extensionAbilityName | string | Yes | Name of the ExtensionAbility component. |
| metadataName | string | Yes | Metadata name of the ExtensionAbility component, that is, **name** of the **metadata** tag under [extensionAbilities](../../../quick-start/module-configuration-file.md#extensionabilities) in the **module.json5** file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md). Callback invoked to return the result. If the operation is successful, err is undefined and data is the obtained Array<string>; otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified moduleName is not existed. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified extensionAbilityName not existed. |
| [17700024](../errorcode-bundle.md#17700024-profile-does-not-exist) | Failed to get the profile because there is no profile in the HAP. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let extensionAbilityName = 'com.example.myapplication.extension';
let metadataName = 'ability_metadata';

try {
  bundleManager.getProfileByExtensionAbility(moduleName, extensionAbilityName, metadataName, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbility successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed: %{public}s', message);
}
```


<a id="getprofilebyextensionability2"></a>

## getProfileByExtensionAbility

```TypeScript
function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName?: string): Promise<Array<string>>
```

Obtains the JSON string array of the current application's configuration file based on the given module name, ExtensionAbility name, and metadata name (name configured in [metadata](../../../quick-start/module-configuration-file.md#metadata) of the **module.json5** file). This API uses a promise to return the result.

> If the profile uses the resource reference format, the return value retains this format (for example,
> **$string:res_id**). You can obtain the referenced resources through related APIs of the
> [resource manager](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-bundleManager-function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName?: string): Promise<Array<string>>--><!--Device-bundleManager-function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName?: string): Promise<Array<string>>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name. |
| extensionAbilityName | string | Yes | Name of the ExtensionAbility component. |
| metadataName | string | No | Metadata name of the ExtensionAbility component, that is, **name** of the **metadata** tag under [extensionAbilities](../../../quick-start/module-configuration-file.md#extensionabilities) in the **module.json5** file. The default value is null. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the array of JSON strings obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified moduleName is not existed. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified extensionAbilityName not existed. |
| [17700024](../errorcode-bundle.md#17700024-profile-does-not-exist) | Failed to get the profile because there is no profile in the HAP. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let extensionAbilityName = 'com.example.myapplication.extension';
let metadataName = 'ability_metadata';

try {
  bundleManager.getProfileByExtensionAbility(moduleName, extensionAbilityName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbility successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed. Cause: %{public}s', message);
}

try {
  bundleManager.getProfileByExtensionAbility(moduleName, extensionAbilityName, metadataName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbility successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed. Cause: %{public}s', message);
}
```
